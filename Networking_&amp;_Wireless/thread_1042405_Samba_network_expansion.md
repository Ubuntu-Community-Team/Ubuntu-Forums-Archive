---
title: "Samba network expansion"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by Cornbreadly on 2009-01-17
I am looking for frugal tips on expanding my network.  I have a samba network setup and I want to expand to include more ethernet connected devices than my router has room for. 

If I get a switch, will everything be assigned their own IPs on the network to allow for shared folders?  Or should I get a network bridge?  Can a single RJ45 cable be split?  I only need to connect 5 cables and my router has room for 4.

If you question why, I am starting to play around with turning the old xboxs into media centers.

---

### Post by b747pete on 2009-01-17
I have used a network switch connected from one port on the router to a LAN )not the WAN) port and then the new devices connected to any of the remaining LAN ports.

I got one for $15 at Office Depot, it was a D-Link DES-1108.

Good luck

---

### Post by Macchi on 2009-01-17
If I understand correctly what you are trying to achieve, then you will need a [HUB (see link)]("http://en.wikipedia.org/wiki/Network_hub") or a [SWITCH (see link)]("http://en.wikipedia.org/wiki/Network_switch"), in order to increase the number of physical ports on your existing communications equipment.

If you have automatic assignment of IP addresses ([called DHCP (see link)]("http://en.wikipedia.org/wiki/Dhcp")) then you simply have to connect the cable and it will work. Normally the range of IP addresses allowed far exceeds the number of ports in the equipment.


This will certaily not affect access to your Samba shares. You can test individual pieces of equipment separately even before you can connect them together at the same time. 

Keep in touch if you need more help.

By the way:
A [network bridge (see link)]("http://en.wikipedia.org/wiki/Network_bridge") is a different thing, it connects two different networks or could (can) be used to connect networks that use different protocols.

---

### Post by Cornbreadly on 2009-01-17
I see.  If my gateway ip to the router is 192.168.0.1 and the four ethernet cables attached to it now are static ips at 192.168.0.11-14, adding other cables through a swtich behind the router will just increase that capability.  Meaning I can add 192.168.0.15 by taking out one of the RJ45 cables now connected and connect it to the switch with my expansion RJ45 cable, and running one RJ45 from the switch to the router.

For samba, I just add any IPs that want to let access shares.  

Did I pick up what you guys are laying down?

---

