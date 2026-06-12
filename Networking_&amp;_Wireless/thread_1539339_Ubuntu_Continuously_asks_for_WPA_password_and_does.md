---
title: "Ubuntu Continuously asks for WPA password and doesn't connect"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by watsyurname529 on 2010-07-26
Okay, I've searched the internet far and wide and tried almost every fix I can think of. Maybe you guys know one I don't so here's my shot at the forums.

I'm running Ubuntu 10.04 on an old Dell that I'm going to use a MAME machine. I've tried connecting to the internet with three different adapters. One works perfectly (Netgear WN111 USB), problem is that's for my main computer. The other two that I can use for the machine come up with the same problem.

Using a Netgear WG311v3 PCI and a Netgear WG111t USB adapter, I can get the system to recognize both using ndiswrapper and the proper drivers, see my home network, and try to connect using the WPA-PSK passcode. Once I put in the password, it tries to connect and eventually asks for it again, even though the password is auto entered as I originally typed, I hit connect and then it repeats the cycle endlessly and will never actually connect to the network and internet.

Both adapters should be properly configured, as lshw -C Network lists both adapters using their proper ndiswrapper drivers and that both are found and working. I've blacklisted the bcm43xx, b43, b43legacy, and ssb drivers. I've installed wpa_supplicant, however I have yet to try and edit that. I've cleared out the .gnome2 keyring folder and restarted and that doesn't work.

So, I turn to all of you for help. If you have any further questions or need system readouts, I will give them to you asap.

---

