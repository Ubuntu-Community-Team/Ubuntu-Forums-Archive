---
title: "Wifi Config file location."
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by nova_intel on 2011-04-23
Hey there, can anyone point me to were the wifi config file is stored in Ubuntu 10.10. I need the file to pull out the configuration of a WPA2 enterprise network so as to try to get my Archos 7 Home Tablet to connect to the same network. Thanks for any help.

---

### Post by jfeeney on 2011-06-27
Hey,

I just had the exact same issue trying to connect to my university's secure network that uses WPA2 Enterprise.

The certificates file can be found at:  /etc/ssl/certs/ca-certificates.crt

**all other certs are in the same folder in case your network uses a different one.

Once I pointed here, I connected no problem. I'm also quite impressed, ubuntu connects quicker and is more reliable with my university network than Windows 7.

Cheers,
Justin

---

