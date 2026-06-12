---
title: "Firefox + Kerberos"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by martijntje on 2009-08-30
Can anybody tell me what packages I have to install to enable Firefox to authenticate with kerberos?

I have Kerberos set up, I can run kinit fine, but using Fx to browse to a page with Kerberos authentication always gives me a 401.

---

### Post by munno on 2010-01-20
Hi, I had some different Kerberos problems and bumped into your post while googling. Did you ever get it working? Was just wondering since you haven't mentioned it, do you have the domains of the kerberized services in the following Firefox settings?

```
network.negotiate-auth.delegation-uris 
network.negotiate-auth.trusted-uris 
```

(You will find the settings by typing about:config to address bar and using the search box..)

---

