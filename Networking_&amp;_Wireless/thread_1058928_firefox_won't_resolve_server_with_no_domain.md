---
title: "firefox won't resolve server with no domain"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by cnkbrown on 2009-02-03
I have /etc/nsswitch.conf configured to use /etc/hosts, and I have a line in /etc/hosts for 'servera'.

When I 'nslookup servera', I get the expected Ip address.

However, when I use firefox to open 'https://servera' I get an error that the following;

[code]
    Unable to determine IP address from host name for 

The dnsserver returned:

    Name Error: The domain name does not exist. 

This means that:

 The cache was not able to resolve the hostname presented in the URL. 
 Check if the address is correct. 
[code]

if the server had a domain suffix, i could set the proxy configuration to bypass the cache, and get the right address from /etc/hosts, but since firefox hits the cache first, it always fails.

Is there a way to configure around this?

---

### Post by cnkbrown on 2009-02-03
Never mind - dumb question.

---

