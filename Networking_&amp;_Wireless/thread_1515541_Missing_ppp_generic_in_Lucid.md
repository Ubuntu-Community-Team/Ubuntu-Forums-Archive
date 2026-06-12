---
title: "Missing ppp_generic in Lucid"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by genesys87 on 2010-06-22
Today I installed Ubuntu Lucid, and now I cannot connect with my adsl usb modem.
Previously, on older versions, I used pppd, but now it gives me this error:
```

Plugin /usr/lib/pppd/2.4.5/pppoatm.so loaded.
Couldn't open the /dev/ppp device: Permission denied
FATAL: Module ppp_generic not found.
Kernel doesn't support ppp_generic - needed for PPPoATM

```

There is no module ppp_generic in the system, nor ppp_generic.c to compile in ppp related packages.
Has something changed from karmic regarding this module?

Thanks for your help.

---

### Post by egyptianbman on 2011-05-07
I know this is an old item but there were no replies and I am receiving a similar issue with Ubuntu 11.04:

```
user@cr-48-ubuntu:~$ sudo pppd
[sudo] password for user: 
Couldn't open the /dev/ppp device: No such device or address
FATAL: Module ppp_generic not found.
pppd: Please load the ppp_generic kernel module.

```

---

