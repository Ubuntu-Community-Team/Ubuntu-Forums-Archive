---
title: "PPTP VPN connection stopped working"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by toscal on 2010-10-06
I managed to set up a PPTP VPN connection in Ubuntu 10.04, and it worked first time.This was about 3 months ago. It was working yesterday (Oct 05 2010), but when I came to log in to the VPN today it doesn't work. 
 I tried the same VPN connection on my wife's laptop which runs Vista and it works. 
I have tried re-entering the details, even deleting and setting up from scratch via network manager. And yes I have the correct VPN plugins. 
So any ideas as what I should do. Is there a log file so I can have a look at it to see what the problem is. If there is where is it located. 
 The computer is able to connect to the internet without any problems, just can't connect to the VPN.
 The only thing I can think of is that the update manager popped up this morning so a few things have got updated today. maybe something in there broke the VPN connection.

---

### Post by toscal on 2010-10-06
Its working again. 
does any one remember the music to the twilight zone. 
I blame sun spots actually. :roll:

---

### Post by mgt2000 on 2011-09-03
I have the same problem with Ubuntu 11.04 and the connection worked fine one or two times but after that it stopped working. Even I reinstalled the system two times but it is the same. I have reinstall all plug-ins ... but nothing has been changed. I can not connect to any kind of VPN connections like pptp and Cisco or OpenVPN.

---

### Post by praseodym on 2011-09-03
Hi mgt2000,

try to reinstall _all_ components that start with "network-manager" you already have installed. Does your VPN-server use LZO compression? If so, you have to activate in the NM applet (somewhere in "Advanced").

---

### Post by mgt2000 on 2011-09-03
thank you praseodym for your reply.
I could finally find the problem. I removed _**Firestarter**_ which is a firewall and now I can connect to all my VPN connections again. Of course I still don't know what was exactly the problem and why Couldn't I use my VPNs with this firewall.

---

