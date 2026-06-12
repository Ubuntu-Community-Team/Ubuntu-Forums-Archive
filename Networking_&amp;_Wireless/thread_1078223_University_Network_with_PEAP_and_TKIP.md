---
title: "University Network with PEAP and TKIP"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by woody22075 on 2009-02-23
I have Ubuntu 8.10 and am running wicd as network manager.  I am having trouble connecting to my University's wireless network.  The network uses WPA with TKIP and a root certificate.  I have configured the connection on wicd with PEAP and TKIP and have entered my login information.  I have selected the appropriate .pem file--I converted the .cer file provided by the University to .pem using openssl and the following command: 

$openssl x509 -in [filename.cer] -out [filename.pem]

But I am still failing at the authentication phase.

Thank you for any insight!

M.

---

