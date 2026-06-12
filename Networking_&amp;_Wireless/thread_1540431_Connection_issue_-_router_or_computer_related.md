---
title: "Connection issue - router or computer related?"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by deveborn on 2010-07-27
I have a hopeless network problem annoying me. The wireless computers in my network is unreachable from other computers in LAN but possible to ping from the router.

My network:

Netgear DG834GT router 
Linux (suse) server (web and samba share), wired connection
Windows XP home PC, wired connection
Mythbuntu PC (an ubuntu version), wireless connection
Laptop (Windows XP pro/Linux Ubuntu), wireless connection
Network Printer

DHCP configuration with address reservation for SUSE server, Mythbuntu PC and Printer. NO wireless isolation. No router firewall rules within LAN but port forwarding of HTTP, MYSQL and SVN traffic to suse server. NO DMZ.

Problem description

Want to communicate with Mythbuntu PC by VLC and samba. Mythbuntu PC connects fine to internet and can reach samba shares from SUSE server. Suse server can be accessed via VLC. Mytbuntu server can not (not even respond to ping from any LAN computer). However, Mythbuntu PC respond to ping from router!? I have reconfigured the router several times and reset it to factory defaults. I have realized that it is possible to connect to the Mythbuntu PC some minutes after a router reboot. But soon the box will be isolated. Months ago all this was working for me and I know that I have been fiddle with the Mythbuntu box but now I dont even know if I have a router or a computer issue!

Someone kind that have a suggestion?

---

### Post by deveborn on 2010-07-29
I have now found this issue to be computer related. It seams to be a problem with the ath9k wireless driver. By installing backportmodules and a replacement for Network Manager I can now ping and connect as expected. The time will tell if this is a sustainable solution. 

The following packages was installed (I found the solution in this thread [http://ubuntuforums.org/showthread.php?t=1137780]("http://ubuntuforums.org/showthread.php?t=1137780")):

1) linux-backports-modules-jaunty
2) wicd

---

