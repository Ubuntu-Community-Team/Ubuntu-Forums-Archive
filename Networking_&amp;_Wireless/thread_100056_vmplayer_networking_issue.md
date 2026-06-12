---
title: "vmplayer networking issue"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by Xappe on 2005-12-06
Hi,

 Installed vmware player yesterday, made a .vmdk image with qemu and installed win2k. I set up vmplayer to bridge the virtual network to my eth1 (my local network gateway) so that I can control the traffic through my existing shorewall NAT (running on the host). 

The problem is now, that the connection from the virtual machine (win2k) to eth1 and the host i VERY slow. Tried to sftp some files to my virtual machine with winscp from the host, and the transfer never reached over 2 kB/s. After a while the connection with the host died. When surfing the web, connections very often time out or the pages load very slow.

The eth1 card is 10Mbit. My internet connection through eth0 is 10/100 LAN.

Any suggestions?

---

