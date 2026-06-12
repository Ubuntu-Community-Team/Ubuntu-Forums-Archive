---
title: "Switched to static IP but could not connect to Internet"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by bclay on 2009-10-25
I am having the same problem as others in this message thead.
 
I have a dual boot system (Ubuntu and Windows XP).  When I first installed Ubunu it defaulted to dynamic address and everything worked fine.  When I switched to Static IP outside users can see my system but no one on my system can see the network.
 
My network provided is AT&T U-Verse and my static IP addresses assigned by GoDaddy are in the range of 99.29.x.x.  Systems inside my intranet that use dynamic IP are using IP's in the range of 192.168.x.x as is the geteway
 
When I boot into Windows XP everything seems to work ok but not when in Ubuntu.
 
If I add my gateway address (in the 192.168.x.x) to the /etc/network/interface file then execute ifdown the if up I get an error message "SIOCADDRT No such process Faile to bring up etho".
 
To add even more confusion to the mess my name server is on 4.2.2.1.
 
I realize it is not normal to have different addresses within the same net but these are the addresses I was given.
 
Bruce

---

### Post by Iowan on 2009-10-25
What is in */etc/network/interfaces*?
Have you tried configuring manual (static) address vis Network Manager?

---

