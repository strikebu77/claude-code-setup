Conduct a comprehensive security review of this codebase following the OWASP Code Review Guide v2.0 methodology.

### IMPORTANT REQUIREMENTS:

- **DO NOT WRITE CODE** - perform security review only
- Save results to file `.claude/reviews/security.md`
- If file `.claude/reviews/security.md` already exists:
  1. First analyze existing results
  2. Note which issues have been fixed
  3. Conduct a new full review
  4. Compare results and indicate changes

### 1. CONTEXTUAL REVIEW

- Determine application type (web, mobile, API, desktop)
- Identify programming languages and frameworks used
- Identify entry points and attack surface
- Determine critical assets and data requiring protection

### 2. OWASP TOP 10 VULNERABILITIES CHECK

Systematically check for the following vulnerability classes:

**A1 - Injection**

- SQL, NoSQL, OS command, LDAP injections
- Check query parameterization
- Input data validation

**A2 - Broken Authentication**

- Authentication mechanisms
- Session management
- Password storage (hashing, salt)

**A3 - Cross-Site Scripting (XSS)**

- Reflected, Stored and DOM-based XSS
- Output data encoding
- Content Security Policy

**A4 - Insecure Direct Object References**

- Authorization checks when accessing objects
- Request parameter validation

**A5 - Security Misconfiguration**

- Configuration files
- Framework security settings
- Access rights and privileges

**A6 - Sensitive Data Exposure**

- Data encryption at rest and in transit
- Use of outdated cryptographic algorithms
- Key management

**A7 - Missing Function Level Access Control**

- Function-level authorization checks
- RBAC/ACL implementation

**A8 - Cross-Site Request Forgery (CSRF)**

- CSRF tokens
- Referer/Origin header validation

**A9 - Using Components with Known Vulnerabilities**

- Library versions used
- Known CVEs

**A10 - Unvalidated Redirects and Forwards**

- URL validation for redirects
- Whitelists of allowed domains

### 3. TECHNOLOGY-SPECIFIC CHECKS

**For each language/framework check:**

- Unsafe functions and methods
- Proper use of built-in security mechanisms
- Compliance with technology-specific best practices

### 4. ARCHITECTURAL REVIEW

- Application layer separation
- Principle of least privilege
- Defense in depth
- Fail securely principles

### 5. BUSINESS LOGIC REVIEW

- Business rule bypass
- Race conditions
- Logic errors in critical operations

### 6. PROTECTION MECHANISMS CHECK

- Logging and monitoring
- Error handling (without information leakage)
- DoS attack protection
- Attack detection mechanisms

### REPORT FORMAT:

#### File header:

```markdown
# Codebase Security Review

**Review Date**: [current date]
**Review Version**: [version number if repeat review]
**Status**: [Initial Review / Repeat Review]
```

#### For each vulnerability found:

1. **Severity**: Critical/High/Medium/Low (using DREAD or CVSS)
2. **Description**: Brief problem description
3. **Location**: File, line of code, function
4. **Proof of Concept**: Exploitation example
5. **Recommendations**: Specific remediation steps
6. **References**: Links to OWASP, CWE, CVE
7. **Status**: [New / Fixed / In Progress / Not Fixed]

### ACTION PLAN (TODO LIST):

After review, create a tasks section in the following format:

```markdown
## Vulnerability Remediation Plan

### Critical - immediate fix required

- [ ] [CRIT-001] Fix SQL injection in file `auth.php:45`
- [ ] [CRIT-002] Implement parameterized queries in module `database.js`

### High - fix within 1 week

- [ ] [HIGH-001] Add CSRF tokens to all forms
- [ ] [HIGH-002] Update jQuery library to version 3.6.0+

### Medium - fix within 1 month

- [ ] [MED-001] Improve input validation in API endpoints
- [ ] [MED-002] Configure Content Security Policy

### Low - plan for next release

- [ ] [LOW-001] Add rate limiting for API
- [ ] [LOW-002] Improve security logging

### Additional Security Measures

- [ ] Conduct team training on secure development
- [ ] Implement SAST in CI/CD pipeline
- [ ] Configure regular dependency scanning
```

### PRIORITIZATION:

Rank found vulnerabilities by:

- Business criticality
- Ease of exploitation
- Potential damage

### COMPARISON WITH PREVIOUS REVIEW (if applicable):

```markdown
## Comparison with Previous Review

### Fixed Vulnerabilities:

- ✅ [Description of fixed vulnerability]

### New Vulnerabilities:

- 🆕 [Description of new vulnerability]

### Unresolved Issues:

- ⚠️ [Description of issue that remains]

### Overall Progress:

- Fixed: X of Y
- New issues: Z
- Overall security level: [Improved/Degraded/No Change]
```

Begin review with the most critical system components (authentication, authorization, payment processing, personal data handling).
