---
title: "Use wireless router to connect to wireless AP"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by linuxtorvalds on 2009-04-07
I've searched around, but can't find what I'm looking for.  I think I don't know the correct nomenclature.  Here's what I have (warning, crude ascii diagram).

laptop with internal pcmcia wifi card  --------->   wireless access point.

Which works fine.  What I would like to do is:

laptop --> ethernet cable --> wireless router  -------> wireless access point

The router is a Netgear WGT624.  I do have telnetenable so I can change it from client to bridge to station to AP, but I don't know what to change it too, or what other settings to change.

Laptop is running Intrepid.  I can iwlist eth1 scan and see networks with the pcmcia card in, then connect normally.  I would like to do the same going through eth0 to the router.

Ideas?

---

### Post by wkulecz on 2009-04-07
Assuming the internet is connected through the Wireless Access point, you need to put the wireless router in bridge mode and set to to assign IP addresses in an unused range in the network the AP is part of.

HTH,
--wally.

---

### Post by linuxtorvalds on 2009-04-07
Thanks, I'll try that, I was working as a client with dhcp off...

---

### Post by linuxtorvalds on 2009-04-07
I have partial success, I set the Netgear router to client, turned off the Netgrear LAN DHCP server, then set the essid of the Netgear to the essid of the access point.  The AP will now assign the laptop an IP address.  Plus they both have to be on the same net, 192.168.1.xxx.  Still not networking, but that's probably due to other issues haven't got to yet.  Thanks for your help.

---

