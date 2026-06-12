---
title: "Squid AD auth help"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by shikomizue on 2010-11-09
Hi everyone,

I am trying to get squid to work as a sibling so I can turn internet access on/off for computer labs.

Currently there is already another squid 2.5 which is the parent. Due to the setup I can't make any changes or view this squids configuration.

Using Ubuntu 10.10 64bit and squid 2.7. Once its working I will change the proxy settings of browsers on computers that we want to control.


I am having trouble getting squid to pass on current users log on details to the parent. Which then blocks access.

Below is my current conf file.

```
http_port 3128

acl all src 0.0.0.0/0.0.0.0

#allow all sites to use connect to us via HTTP
http_access allow  all

#allow all sites to use us as a sibling
icp_access  allow  all



auth_param basic program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-basic
auth_param ntlm children 30
auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp
auth_param basic realm blahblah.net
auth_param basic credentialsttl 2 hour
auth_param basic children 5

cache_peer parentip parent parentport 0 proxy-only default login=PASS
cache_log /var/log/squid/access.log
```If I change the login to username:password it all works fine. But I need it to work with current logged in details.

Any suggesitons?

---

