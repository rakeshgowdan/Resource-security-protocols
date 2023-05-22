# Resource-security-protocols

# five most commonly used authentication protocols 

# LDAP

LDAP (Lightweight Directory Access Protocol) is a software protocol for enabling anyone to locate organizations, individuals, and other resources such as files and devices in a network, whether on the public Internet or a corporate intranet.

LDAP is a lightweight subset of the X.500 Directory Access Protocol, and has been around since the early 1990s. It was developed by the University of Michigan as a software protocol to authenticate users on an AD network, and it enables anyone to locate resources on the Internet or on a corporate intranet. LDAP single sign-on also lets system admins set permissions to control access the LDAP database. That way, you can be certain that data stays private.

LDAP is more flexible. It can accommodate other types of computing including Linux/Unix.

It is fair to say that LDAP has become a popular program. It served as the foundation on which Microsoft built Active Directory, and has been instrumental in the development of today’s cloud-based directories (also known as Directories-as-a-Service).

LDAP sends messages between servers and client applications which can include everything from client requests to data formatting.

On a functional level, LDAP works by binding an LDAP user to an LDAP server. The client sends an operation request that asks for a particular set of information, such as user login credentials or other organizational data. The LDAP server then processes the query based on its internal language, communicates with directory services if needed, and responds. When the client receives the response, it unbinds from the server and processes the data accordingly.

LDAP is ideal for situations where you need to access data frequently but only add or modify it now and then. That means it works especially well with passwords: it can deal with password expiration, password quality validation, and account lockout after a user has too many failed attempts. An LDAP agent can authenticate users in real-time—it compares the data presented to what’s stored in the LDAP database instantly, so no sensitive user data needs to be stored in the cloud.

![how-ldap-works](https://github.com/rakeshgowdan/Resource-security-protocols/assets/41374671/732d50fa-cd3f-4e9e-85ed-66adf8ddf7aa)

# Kerberos

Kerberos is a network authentication protocol. It is designed to provide strong authentication for client/server applications by using secret-key cryptography. A free implementation of this protocol is available from the Massachusetts Institute of Technology. Kerberos is available in many commercial products as well.

Here are the most basic steps taken to authenticate in a Kerberized environment.

Client requests an authentication ticket (TGT) from the Key Distribution Center (KDC).
The KDC verifies the credentials and sends back an encrypted TGT and session key.
Client requests to access an application on a server. A ticket request for the application server gets sent to the KDC which consists of the client’s TGT and an authenticator.
The KDC returns a ticket and a session key to the user.
The ticket is sent to the application server. Once the ticket and authenticator have been received, the server can authenticate the client.
The server replies to the client with another authenticator. On receiving this authenticator, the client can authenticate the server.

![kerberos_authentication_process_diagram-f_mobile](https://github.com/rakeshgowdan/Resource-security-protocols/assets/41374671/1f201260-e4ce-4828-bdc6-bbeaaca522da)

# Oauth 2

OAuth 2 is an authorization framework that enables applications to obtain limited access to user accounts on an HTTP service, such as Facebook, GitHub, and DigitalOcean.

Here is a description of the basic steps in the authorization process:

Application requests authorization for access service resources from the user.
If that user approves then the application receives an authorization grant.
Application requests an access token from the authorization server (API). This is done by presenting its identity and the authorization grant.
If the application identity is authenticated and the authorization grant is valid, the API issues an access token to the application. Authorization is complete.
The application requests the resource from the API and presents the access token for authentication.
If the access token is valid, the API serves the resource to the application.

![abstract_flow](https://github.com/rakeshgowdan/Resource-security-protocols/assets/41374671/9b741e46-b8ba-4429-a843-0da8299256fc)

How OAuth2 is Used for SSO

The process of exchanging information is slightly different in OAuth2 as opposed to SAML 2.0, with the main difference being that the client (your browser or app) is called one extra time. You request a login to the relevant app, it sends you a ‘grant’ to request access from the SSO provider, which in turn gives you an access token, which you pass to the resource server. This is all done to ensure that it is actually you making the request, rather than a malicious third party. Afterwards, the app communicates directly with the SSO provider in OAuth2 to login.

![image](https://github.com/rakeshgowdan/Resource-security-protocols/assets/41374671/b1c0bbc4-8579-4d0e-a99b-3eba4cf5b738)

The diagram above depicts this interaction well. The flow is different from that prescribed by SAML 2.0, but the end result is the same.

# SAML
Security Assertion Markup Language (SAML) is an XML-based, open-standard data format for exchanging authentication and authorization data between parties, in particular, between an identity provider and a service provider. SAML is a product of the OASIS Security Services Technical Committee.

JumpCloud is one of the best Single Sign-On (SSO) providers which supports SAML authentication protocols. JumpCloud’s SSO provides SAML integrations with 700 popular business applications (including Kisi) and automated user lifecycle management features like Just-in-Time (JIT) provisioning and SCIM provisioning/deprovisioning.

Here is a description of the typical steps in the authentication process:

User accesses remote application using a link on an intranet or similar and the application loads.
Application identifies user’s origin (by application subdomain, user IP address, or similar). It redirects the user back to the identity provider, asking for authentication.
User either has an existing active browser session with the identity provider or establishes one by logging into the identity provider.
Identity provider builds authentication response in the form of an XML-document containing user’s username or email address. This is then signed using an X.509 certificate and then posted to the service provider.
Service provider (which already knows the identity provider and has a certificate fingerprint) retrieves authentication response and validates it using certificate fingerprint.
The identity of the user is established, and the user is provided with app access.


<img width="653" alt="saml-auth" src="https://github.com/rakeshgowdan/Resource-security-protocols/assets/41374671/87eec68e-43ab-4987-bbd3-14b21c331170">

# SAML 2.0

SAML 2.0 stands for “Security Access Markup Language,” and is essentially a way to encode text that is used specifically to exchange identification information. SAML is an open standard, meaning anyone can have access to the documentation, and ensure that their code adheres to it. As opposed to a proprietary or closed standard, which would ‘belong’ to a certain company, and that nobody else would have permission to use.

The direct upshot is that this has become one of the primary standards for SSO. The fact that it is an open standard means that any application can make sure that their authentication requests are up to par, and when that is satisfied, they can be enabled with SSO providers, like Okta and OneLogin.

Concretely, a markup language is a wrapper around plaintext that modifies it in such a way as to be readable by computers. The most famous example is HTML, which stands for hypertext markup language. It looks like items in brackets around text, like this: <body>Plaintext</body>. These commands turn the text into machine language, and for SAML 2.0, encrypt it in a universally recognizable and secure way, specifically for identification information.

The last point to note is that SAML 2.0 is optimized for web applications. This means that if you’re transmitting information using a web browser, then SAML 2.0 is the right way to go. However, if you’re attempting a login in a native app, like an iPhone or Android app, it will not work as well, and you’re better off using OAuth2, which we’ll discuss next.

How SAML 2.0 is Used for SSO

As mentioned, SAML 2.0 is a standard for encrypting identification information. The following diagram gives an overview of the process. There are three players here: The client (you, or your web browser), the resource server (the app you are trying to access), and the authorization server (the SSO provider). They exchange information in the following way, when you send a new login attempt on your web browser to the resource server.

![image](https://github.com/rakeshgowdan/Resource-security-protocols/assets/41374671/ded90e43-05f7-47e9-a74f-8147e91d1c45)

Basically, the complicated path of arrows denotes that you send the request to login to the app, it then requests the SSO provider for login credentials in SAML 2.0, which then prompts you, the user, to agree to send the information to the app via the provider, and then the ID information is sent to the app in SAML 2.0, and voilà, you’re logged in!

# RADIUS

Remote Authentication Dial-In User Service (RADIUS) is a networking protocol that provides centralized Authentication, Authorization, and Accounting (AAA or Triple A) management for users who connect and use a network service.

RADIUS authentication begins when the user requests access to a network resource through the Remote Access Server (RAS). The user enters a username and a password, which are encrypted by the RADIUS server before being sent through the authentication process.

Then the RADIUS server checks the accuracy of the information by employing authentication schemes to verify the data. This is done by comparing the user-provided information against a locally stored database or referring to external sources such as Active Directory servers.

The RADIUS server will then respond by accepting, challenging or rejecting the user. Individual users may be granted restricted access without affecting other users. In the case of a challenge, the RADIUS server requests additional information from the user to verify their user ID - which may be a PIN or a secondary password. In the case of a reject, the user is unconditionally denied all access to the RADIUS protocol.

![remote_access_using_radius_protocol-f_mobile](https://github.com/rakeshgowdan/Resource-security-protocols/assets/41374671/4189ac8a-72b2-45d3-acc9-863a7cea9370)


--------------------------------------------------------------------------------------------------------------------

# ADFS

Active Directory Federation Services (ADFS)
Microsoft developed ADFS to extend enterprise identity beyond the firewall. It provides single sign-on access to servers that are off-premises. ADFS uses a claims-based access-control authorization model. This process involves authenticating users via cookies and Security Assertion Markup Language (SAML).

That means ADFS is a type of Security Token Service, or STS. You can configure STS to have trust relationships that also accept OpenID accounts. This lets companies bypass setting up separate registration and user credentials when adding new users—they can just use the existing OpenID credentials.

ADFS is focused on Windows environments

![image](https://github.com/rakeshgowdan/Resource-security-protocols/assets/41374671/dcf8311d-424e-43c6-ab77-3df0ac5bad8f)
![image](https://github.com/rakeshgowdan/Resource-security-protocols/assets/41374671/12507934-3138-4ae3-aa91-e4271c604da5)


ADFS is a valuable tool, but it does have a few drawbacks:

It’s cumbersome to use when integrating with cloud or non-Microsoft mobile applications
It requires IT resources to install, configure, and maintain
It’s difficult to scale and requires tedious application installations
Although it’s technically a free offering from Microsoft, using ADFS can pose hidden costly under-the-hood issues, like the IT costs to maintain it.
