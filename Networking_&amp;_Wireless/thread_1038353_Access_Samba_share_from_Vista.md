---
title: "Access Samba share from Vista"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by HokeyFry on 2009-01-12
I am trying to access a samba share I have on my network. The server running Samba is running Ubuntu Server 8.10. The client is Windows Vista.

Basically I can connect to some of my shares as a guest (the ones with 'guest ok = yes', but when I try to authenticate with my username, it says that it cannot authenticate with my credentials. I have already set LsaCompatibility to 1 on the Vista machine, and everything was going great until I booted the machine up today. I am very sure the problem lies with Samba as I had the same issue last night and I had to remove and reinstall Samba to make it work again. Any ideas why authentication is not working? I have not turned off/power cycled the server since last night.

---

