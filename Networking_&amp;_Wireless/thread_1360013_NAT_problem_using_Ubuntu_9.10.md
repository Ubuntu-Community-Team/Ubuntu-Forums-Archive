---
title: "NAT problem using Ubuntu 9.10"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by linux411 on 2009-12-20
Hello everyone,

  I had been using Slackware 13 but decided to try Ubuntu again. I am more used to editing config files than using a GUI so this may be 2 sided. I was using Ubuntu 9.04 and running a NAT gateway with no issues. However, when I install Ubuntu 9.10, it seems that both interfaces cannot exist in peace. Details as follows .....

eth0 - Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03) (LAN)

eth1 - Ricoh Co Ltd RL5c475 (rev 81) with a Dell Wireless 5100 PCMCIA card. (WAN)

Each will run by themselves, but will not run together in order to setup a NAT. When eth0 is up, it shuts down eth1. When eth1 is up, it shuts down eth0. Never had a problem either with Ubuntu 9.04 or any Linux distro. I would like to mention that the WIFI manager for GNOME seems to be an issue, as editing the rc.inet1.conf, rc.wireless.conf and running rc.inet1 has always worked in the past. However, the GNOME WIFI manager enjoys overwritting changes. Thanks in advance for help. If I can resolve this issue, I can happily upgrade to Ubuntu 9.10.

---

### Post by Iowan on 2009-12-20
Network Manager began with Hardy (8.04). Although this laptop will occasionally connect via wired and wireless at the same time, Network Manager ordinarily manages only one interface at a time.  You should be able to configure one of the interfaces via */etc/network/interfaces*.(Network Manager will probably deny it's existence...)

---

