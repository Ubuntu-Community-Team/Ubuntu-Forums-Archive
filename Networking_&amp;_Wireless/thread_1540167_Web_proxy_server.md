---
title: "Web proxy server"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by turtle.ninja on 2010-07-27
Hello,
What package/s should I install in order to have my own web proxy server (like anonymizer.com) ?

Turtle

---

### Post by chopinhauer on 2010-07-27
The best standalone proxy is probably [Squid]("https://help.ubuntu.com/community/Squid") whose version 2.7 ships with Ubuntu Lucid Lynx.

However it doesn't anonymize requests in its default configuration. You'll need to deactivate the [forwarded_for]("http://www.squid-cache.org/Versions/v2/2.7/cfgman/forwarded_for.html") directive. Moreover you'll need to decide which HTTP headers to pass through to the final server as described in the [Squid FAQ]("http://wiki.squid-cache.org/SquidFaq/ConfiguringSquid#Can_Squid_anonymize_HTTP_requests.3F") and on [Lutz Donnerhacke]("http://www.iks-jena.de/mitarb/lutz/anon/web.en.html") website.

If you want to access Squid from outside your local network, authentication is necessary. The easiest to deploy should be [PAM Authentication]("http://www.howforge.com/how-configure-pam-authentication-squid"), which will authenticate requests to the Squid server with the servers local user credentials.

Note that you can not achieve the same amount of privacy as you get with anonymizer.com since requests will always trace back to your server.

---

### Post by turtle.ninja on 2010-07-28
Ok, let's put the anonymous part afterwards.

If I deploy a proxy server with Squid will someone be able to use it if he/she has to use ISP's proxy? 

User -> ISP's Proxy -> Filtered Internet -> My Proxy -> Unfiltered Internet

I am assuming "My Proxy" is reachable since it is not being filtered by ISP's Proxy. "Unfiltered Internet" is equal to Internet without restrictions.

---

### Post by martine4161 on 2010-07-28
Web proxy server is very good topic to discuss. Here everyone can their thoughts and their experience about proxy server. squid is very good proxy server. Squid is a full-featured web proxy cache server application which provides proxy and cache services for Hyper Text           Transport Protocol (HTTP), File Transfer Protocol (FTP), and other popular network protocols. If you would like to redirect the all HTTP traffic through the proxy without needing to set up a proxy manually in all your applications you will need to add some rules

---

### Post by chopinhauer on 2010-07-29
> **turtle.ninja said:**
> 
If I deploy a proxy server with Squid will someone be able to use it if he/she has to use ISP's proxy? 


Chaining two HTTP servers will not work out of the box with Firefox. However, one may use tools such as **proxytunnel** to achieve it.

---

