---
title: "Linksys WMP54G not connecting to wireless"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by dpatel304 on 2010-11-12
I've just installed Ubuntu 10.10 and everything seems to be working fine, but I can't seem to connect to my wireless network.  I am able to see the wireless networks nearby, so I'm guessing that means the drivers are fine and the hardware is working.

When I try to connect, I am seeing the wireless networks of my neighbors, but mine isn't showing.  So I manually enter the information in and try to connect, but it doesn't seem to connect.  I enter the WEP key and it attempts, then the WEP key screen pops up again, as if I entered the key incorrectly.  I've tried many times and I'm 100% certain my key is correct, so I'm just wondering if there are any settings I need to change or something else I'm missing.

By the way, the chipset is: Ralink RT61 

Which means it really should just work out of the box.

---

### Post by dpatel304 on 2010-11-12
Any help would be greatly appreciated.

---

### Post by dpatel304 on 2010-11-12
Sorry to bump again, but I've not got my PC connected directly into my router (via ethernet) and it connected instantly.  I'm literally right next to the router, and still unable to connect, so I don't think it's a problem with being too far or too much interference to connect to the router.

Even though the internet is working on there now, I need to be able to connect wirelessly, as the desktop will be too far away for a wired connection.

---

### Post by heavy metal on 2010-11-14
Did you check if the router wireless signal is working, because sometime ago I had a router who connected my computer via cable to internet but when I wanted to use a wifi card I noticed the wireless signal from the router wasn't working, so I had to get another router...

---

### Post by dpatel304 on 2010-11-15
> **heavy metal said:**
> Did you check if the router wireless signal is working, because sometime ago I had a router who connected my computer via cable to internet but when I wanted to use a wifi card I noticed the wireless signal from the router wasn't working, so I had to get another router...

It's definitely working.  I've got 1 other desktop and 2 other laptops all receiving a great signal from the same router.  It shouldn't make a difference, but those are all windows machines.. but that just tells me that some settings or drivers need adjusting on my ubuntu box.

---

### Post by grahammechanical on 2010-11-15
Here is a link to the trouble shooting guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections)

Try the command sudo iwconfig. First disconnect the ethernet cable. If it shows Access point: not associated. It is because you are not connected to the router by wireless. If it shows Connected and the ESSID is that of your network connection, then you are connected.

When connected by ethernet, type sudo ifconfig. You can get enough information from the listing of eth0 or eth1 (whichever is connected) to make sure you have the right information for your wireless connection.

I cannot understand why you can see other wireless networks as available but not your own. 

Regards.

---

