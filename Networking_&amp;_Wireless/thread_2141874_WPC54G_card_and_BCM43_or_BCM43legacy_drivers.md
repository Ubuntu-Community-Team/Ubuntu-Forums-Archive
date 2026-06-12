---
title: "WPC54G card and BCM43 or BCM43legacy drivers"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by romain.astie on 2013-05-04
Hey all,

I have a fairly old system that now runs lubuntu, and have a WPC54G Linksys PCI card I want to use for a wireless card. I have gotten it to work in the past; however, it was using ndiswrapper, and I never got a good or fast connection, and ndiswrapper bogged down my system a little bit (it's already extremely minimal). The card is based on the Broadcom BCM43 chipset family, so I wonder why the drivers included with ubuntu never worked. Is there any way to make the card work without using ndiswrapper, using the BCM43 or BCM43legacy drivers, already included by default with ubuntu,  instead?

---

### Post by romain.astie on 2013-05-04
Solved the problem. I looked up the BCM4306 chipset, and successfully installed the correct driver package as per the instruction here : [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)
Before that, I checked which driver to install with the instructions here : [http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices](http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices)

Moderator, how to I change the prefix to [solved]?

---

### Post by Hadaka on 2013-05-04
Hi, follow this link to mark solved..
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks

---

