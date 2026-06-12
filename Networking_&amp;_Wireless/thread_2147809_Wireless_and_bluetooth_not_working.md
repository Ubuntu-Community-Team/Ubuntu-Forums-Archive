---
title: "Wireless and bluetooth not working"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by tilakrajsingh on 2013-05-23
I have a dell inspiron 5420 model. My wireless was working fine but  there was some problem with my bluetooth. While trying to do so my wifi  also stopped working. I tried numerous methods on various forums but  couldnt correct it. Could somebody please help me.

lspci | grep Network
```
Network controller: Broadcom Corporation Device 4365 (rev 01)
```
rfkill list shows everything blocked...rfkill unblock all doesnt unblocks anything...

Found that I have to install a deb file but it seems to conflict... here is the output..

```
dpkg: regarding wireless-bcm43142-dkms-6.20.55.19_amd64.deb containing wireless-bcm43142-oneiric-dkms:
 wireless-bcm43142-oneiric-dkms conflicts with bcmwl-kernel-source
  bcmwl-kernel-source (version 6.20.155.1+bdcom-0ubuntu0.0.1) is present and installed.
dpkg: error processing wireless-bcm43142-dkms-6.20.55.19_amd64.deb (--install):
 conflicting packages - not installing wireless-bcm43142-oneiric-dkms
Errors were encountered while processing:
 wireless-bcm43142-dkms-6.20.55.19_amd64.deb
```

Could someone please help me. I need it urgent...

---

### Post by tilakrajsingh on 2013-05-23
okay I installed the deb file but still the wifi doesnt seem to work

---

