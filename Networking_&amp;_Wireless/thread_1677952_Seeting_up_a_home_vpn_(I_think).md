---
title: "Seeting up a home vpn (I think)"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by Lifebandit on 2011-01-29
Hey guys, I am new to Ubuntu and to Linux period, I have Ubuntu 10.10 and love it. I have 2 kids that are wanting their own computers in their rooms and I want to put Ubuntu 10.10 on them. 

What I want to do is, instead of putting the full Ubuntu OS on their computers and having to manage the parental controls on each, I am wanting to make a server that has the Full OS with both of their accounts and have them log into that server to access their desktop from a small client Ubuntu OS from their computers. 

What software do I need and how do I need to configure it?

Thanks in advance.



Edit: My home network hardware setup consists of a cable modem that is connected to a 8 port hub that all computers in house will connect to.

---

### Post by Lifebandit on 2011-01-30
Ok, I found this page [http://linux4dummies.wordpress.com/2007/06/29/ubuntu-ltsp-server/](http://linux4dummies.wordpress.com/2007/06/29/ubuntu-ltsp-server/) and followed the instructions up untill it told me to go to rom-o-matic.com. That site is down so I can't download the client boot disks. But since installing the lstp server, I can no longer access the internet from that server. Is that supposed to happen or is it a setting somewhere?

---

### Post by gottr on 2011-02-10
Here are some 64bit 10.10 instructions.  Additionally to this you might need to configure your network.

#LTSP 64bit server install

1. Used Ubuntu Alternate CD 10.10 64bit
2. Configured VMware server with 2 NICs and adjusted RAM and Processors
3. Booted VMware server to the ubuntu .iso file
4. Press F4 upon boot and choose install LTSP server
5. Follow guided installation
####6. After server is installed you should be able to boot thin client
7. Must be on same network segment
8. 2 nics are used becuase 1 nic gives network access the other assigns dchp addresses to thin clients
9. Build 32-bit image: sudo ltsp-build-client --arch i386
10. Edit the /etc/ltsp/dhcpd.conf to add the i386 directory instead of amd
11A. Restart dhcp: /etc/init.d/dhcp3-server restart

---

