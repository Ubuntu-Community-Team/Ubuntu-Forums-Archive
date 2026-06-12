---
title: "Ubuntu Support for WPA2 Enterprise with EAP FAST Authentication"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by Joseph Brown on 2009-10-08
My company is now using WPA2 Enterprise security with EAP FAST Authentication. I have found very little documentation on this. Does anyone know how I can get this setup on my Ubuntu 9.04 laptop?

---

### Post by spd106 on 2009-10-09
There's an old bug report open for adding EAP FAST support to wpa_supplicant.
[https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/34982](https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/34982)

But until then you'll need to compile it separately. There are some instructions on the following help wiki page.
[https://help.ubuntu.com/community/WifiDocs/Device/CiscoCB21AG](https://help.ubuntu.com/community/WifiDocs/Device/CiscoCB21AG)

---

