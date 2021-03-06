source  : https://jwt.io/introduction

### What is JSON Web Token?
* JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. 
* This information can be verified and trusted because it is digitally signed. 
* JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.

Although JWTs can be encrypted to also provide secrecy between parties, we will focus on signed tokens. Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims from other parties. When tokens are signed using public/private key pairs, the signature also certifies that only the party holding the private key is the one that signed it.

### How do JSON Web Tokens work?
1. In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned. Since tokens are credentials, great care must be taken to prevent security issues. In general, you should not keep tokens longer than required.

You also should not store sensitive session data in browser storage due to lack of security.

2. Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema. The content of the header should look like the following:

```Authorization: Bearer <token>```

This can be, in certain cases, a stateless authorization mechanism. The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources. If the JWT contains the necessary data, the need to query the database for certain operations may be reduced, though this may not always be the case.

3. If the token is sent in the Authorization header, **Cross-Origin Resource Sharing (CORS)** won't be an issue as it doesn't use cookies.

![image from jwt.io](https://cdn2.auth0.com/docs/media/articles/api-auth/client-credentials-grant.png)

The above image is from jwt.io

### Why should we use JSON Web Tokens?

##### Benefits of JSON Web Tokens (JWT) over Simple Web Tokens (SWT) and Security Assertion Markup Language Tokens (SAML) : 

* As JSON is less verbose than XML, when it is encoded its size is also smaller, making JWT more compact than SAML. This makes JWT a good choice to be passed in HTML and HTTP environments.
* Security-wise, SWT can only be symmetrically signed by a shared secret using the HMAC algorithm **HMAC : Hash based Message Authentication Code** . However, JWT and SAML tokens can use a public/private key pair in the form of a X.509 certificate for signing. 
* Signing XML with XML Digital Signature without introducing obscure security holes is very difficult when compared to the simplicity of signing JSON.
* JSON parsers are common in most programming languages because they map directly to objects. Conversely, XML doesn't have a natural document-to-object mapping. This makes it easier to work with JWT than SAML assertions.
* Regarding usage, JWT is used at Internet scale. This highlights the ease of client-side processing of the JSON Web token on multiple platforms, especially mobile.
