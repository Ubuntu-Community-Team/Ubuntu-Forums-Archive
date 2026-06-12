---
title: "Belkin F5D7050 Adapter"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by cdawley4 on 2009-06-05
Hi,

I have a Dell Inspiron 1200 laptop that I want to add a Belkin F5D7050 wireless adapter to.  I am currently using a Linksys PCMCIA card.  Sometimes the linksys card doesn't connect and I wanted to use the Belkin card with it.  I have read where I can use ndiswrapper with it, but can't seem to get the adapter to turn on.  When I run lsusb, I get the following output.

```
chris@chris-laptop:~$ lsusb
Bus 001 Device 003: ID 0324:bc06  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Ubuntu won't recognize my adapter.  Is there anything else I can try?  I tried ndiswrapper with rt73.inf and can't get anywhere.  I am using 9.04.

Thanks,

Chris

---

