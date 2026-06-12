---
title: "setting up network and internet"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by fr0styfr0st on 2010-07-26
I have Ubuntu 10.4 on my desktop PC 
it is connected to a router with other computers on the network.
I would like  some help setup my connection to see the other computers(all running XP)
and i would like help setting getting it running on the internet etc.
it is connected with an Ethernet cable.

Thanks for the time greatly appreciated
Fr0styfr0st

---

### Post by P4man on 2010-07-26
You shouldnt have to do anything to get it on the internet; provided your router is connected to the internet (and set to assign IP addresses using DHCP; which is the default for any router ive seen). 

To share files and folders ought to be rather self explanatory as well (places > network > browse your network),  however I suspect perhaps your network connection is not working? If you right click the network manager icon (top right) and click on "connection information"; do you have an active network connection with IP address and everything?

---

### Post by martinez6341 on 2010-07-26
i had the same problem, try this it should work. Unplug your ethernet connections, then unplug your router for a full minute ,then plug it back, make shore you wait until the router is fully operational, then once you have all the lights you need start plugging in your ethernet connections. What you are doing is reseting you ISP signal. Hope it works

---

### Post by Goolie on 2010-07-26
Try out Samba for setting up sharing with the XP computers.

---

### Post by Iowan on 2010-07-26
From a terminal (Applications->Accessories->Terminal) check **ifconfig -a** (post if possible) to verify interface has an IP address.

---

