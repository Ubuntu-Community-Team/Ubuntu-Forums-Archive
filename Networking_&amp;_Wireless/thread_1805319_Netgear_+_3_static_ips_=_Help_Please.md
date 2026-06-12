---
title: "Netgear + 3 static ips = Help Please"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by chaos_efphect on 2011-07-15
First off not sure if this is the right area or if any of your guys could help, but since this forum rocks so much i though i would give it a try.

Well first thing, there is going only going to be 2 computers and the netgear on this network that's it no other computers clients or anything else. The way the system was set up before was from the ISP we have 3 static ips (over kill i know), so each device had its own static ip.
MDM--------------Netgear Router---- PC1/PC2
Bridged-----------Static Ip 1-----------Static ip 2/3

My main issue is at this point finding a way to disable NAT/DHCP in this router and in short making it in to a switch or set it so the 2 computers will work with the other 2 Static ips from my isp.

---

### Post by jmoorse on 2011-07-16
I am sure we can figure something out, but first I want to understand what you are trying to accomplish.

Why do you want to give the PCs public static IPs?

---

### Post by chaos_efphect on 2011-07-26
Thank you for the response, in a nut shell that is how the network was set up when i got there and what the owner wishes. 1 of the pcs is a fax server and the other is a web server.

---

### Post by idlemind324 on 2011-07-26
Chaos you don't have AT&T U-Verse do you?

---

### Post by newbie-user on 2011-07-27
Turn off the router's DHCP server first, then plug the modem into one of the LAN ports of the router.  Then you can assign the two computers the proper static IP addresses.  Basically, you'd be deactivating the router functionality of the Netgear and making it into a switch.

---

### Post by chaos_efphect on 2011-07-30
Thank you everyone for your responses, newbie-user going to try that as soon as i get home. idlemind324 i in fact do not have  AT&T U-Verse, this set up is being ran at a hosting company.

---

