---
title: "Sonic firewall and Ubuntu Server on VM ware"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by maganda on 2010-01-21
Hi 

Recently I installed a ubuntu server on VMware cluster to be used as tftpserver for Cisco routers actually to apply rancid but network access needs to working at first.
Somehow can't get the tftp working threw the sonic firewall.

Tech details
Ubuntu 9.04
 uname -a
Linux quickeloveit 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Firewall
Sonic Firewall  Model:         PRO 3060 Enhanced
latest firmware Firmware Version:         SonicOS Enhanced 4.0.0.12-64e

Firewall permit ping though don't receive reply on my ubuntu.
yes I did also via sudo same results

Firewall give this logs01/21/2010 16:54:15.432    Info    Network Access    ICMP packet from LAN allowed    10.10.X.X, 18967, X0    213.X.X.58, 8, X1    ICMP Echo, Code: 0     
2    01/21/2010 16:54:04.432    Info    Network Access    ICMP packet from LAN allowed    10.10.X.X, 18967, X0    213.X.X.58, 8, X1    ICMP Echo, Code: 0     
3    01/21/2010 16:53:14.304    Info    Network Access    ICMP packet from LAN allowed    10.10.X.X, 18711, X0    213.X.X.58, 8, X1    ICMP Echo, Code: 0


Obviously I missed something 
do much apprecitiate some hints 
I've followed this link 
[http://www.ubuntugeek.com/howto-setup-advanced-tftp-server-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-advanced-tftp-server-in-ubuntu.html)
and applied everything till the test cause that didn't work.........
hence the reason why I'm typing the above info.

note: I was NOT my idea of ordering a Sonic FW :twisted:

---

