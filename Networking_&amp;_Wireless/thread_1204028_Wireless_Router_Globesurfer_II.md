---
title: "Wireless Router Globesurfer II"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by gesy on 2009-07-04
Hi,
I have a GlobeSurfer II Wireless Router. Everything works fine but forwarding or triggering to open some ports. The version of the router is:

Version:	R2D03
Distribution:	GS2P_72
Release date:	Nov 13 2008
Platform:	Broadcom 5352 - GS2
Modem firmware version:	2.5.17AHd
Hardware version:	3.0
Hardware serial number:	G33787P81D
IMSI:	425020356069208
IMEI:	352375016002610

Has somebody already solved this problem and how ?  

Is it possible to use this router only as a modem and route with an other router more easy to configure ?

Has somebody a good experience with an other wireless modem or router of this class (the globesurfer use SIM Card to link to the internet) to remplace the one I own ?

Thanks.

---

### Post by superprash2003 on 2009-07-04
have you tried opening ports? do you use firestarter or gufw? [www.portforward.com](www.portforward.com) has some good guides on opening ports..

---

### Post by gesy on 2009-07-04
thanks for the answer. I use Firestarter and opened the ports. Even if I stop the firewall, the problem persist: the router doesn't seem to react to forwarding ou triggering ports. I readed that I'm not the only one with the same problem.

---

### Post by superprash2003 on 2009-07-06
post output of **sudo iptables -**L when firestarter is on and off

---

### Post by gesy on 2009-07-08
I found a solution that I wrote for those wich have the same problem.
I think the problem is the router that isn't able to manage enough ports.
So, I did like this and it works:

Enter in Portforwarding's tab (Connection settings -> Security -> Portforwarding) and write a new enter (or corrige the one in use) with these parameters (let's say that you want forward for eMule):

local host: your computer's IP (192.168.1.xxx)
Protocol: "user defined"
Server Port:  TCP
Source Ports: Any
Destination ports: Single - 4662 (for example)
OK
Forward to Port: "Same as incoming port"
Schedule:  "Always"
OK
Apply
OK

Do the same for: 
 - Server Port: UDP
 - Destination ports: Single - 4665

Make the firewall compatible

Desactivate UPnP in eMule

and it's all (don't trigger the ports !).

Thanks for your answers.

---

