---
title: "Does anyone know why Intrepid produces this &quot;kernel IP routing table&quot;?"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by jhary on 2009-03-30
I was playing with fwbuilder (GUI firewall builder) on a just-built, sandbox machine with 2 NIC ports (so that I might add the firewall to a home-based Asterisk PBX). Intrepid was installed with RAID1 and both NICs - install found them both and they were both operational.  The Internet had been connected to eth0 (the onboard port).

  Recently, I was unable to connect with the Internet, and, in looking at the routing table, discovered several things, namely:
    1. my loopback address is the old Class B nemesis address, 169.254/16 instead of 127.0.0.1.
    2. there are 2 default gateways listed which is causing the problem (if I manually delete the default eth1 gateway, then traffic goes through eth0 to the Internet).
    3,  Network Tools does show a loopback of 127.0.0.1. (I can still connect to localhost).

COMMENTS:
1.	I realize I probably will have to just add the ifconfig/route commands to rc.local, but really would like to understand what is happening.  Also, when fwbuilder firewall is install, I think I can handle the routing there – maybe!
2.	The /etc/network/interfaces file that you see has been expanded from the install version, because I wanted to document changes that I was making and to make certain that there was no ambiguity – hence the hardware lines, etc.
3.	Something is still wiping out my /etc/resolv.conf file, even though I have “false” in the NetworkManager settings file.  The process command shows the NetworkManager daemon is running and using the settings file.  I have learned to stay away from the Network Manager, since it isn’t “in sync” with what Network Tools shows.  On the panel, the icon has the small warning, so that I know if I select “check connection”, it will display a warning window that “there are no active connections”, despite the fact I have both ports connected and Network Tools shows the correct connections.
4.	I had been doing all system updates as they became available, so I don’t know if one of the updates affected my system (negatively, that is).
5.	Don’t think this is pertinent, but, just in case: I am using a Gigabyte motherboard with an AMD Phenom II 940 CPU (see the version info).

QUESTIONS:
1.	Does anyone have ideas/comments/suggestions?
2.	In the event that I add some “route” commands to rc.local, does anyone happen to know in which scripts the routing protocols are set at boot time?  Shouldn’t they really be removed or commented out?
3.	Does anyone know if disabling the NetworkManager daemon has unintended consequences?

The attachment lists network relevant files on the Intrepid box.

---

