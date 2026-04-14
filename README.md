# 🛡️ OWASP Web Application Security Testing Checklist

> A comprehensive penetration testing checklist based on OWASP methodology.  
> Use this as a reference during web application security assessments.

---

## Table of Contents

- [1. Information Gathering](#1-information-gathering)
- [2. Configuration & Deployment Management Testing](#2-configuration--deployment-management-testing)
- [3. Identity Management Testing](#3-identity-management-testing)
- [4. Authentication Testing](#4-authentication-testing)
- [5. Authorization Testing](#5-authorization-testing)
- [6. Session Management Testing](#6-session-management-testing)
- [7. Input Validation Testing](#7-input-validation-testing)
- [8. Error Handling Testing](#8-error-handling-testing)
- [9. Weak Cryptography Testing](#9-weak-cryptography-testing)
- [10. Business Logic Testing](#10-business-logic-testing)
- [11. Client Side Testing](#11-client-side-testing)
- [12. Other Common Issues](#12-other-common-issues)
- [13. API Security Testing](#13-api-security-testing)
- [14. Modern Web Vulnerabilities](#14-modern-web-vulnerabilities)
- [15. Security Headers & CSP](#15-security-headers--csp)
- [16. OAuth 2.0 & SSO Testing](#16-oauth-20--sso-testing)
- [17. Supply Chain & Dependency Testing](#17-supply-chain--dependency-testing)
- [18. Email Security Testing](#18-email-security-testing)

---

## 1. Information Gathering

### 🔍 Open Source Reconnaissance
- [ ] Perform Google Dorks search
- [ ] Perform OSINT

### 🖥️ Fingerprinting Web Server
- [ ] Find the type of Web Server
- [ ] Find the version details of the Web Server

### 📄 Looking For Metafiles
- [ ] View the `robots.txt` file
- [ ] View the `sitemap.xml` file
- [ ] View the `humans.txt` file
- [ ] View the `security.txt` file

### 🌐 Enumerating Web Server's Applications
- [ ] Enumerate with Nmap
- [ ] Enumerate with Netcat
- [ ] Perform a DNS lookup
- [ ] Perform a Reverse DNS lookup

### 📝 Review The Web Contents
- [ ] Inspect the page source for sensitive info
- [ ] Try to find sensitive JavaScript codes
- [ ] Try to find any keys
- [ ] Make sure autocomplete is disabled

### 🚪 Identifying Application's Entry Points
- [ ] Identify what methods are used
- [ ] Identify where the methods are used
- [ ] Identify the injection point

### 🗺️ Mapping Execution Paths
- [ ] Use Burp Suite
- [ ] Use Dirsearch
- [ ] Use Gobuster

### 🧩 Fingerprint Web Application Framework
- [ ] Use the Wappalyzer browser extension
- [ ] Use WhatWeb
- [ ] View URL extensions
- [ ] View HTML source code
- [ ] View the cookie parameter
- [ ] View the HTTP headers

### 🏗️ Map Application Architecture
- [ ] Map the overall site structure

---

## 2. Configuration & Deployment Management Testing

### 🌍 Test Network Configuration
- [ ] Check the network configuration
- [ ] Check for default settings
- [ ] Check for default credentials

### ⚙️ Test Application Configuration
- [ ] Ensure only required modules are used
- [ ] Ensure unwanted modules are disabled
- [ ] Ensure the server can handle DoS attempts
- [ ] Check how the application handles `4xx` & `5xx` errors
- [ ] Check for privilege required to run
- [ ] Check logs for sensitive info

### 📂 Test File Extension Handling
- [ ] Ensure the server won't return sensitive extensions
- [ ] Ensure the server won't accept malicious extensions
- [ ] Test for file upload vulnerabilities

### 🗃️ Review Backup & Unreferenced Files
- [ ] Ensure unreferenced files don't contain sensitive info
- [ ] Ensure proper naming conventions for old/new backup files
- [ ] Check the functionality of unreferenced pages

### 🔧 Enumerate Infrastructure & Admin Interfaces
- [ ] Try to find the Infrastructure Interface
- [ ] Try to find the Admin Interface
- [ ] Identify hidden admin functionalities

### 📡 Testing HTTP Methods
- [ ] Discover the supported methods
- [ ] Ensure `PUT` method is disabled
- [ ] Ensure `OPTIONS` method is disabled
- [ ] Test access control bypass
- [ ] Test for XST attacks
- [ ] Test for HTTP method overriding

### 🔒 Test HSTS
- [ ] Ensure HSTS is enabled

### 🌐 Test RIA Cross Domain Policy
- [ ] Check for Adobe's Cross Domain Policy
- [ ] Ensure it has the least privilege

### 📋 Test File Permission
- [ ] Ensure permissions for sensitive files
- [ ] Test for directory enumeration

### 🌿 Test For Subdomain Takeover
- [ ] Test DNS, A, and CNAME records for subdomain takeover
- [ ] Test NS records for subdomain takeover
- [ ] Test 404 response for subdomain takeover

### ☁️ Test Cloud Storage
- [ ] Check sensitive paths of AWS
- [ ] Check sensitive paths of Google Cloud
- [ ] Check sensitive paths of Azure

---

## 3. Identity Management Testing

### 👥 Test Role Definitions
- [ ] Test for forced browsing
- [ ] Test for IDOR (Insecure Direct Object Reference)
- [ ] Test for parameter tampering
- [ ] Ensure low-privilege users cannot access high-privilege resources

### 📋 Test User Registration Process
- [ ] Ensure the same user/identity can't register repeatedly
- [ ] Ensure registrations are verified
- [ ] Ensure disposable email addresses are rejected
- [ ] Check what proof is required for successful registration

### 🔑 Test Account Provisioning Process
- [ ] Check the verification for the provisioning process
- [ ] Check the verification for the de-provisioning process
- [ ] Check provisioning rights for admin users to other users
- [ ] Check whether a user can de-provision themselves
- [ ] Check for the resources of a de-provisioned user

### 🔎 Testing For Account Enumeration
- [ ] Check response when valid username + valid password entered
- [ ] Check response when valid username + invalid password entered
- [ ] Check response when invalid username + password entered
- [ ] Ensure rate-limiting is enabled on username and password fields

### 👤 Test For Weak Username Policy
- [ ] Check response for both valid and invalid usernames
- [ ] Check for username enumeration

---

## 4. Authentication Testing

### 🔓 Test For Un-Encrypted Channel
- [ ] Check for HTTP login page
- [ ] Check for HTTP register/sign-in page
- [ ] Check for HTTP forgot password page
- [ ] Check for HTTP change password page
- [ ] Check for resources on HTTP after logout
- [ ] Test for forced browsing to HTTP pages

### 🗝️ Test For Default Credentials
- [ ] Test with default credentials
- [ ] Test organization name as credentials
- [ ] Test for response manipulation
- [ ] Test for default username with blank password
- [ ] Review the page source for credentials

### 🔐 Test For Weak Lockout Mechanism
- [ ] Ensure account is locked after 3–5 incorrect attempts
- [ ] Ensure the system only accepts valid CAPTCHA
- [ ] Ensure the system rejects invalid CAPTCHA
- [ ] Ensure CAPTCHA regenerates after reload
- [ ] Ensure CAPTCHA reloads after wrong code entry
- [ ] Ensure users have a recovery option for locked accounts

### 🚫 Test For Bypassing Authentication Schema
- [ ] Test forced browsing directly to internal dashboard without login
- [ ] Test for session ID prediction
- [ ] Test for authentication parameter tampering
- [ ] Test for SQL injection on the login page
- [ ] Test to gain access using session ID
- [ ] Test whether multiple logins are allowed

### 🧠 Test For Vulnerable Remember Password
- [ ] Ensure stored password is encrypted
- [ ] Ensure stored password is on the server-side

### 🗄️ Test For Browser Cache Weakness
- [ ] Ensure proper `cache-control` is set on sensitive pages
- [ ] Ensure no sensitive data is stored in browser cache

### 🔏 Test For Weak Password Policy
- [ ] Ensure the password policy is set to strong
- [ ] Check for password reusability
- [ ] Check that users can't use their username as password
- [ ] Check for usage of common weak passwords
- [ ] Check the minimum password length
- [ ] Check the maximum password length

### ❓ Testing For Weak Security Questions
- [ ] Check for the complexity of the questions
- [ ] Check for brute-forcing vulnerability

### 🔄 Test For Weak Password Reset Function
- [ ] Check what information is required to reset the password
- [ ] Check for password reset function over HTTP
- [ ] Test the randomness of password reset tokens
- [ ] Test the uniqueness of password reset tokens
- [ ] Test for rate limiting on password reset tokens
- [ ] Ensure token expires after being used
- [ ] Ensure token expires after prolonged non-use

### ✏️ Test For Weak Password Change Function
- [ ] Check if old password is required to make a change
- [ ] Check for uniqueness of forgotten password
- [ ] Check for blank password change
- [ ] Check for password change function over HTTP
- [ ] Ensure old password is not displayed after change
- [ ] Ensure other sessions are destroyed after password change

### 📱 Test For Weak Authentication In Alternative Channel
- [ ] Test authentication on desktop browsers
- [ ] Test authentication on mobile browsers
- [ ] Test authentication in a different country
- [ ] Test authentication in a different language
- [ ] Test authentication on desktop applications
- [ ] Test authentication on mobile applications

---

## 5. Authorization Testing

### 📁 Testing Directory Traversal / File Include
- [ ] Identify the injection point on the URL
- [ ] Test for Local File Inclusion (LFI)
- [ ] Test for Remote File Inclusion (RFI)
- [ ] Test traversal on the URL parameter
- [ ] Test traversal on the cookie parameter

### 🔠 Testing Traversal With Encoding
- [ ] Test traversal with Base64 encoding
- [ ] Test traversal with URL encoding
- [ ] Test traversal with ASCII encoding
- [ ] Test traversal with HTML encoding
- [ ] Test traversal with Hex encoding
- [ ] Test traversal with Binary encoding
- [ ] Test traversal with Octal encoding
- [ ] Test traversal with Gzip encoding

### 💻 Testing Traversal With Different OS Schemes
- [ ] Test traversal with Unix schemes
- [ ] Test traversal with Windows schemes
- [ ] Test traversal with Mac schemes

### 🔡 Test Other Encoding Techniques
- [ ] Test traversal with double encoding
- [ ] Test traversal with all characters encoded
- [ ] Test traversal with only special characters encoded

### 🛡️ Test Authorization Schema Bypass
- [ ] Test for horizontal authorization schema bypass
- [ ] Test for vertical authorization schema bypass
- [ ] Test overriding the target with custom headers

### ⬆️ Test For Privilege Escalation
- [ ] Identify the injection point
- [ ] Test for bypassing security measures
- [ ] Test for forced browsing
- [ ] Test for IDOR
- [ ] Test for parameter tampering to high-privilege user

### 🔗 Test For Insecure Direct Object Reference (IDOR)
- [ ] Test changing the ID parameter
- [ ] Test adding parameters at the endpoints
- [ ] Test for HTTP parameter pollution
- [ ] Test by adding an extension at the end
- [ ] Test with outdated API versions
- [ ] Test by wrapping the ID with an array
- [ ] Test by wrapping the ID with a JSON object
- [ ] Test for JSON parameter pollution
- [ ] Test by changing the case
- [ ] Test for path traversal
- [ ] Test by changing words
- [ ] Test by changing methods

---

## 6. Session Management Testing

### 🍪 Test For Session Management Schema
- [ ] Ensure all `Set-Cookie` directives are secure
- [ ] Ensure no cookie operation takes place over an unencrypted channel
- [ ] Ensure the cookie can't be forced over an unencrypted channel
- [ ] Ensure the `HTTPOnly` flag is enabled
- [ ] Check if any cookies are persistent
- [ ] Check for session cookies and cookie expiration date/time
- [ ] Check for session fixation
- [ ] Check for concurrent login
- [ ] Check for session after logout
- [ ] Check for session after closing the browser
- [ ] Try decoding cookies (Base64, Hex, URL, etc.)

### 🏷️ Test For Cookie Attributes
- [ ] Ensure the cookie is set with the `Secure` attribute
- [ ] Ensure the cookie is set with the `Path` attribute
- [ ] Ensure the cookie has the `HTTPOnly` flag

### 📌 Test For Session Fixation
- [ ] Ensure new cookies are issued upon successful authentication
- [ ] Test manipulating the cookies

### 👁️ Test For Exposed Session Variables
- [ ] Test for encryption
- [ ] Test for GET and POST vulnerabilities
- [ ] Test if GET request incorporates the session ID
- [ ] Test by interchanging POST with GET method

### 🔙 Test For Back Refresh Attack
- [ ] Test after password change
- [ ] Test after logout

### 🔀 Test For Cross Site Request Forgery (CSRF)
- [ ] Check if the token is validated on the server-side
- [ ] Check if the token is validated for full or partial length
- [ ] Compare CSRF tokens for multiple dummy accounts
- [ ] Check CSRF by interchanging POST with GET method
- [ ] Check CSRF by removing the CSRF token parameter
- [ ] Check CSRF by removing the CSRF token and using a blank parameter
- [ ] Check CSRF by using unused tokens
- [ ] Check CSRF by replacing the CSRF token with its own values
- [ ] Check CSRF by changing content type to `form-multipart`
- [ ] Check CSRF by changing or deleting characters of the CSRF token
- [ ] Check CSRF by changing the referrer to `Referrer`
- [ ] Check CSRF by changing the host values
- [ ] Check CSRF alongside clickjacking

### 🚪 Test For Logout Functionality
- [ ] Check the logout function on different pages
- [ ] Check for the visibility of the logout button
- [ ] Ensure session is ended after logout
- [ ] Ensure dashboard is inaccessible via back button after logout
- [ ] Ensure proper session timeout has been set

### ⏱️ Test For Session Timeout
- [ ] Ensure a session timeout exists
- [ ] Ensure all tokens are destroyed after timeout

### 🧩 Test For Session Puzzling
- [ ] Identify all session variables
- [ ] Try to break the logical flow of session generation

### 🕵️ Test For Session Hijacking
- [ ] Test session hijacking on targets without HSTS enabled
- [ ] Test by logging in with captured cookies

---

## 7. Input Validation Testing

### ⚡ Test For Reflected XSS
- [ ] Ensure `< > ' ' & " "` characters are filtered
- [ ] Test with a character escape sequence
- [ ] Test by replacing `<` and `>` with HTML entities `&lt;` and `&gt;`
- [ ] Test payload with both lower and upper case
- [ ] Test to break firewall regex with new line `\r\n`
- [ ] Test with double encoding
- [ ] Test with recursive filters
- [ ] Test injecting anchor tags without whitespace
- [ ] Test by replacing whitespace with bullets
- [ ] Test by changing HTTP methods

### 💾 Test For Stored XSS
- [ ] Identify stored input parameters reflected on the client-side
- [ ] Look for input parameters on the profile page
- [ ] Look for input parameters on the shopping cart page
- [ ] Look for input parameters on the file upload page
- [ ] Look for input parameters on the settings page
- [ ] Look for input parameters on forum/comment pages
- [ ] Test uploading a file with XSS payload as its filename
- [ ] Test with HTML tags

### 🔀 Test For HTTP Parameter Pollution
- [ ] Identify the backend server and parsing method used
- [ ] Try to access the injection point
- [ ] Try to bypass input filters using HTTP Parameter Pollution

### 💉 Test For SQL Injection
- [ ] Test SQL Injection on authentication forms
- [ ] Test SQL Injection on the search bar
- [ ] Test SQL Injection on editable characteristics
- [ ] Try to find SQL keywords or entry point detections
- [ ] Try to inject SQL queries
- [ ] Use tools like SQLmap or HackBar
- [ ] Use Google Dorks to find SQL keywords
- [ ] Try GET-based SQL Injection
- [ ] Try POST-based SQL Injection
- [ ] Try COOKIE-based SQL Injection
- [ ] Try HEADER-based SQL Injection
- [ ] Try SQL Injection with null bytes before the query
- [ ] Try SQL Injection with URL encoding
- [ ] Try SQL Injection with both lower and upper cases
- [ ] Try SQL Injection with SQL Tamper scripts
- [ ] Try SQL Injection with time delay payloads
- [ ] Try SQL Injection with conditional delays
- [ ] Try Boolean-based SQL Injection
- [ ] Try Time-based SQL Injection

### 📂 Test For LDAP Injection
- [ ] Use LDAP search filters
- [ ] Try LDAP Injection for access control bypass

### 📄 Testing For XML Injection
- [ ] Check if the application uses XML for processing
- [ ] Identify the XML Injection point via XML metacharacters
- [ ] Construct XSS payload on top of XML

### 🔌 Test For Server Side Includes (SSI)
- [ ] Use Google Dorks to find SSI
- [ ] Construct RCE on top of SSI
- [ ] Construct other injections on top of SSI
- [ ] Test injecting SSI on login pages, header fields, referrer, etc.

### 🔍 Test For XPATH Injection
- [ ] Identify XPATH Injection point
- [ ] Test for XPATH Injection

### 📧 Test For IMAP/SMTP Injection
- [ ] Identify IMAP/SMTP Injection point
- [ ] Understand the data flow
- [ ] Understand the deployment structure of the system
- [ ] Assess the injection impact

### 📁 Test For Local File Inclusion (LFI)
- [ ] Look for LFI keywords
- [ ] Try to change the local path
- [ ] Use LFI payload list
- [ ] Test LFI by adding a null byte at the end

### 🌐 Test For Remote File Inclusion (RFI)
- [ ] Look for RFI keywords
- [ ] Try to change the remote path
- [ ] Use RFI payload list

### ⌨️ Test For Command Injection
- [ ] Identify the injection points
- [ ] Look for Command Injection keywords
- [ ] Test using different delimiters
- [ ] Test with payload list
- [ ] Test with different OS commands

### 📝 Test For Format String Injection
- [ ] Identify the injection points
- [ ] Use different format parameters as payloads
- [ ] Assess the injection impact

### 🌐 Test For Host Header Injection (HHI)
- [ ] Test by changing the real `Host` parameter
- [ ] Test by adding `X-Forwarded-Host` parameter
- [ ] Test by swapping real `Host` and `X-Forwarded-Host`
- [ ] Test by adding two `Host` parameters
- [ ] Test by adding target values in front of original values
- [ ] Test by adding target with a slash after original values
- [ ] Test with other injections on the `Host` parameter
- [ ] Test by password reset poisoning

### 🔄 Test For Server Side Request Forgery (SSRF)
- [ ] Look for SSRF keywords
- [ ] Search for SSRF keywords under request header and body
- [ ] Identify the injection points
- [ ] Test if the injection points are exploitable
- [ ] Assess the injection impact

### 🧪 Test For Server Side Template Injection (SSTI)
- [ ] Identify the template injection vulnerability points
- [ ] Identify the templating engine
- [ ] Use tplmap to exploit

---

## 8. Error Handling Testing

### ⚠️ Test For Improper Error Handling
- [ ] Identify the error output
- [ ] Analyze the different outputs returned
- [ ] Look for common error handling flaws
- [ ] Test error handling by modifying the URL parameter
- [ ] Test error handling by uploading unrecognized file formats
- [ ] Test error handling by entering unrecognized inputs
- [ ] Test error handling by making all possible errors

---

## 9. Weak Cryptography Testing

### 🔐 Test For Weak Transport Layer Security
- [ ] Test for DROWN weakness on SSLv2 protocol
- [ ] Test for POODLE weakness on SSLv3 protocol
- [ ] Test for BEAST weakness on TLSv1.0 protocol
- [ ] Test for FREAK weakness on export cipher suites
- [ ] Test for Null ciphers
- [ ] Test for NOMORE weakness on RC4
- [ ] Test for LUCKY 13 weakness on CBC mode ciphers
- [ ] Test for CRIME weakness on TLS compression
- [ ] Test for LOGJAM on DHE keys
- [ ] Ensure digital certificates have at least 2048-bit key length
- [ ] Ensure digital certificates use at least SHA-256 signature algorithm
- [ ] Ensure digital certificates do not use MD5 or SHA-1
- [ ] Ensure the validity of the digital certificate
- [ ] Ensure minimum key length requirements are met
- [ ] Look for weak cipher suites

---

## 10. Business Logic Testing

### 💼 Test For Business Logic
- [ ] Identify the logic of how the application works
- [ ] Identify the functionality of all buttons
- [ ] Test by changing numerical values to high or negative values
- [ ] Test by changing the quantity
- [ ] Test by modifying payments
- [ ] Test for parameter tampering

### 📤 Test For Malicious File Upload
- [ ] Test by uploading malicious files
- [ ] Test by putting your IP address in the filename
- [ ] Test by right-to-left override in the filename
- [ ] Test by encoded filename
- [ ] Test by XSS payload in the filename
- [ ] Test by RCE payload in the filename
- [ ] Test by LFI payload in the filename
- [ ] Test by RFI payload in the filename
- [ ] Test by SQL payload in the filename
- [ ] Test by other injections in the filename
- [ ] Test by inserting payload inside an image using the `bmp.pl` tool
- [ ] Test by uploading large files (DoS)

---

## 11. Client Side Testing

### 🌐 Test For DOM Based XSS
- [ ] Try to identify DOM sinks
- [ ] Build payloads targeting the DOM sink type

### 🔗 Test For URL Redirect
- [ ] Look for URL redirect parameters
- [ ] Test for URL redirection on domain parameters
- [ ] Test using a payload list
- [ ] Test by using a whitelisted word at the end
- [ ] Test by creating a new subdomain matching the target
- [ ] Test for URL redirection by XSS
- [ ] Test for URL redirection by profile URL flaw

### 🌍 Test For Cross Origin Resource Sharing (CORS)
- [ ] Look for `Access-Control-Allow-Origin` on the response
- [ ] Use the CORS HTML exploit code for further exploitation

### 🖱️ Test For Clickjacking
- [ ] Ensure `X-Frame-Options` headers are enabled
- [ ] Exploit with iframe HTML code for PoC

---

## 12. Other Common Issues

### ⏳ Test For No-Rate Limiting
- [ ] Ensure rate limiting is enabled
- [ ] Try to bypass by changing the case of endpoints
- [ ] Try to bypass by adding `/` at the end of the URL
- [ ] Try to bypass by adding HTTP headers
- [ ] Try to bypass by adding HTTP headers twice
- [ ] Try to bypass by adding Origin headers
- [ ] Try to bypass by IP rotation
- [ ] Try to bypass by using null bytes at the end
- [ ] Try to bypass by using race conditions

### 📸 Test For EXIF Geodata
- [ ] Ensure the website strips geodata
- [ ] Test with EXIF checker

### 🔗 Test For Broken Link Hijack
- [ ] Ensure there are no broken links
- [ ] Test broken links using the `blc` tool

### 📧 Test For SPF
- [ ] Ensure the website has an SPF record
- [ ] Test SPF using `nslookup` command

### 🔑 Test For Weak 2FA
- [ ] Try to bypass 2FA via poor session management
- [ ] Try to bypass 2FA via the OAuth mechanism
- [ ] Try to bypass 2FA via brute-forcing
- [ ] Try to bypass 2FA via response manipulation
- [ ] Try to bypass 2FA by using activation links to login
- [ ] Try to bypass 2FA by status code manipulation
- [ ] Try to bypass 2FA by changing the email or password
- [ ] Try to bypass 2FA by using null or empty entry
- [ ] Try to bypass 2FA by changing the boolean to false
- [ ] Try to bypass 2FA by removing the 2FA parameter from the request

### 🔢 Test For Weak OTP Implementation
- [ ] Try to bypass OTP by entering old OTP
- [ ] Try to bypass OTP by brute-forcing
- [ ] Try to bypass OTP by using null or empty entry
- [ ] Try to bypass OTP via response manipulation
- [ ] Try to bypass OTP via status code manipulation

---

---

## 13. API Security Testing

### 🔑 JWT (JSON Web Token) Testing
- [ ] Test with the `none` algorithm (`alg: none`) to bypass signature verification
- [ ] Test for weak HMAC secrets via brute-force (`hashcat`, `jwt_tool`)
- [ ] Test for algorithm confusion — RS256 public key used as HS256 secret
- [ ] Test with an expired token — ensure the server rejects it
- [ ] Test with a modified payload without re-signing
- [ ] Check if the JWT `kid` header is vulnerable to SQL injection or path traversal
- [ ] Check if sensitive data (PII, passwords) is stored in JWT payload (base64 is not encryption)
- [ ] Test for JWT token reuse after logout
- [ ] Test for JWT stored insecurely (localStorage vs httpOnly cookie)
- [ ] Check for overly long JWT expiry (`exp`)

### 🌐 GraphQL Testing
- [ ] Test if introspection is enabled on production (`__schema`, `__type`)
- [ ] Test for GraphQL batching attacks (sending multiple queries in one request)
- [ ] Test for deeply nested queries causing DoS (no query depth limit)
- [ ] Test for field duplication abuse (alias-based query amplification)
- [ ] Test for IDOR through GraphQL object IDs
- [ ] Test for unauthenticated mutations
- [ ] Check if errors leak schema or stack trace information
- [ ] Test for SQL/NoSQL injection through GraphQL arguments
- [ ] Test for SSRF via URL-based GraphQL arguments
- [ ] Check if rate limiting is applied per query, not just per request

### 🔌 REST API Testing
- [ ] Test for Broken Object Level Authorization (BOLA/IDOR) on all object IDs
- [ ] Test for Broken Function Level Authorization (accessing admin endpoints)
- [ ] Test for mass assignment — send extra fields in POST/PUT body
- [ ] Test for excessive data exposure — does the API return more fields than the UI shows?
- [ ] Test for lack of resource and rate limiting
- [ ] Test for security misconfiguration — CORS, debug endpoints, verbose errors
- [ ] Test API versioning — older versions (`/v1/`, `/v2/`) may lack newer security controls
- [ ] Check if API keys are exposed in URLs, logs, or responses
- [ ] Test for HTTP verb tampering on API endpoints
- [ ] Test for API endpoint enumeration via fuzzing (`/api/users`, `/api/admin`, etc.)
- [ ] Check if internal API endpoints are exposed externally

### 📦 Mass Assignment
- [ ] Identify all parameters accepted by the API (diff UI-sent vs all accepted)
- [ ] Test by injecting `role`, `isAdmin`, `verified`, `balance` fields in request body
- [ ] Test mass assignment in nested JSON objects
- [ ] Test on both POST (create) and PUT/PATCH (update) endpoints

---

## 14. Modern Web Vulnerabilities

### 📄 XXE (XML External Entity) Injection
- [ ] Test any endpoint that accepts XML input
- [ ] Test for classic XXE to read local files (`/etc/passwd`, `win.ini`)
- [ ] Test for blind XXE via out-of-band DNS/HTTP callbacks (use Burp Collaborator)
- [ ] Test for XXE via file uploads (SVG, DOCX, XLSX, PDF — all can contain XML)
- [ ] Test for XXE via SOAP endpoints
- [ ] Test for XXE with different encodings (UTF-16, UTF-7)
- [ ] Test for XXE-based SSRF using external entity URLs
- [ ] Test for error-based XXE to exfiltrate data
- [ ] Test for XInclude attacks when full XXE is mitigated

### 💣 Insecure Deserialization
- [ ] Identify serialized objects in cookies, hidden fields, API parameters
- [ ] Detect Java serialization (`rO0AB`), PHP (`O:`), Python (`pickle`), .NET (`AAEAAAD`)
- [ ] Test for Remote Code Execution (RCE) via deserialization gadget chains
- [ ] Use `ysoserial` for Java deserialization exploitation
- [ ] Use `phpggc` for PHP deserialization exploitation
- [ ] Test for object injection leading to privilege escalation
- [ ] Test for DoS via deeply nested or large deserialized objects
- [ ] Check if HMAC or digital signature protects serialized data

### 🚇 HTTP Request Smuggling
- [ ] Test for CL.TE smuggling (front-end uses `Content-Length`, back-end uses `Transfer-Encoding`)
- [ ] Test for TE.CL smuggling (front-end uses `Transfer-Encoding`, back-end uses `Content-Length`)
- [ ] Test for TE.TE smuggling (both support Transfer-Encoding, one can be obfuscated)
- [ ] Use Burp Suite's HTTP Request Smuggler extension for detection
- [ ] Test for cache poisoning via request smuggling
- [ ] Test for credential hijacking via request smuggling
- [ ] Test for bypassing front-end security controls via request smuggling

### 🗃️ Web Cache Poisoning / Cache Deception
- [ ] Identify unkeyed inputs (headers, cookies, params) that affect the response
- [ ] Test for cache poisoning via `X-Forwarded-Host`, `X-Forwarded-For`, `X-Original-URL`
- [ ] Test for poisoning the cache with XSS payloads
- [ ] Test for fat GET requests (body parameters in cacheable GET requests)
- [ ] Test for cache deception — tricking the server to cache sensitive user data
- [ ] Test for parameter cloaking (`?param=x&utm_content=y`)
- [ ] Check if `Vary` header is correctly set for user-specific responses
- [ ] Test for unkeyed port and protocol cache poisoning

### 🧬 Prototype Pollution
- [ ] Test for prototype pollution in JSON input (`__proto__`, `constructor.prototype`)
- [ ] Test for client-side prototype pollution via URL query parameters
- [ ] Test for server-side prototype pollution in Node.js applications
- [ ] Test for prototype pollution leading to XSS
- [ ] Test for prototype pollution leading to RCE in server-side JS
- [ ] Use tools like `ppmap` or Burp's DOM Invader for automated detection
- [ ] Test for prototype pollution via `JSON.merge`, `lodash.merge`, or `jQuery.extend`

### 🔌 WebSocket Security Testing
- [ ] Intercept WebSocket handshake and messages using Burp Suite
- [ ] Test for lack of authentication on WebSocket connections
- [ ] Test for CSRF on the WebSocket handshake (no CSRF token)
- [ ] Test for injection attacks (XSS, SQLi) via WebSocket message payloads
- [ ] Test for Cross-Site WebSocket Hijacking (CSWSH) — missing `Origin` header check
- [ ] Test for authorization bypass — can a low-privilege user access high-privilege channels?
- [ ] Test for insecure data exposure over WebSocket messages
- [ ] Test whether WebSocket connections use `wss://` (TLS) or plain `ws://`
- [ ] Test for DoS via sending large or malformed WebSocket frames

---

## 15. Security Headers & CSP

### 🧱 Content Security Policy (CSP)
- [ ] Check if a CSP header is present (`Content-Security-Policy`)
- [ ] Identify `unsafe-inline` directives — allow inline script execution
- [ ] Identify `unsafe-eval` directives — allow `eval()` usage
- [ ] Check for overly permissive `script-src *` or `default-src *`
- [ ] Test for CSP bypass via JSONP endpoints on whitelisted domains
- [ ] Test for CSP bypass via AngularJS client-side template injection on whitelisted CDNs
- [ ] Test for CSP bypass via open redirects on whitelisted domains
- [ ] Check if `report-uri` or `report-to` is configured to catch violations
- [ ] Test for `data:` URI bypass in `img-src`

### 🏷️ HTTP Security Headers Audit
- [ ] Ensure `Strict-Transport-Security` (HSTS) is set with `includeSubDomains` and `preload`
- [ ] Ensure `X-Content-Type-Options: nosniff` is set
- [ ] Ensure `X-Frame-Options: DENY` or `SAMEORIGIN` is set (or CSP `frame-ancestors`)
- [ ] Ensure `Referrer-Policy` is set to `no-referrer` or `strict-origin-when-cross-origin`
- [ ] Ensure `Permissions-Policy` disables unused browser features (geolocation, camera, etc.)
- [ ] Ensure `Cache-Control: no-store` on sensitive pages
- [ ] Ensure `X-Powered-By` and `Server` headers are removed or obscured
- [ ] Check for information leakage in custom headers

### 🔗 Subresource Integrity (SRI)
- [ ] Ensure all externally hosted scripts (`<script src>`) have `integrity` attributes
- [ ] Ensure all externally hosted stylesheets have `integrity` attributes
- [ ] Verify SRI hashes are correct and up to date

---

## 16. OAuth 2.0 & SSO Testing

### 🔐 OAuth 2.0 Flow Testing
- [ ] Test for `state` parameter absence — enables CSRF on OAuth flow
- [ ] Test for open redirect in the `redirect_uri` parameter
- [ ] Test for `redirect_uri` bypass using path traversal (`/callback/../evil`)
- [ ] Test for `redirect_uri` bypass using subdomains (`evil.trusted.com`)
- [ ] Test for authorization code reuse — code must be single-use
- [ ] Test for authorization code leakage via Referer header
- [ ] Test for access token leakage in URL fragments or logs
- [ ] Test for scope escalation — request higher scopes than granted
- [ ] Test for token substitution — use another user's authorization code
- [ ] Test implicit grant flow for token leakage in URL
- [ ] Check if PKCE (`code_challenge`) is enforced for public clients

### 🔑 SSO & SAML Testing
- [ ] Test for SAML signature wrapping attacks (XXE via SAML XML)
- [ ] Test for missing signature verification on SAML assertions
- [ ] Test for SAML replay attacks — reuse a valid SAML response
- [ ] Test for XML signature exclusion bypass
- [ ] Test if the `NameID` can be manipulated to impersonate other users
- [ ] Check for overly permissive SAML attribute mapping
- [ ] Test for account linking abuse (link attacker account to victim identity)

### 🌐 OpenID Connect Testing
- [ ] Test for `nonce` parameter absence — enables replay attacks
- [ ] Test for ID token validation bypass
- [ ] Test for `iss` (issuer) and `aud` (audience) claim validation
- [ ] Test for authorization code injection into the ID token flow

---

## 17. Supply Chain & Dependency Testing

### 📦 Frontend Dependency Analysis
- [ ] Enumerate all JavaScript libraries and their versions (via Wappalyzer, Retire.js)
- [ ] Check for known CVEs in detected JS libraries (`npm audit`, Retire.js)
- [ ] Test for prototype pollution in third-party libraries
- [ ] Check if outdated jQuery versions are in use (XSS gadgets)
- [ ] Look for exposed `package.json`, `yarn.lock`, `package-lock.json` files
- [ ] Check if source maps (`.js.map`) are exposed in production — leaks source code

### 🔗 Dependency Confusion
- [ ] Identify internal package names from `package.json`, error messages, or job postings
- [ ] Check if internal package names exist on public registries (npm, PyPI, RubyGems)
- [ ] Test if the build system prefers public registry over internal for same-named packages

### 🗂️ Exposed Development Artifacts
- [ ] Check for exposed `.git` directory (`/.git/config`)
- [ ] Check for exposed `.env` files (API keys, DB credentials)
- [ ] Check for exposed `Dockerfile`, `docker-compose.yml`
- [ ] Check for exposed CI/CD config files (`.github/workflows`, `.gitlab-ci.yml`, `Jenkinsfile`)
- [ ] Check for exposed cloud config (`aws_credentials`, `.s3cfg`)
- [ ] Check for exposed `wp-config.php`, `config.php`, `database.yml`
- [ ] Check for exposed API documentation (`/swagger-ui`, `/api-docs`, `/openapi.json`)
- [ ] Check for exposed debug endpoints (`/debug`, `/trace`, `/actuator`, `/metrics`)

---

## 18. Email Security Testing

### 📧 Email Authentication
- [ ] Check for SPF record using `nslookup -type=TXT domain.com`
- [ ] Check for DKIM record (`selector._domainkey.domain.com`)
- [ ] Check for DMARC record (`_dmarc.domain.com`) and ensure policy is `reject` or `quarantine`
- [ ] Ensure DMARC `rua` / `ruf` reporting addresses are configured
- [ ] Test for email spoofing if SPF/DKIM/DMARC are misconfigured
- [ ] Check for subdomain DMARC coverage (`sp=reject`)

### 📬 Email Functionality Testing
- [ ] Test for email header injection in user-supplied name/subject fields
- [ ] Test for open mail relay — can the server be used to send arbitrary emails?
- [ ] Test for password reset token leakage via `Referer` header in reset emails
- [ ] Test if confirmation/reset emails can be sent to unverified arbitrary addresses
- [ ] Check if email enumeration is possible through registration/reset responses

---

<div align="center">

**Made for security professionals and bug bounty hunters.**  
*Always test with proper authorization. Never test systems you don't own or have explicit permission to test.*

-github/sankarlmao
-linkdin/in/sankarcy
</div>