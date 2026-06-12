---
title: "onboard LAN on ALiveNF6P-VSTA"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by jm_smits on 2009-01-23
I have installed Ubuntu 8.10 (64 bit) on a brand new computer, but I find that the onboard LAN does not work. The motherboard is ALiveNF6P-VSTA, the cpu is an AMD Athlon 64 X2 5000+.

The Internet connection is a simple DHCP through a router, which works just fine on my laptop. The LAN was tested in the shop, where they managed to use it to boot from their network. So the hardware itself seems to be fine. 

I have tried to install the package NFORCE-Linux-x86_64-1.0-0310-pkg1 (NVidia network driver), but it simply fails without giving any details, except for referring to the log file, which I have attached.

When I type: 'sudo lshw', the output contains:
*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0e:0f:3a:1c:1b:5e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Does anybody have any suggestions?

Cheers,
Roy

---

### Post by jm_smits on 2009-01-24
No ideas from anybody? I'm getting rather desperate. I've just burned a Suse CD and I'm not afraid to use it ;).

Roy

---

