---
title: "Cisco VPN AnyConnect error kubuntu 11.10"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by gdesanti on 2011-11-11
Hi everybody,

I have kubuntu 11.10 32 bits, and installed cisco vpn any connect, but when I try to connect receive the following error:

"Posture Assessment Failed: hostscan prelogin error" or something like that.

Any idea?

Thank you in advance for your help

---

### Post by casevh on 2011-12-06
Cisco unfortunately searches a hard-coded list for libraries. Here is an ugly hack that will create symlinks for the missing files:

sudo ln -s /usr/lib/i386-linux-gnu/libcurl.so.4.2.0 /usr/lib/libcurl.so
sudo ln -s /usr/lib/i386-linux-gnu/libssl.so.1.0.0 /usr/lib/libssl.so
sudo ln -s /usr/lib/i386-linux-gnu/libcrypto.so.1.0.0 /usr/lib/libcrypto.so

HTH,
casevh

---

