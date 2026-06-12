---
title: "Sharing internet wirelessly"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by cshake on 2006-06-03
First off, I just installed ubuntu last night, and I'm quite happy with it! (though my first linux was gentoo a few years ago, I couldn't get it to install this time)

Anyway, I'm living in a dorm, and have one ethernet jack in my room. The network here assigns ips to registered mac addresses, one per user. I can't use a hub or anything to connect both my computers (desktop: WinXP+xubuntu, and laptop: OSX Tiger) because both will be assigned the same ip.

The way I've been getting around this is setting up a ad-hoc wireless network between the two computers, plugging the desktop into the wall, and sharing internet with WinXP.

My problem is that I can't figure out how to set up a p2p wireless network with ubuntu (using xfce4). I can't let it broadcast as an access point, because network people here will come and shut it down.

The wired connection is working fine, I just want to share it.
"Network Tools" only shows lo and eth0 in the device list, but the "Networking" panel shows wlan0 and wifi0 as well, but wifi0 is shown as not configured and wlan0 is not active.
My card is D-Link-DWL-650 RevP-DC64

chris

---

### Post by Jason_25 on 2006-06-03
You may be able to setup your wireless card as an access point depending on the chipset.  Then hide the essid.  Or do you feel they will be able to find an access point despite having the essid hidden?  It is possible with certain tools, but your network admins may not be cunning enough to use them, or be too lazy to bother.  If it's just through one wall, you may be able to turn the transmit power down (again, depending on your card), so it's not noticeable from very far away.

This post shows my experience with ubuntu as an access point.
[http://ubuntuforums.org/showthread.php?t=150842&highlight=pocket+skype](http://ubuntuforums.org/showthread.php?t=150842&highlight=pocket+skype)

edit:
Check out this page.
[http://www.seattlewireless.net/LinuxDrivers](http://www.seattlewireless.net/LinuxDrivers)
Apparently, the hostap driver I was using does support the prism 3 chipset that you have in your revision p dwl-650.

---

### Post by darkshadow on 2006-06-03
I just started playing with a firewall gui called firestarter that gives the option of starting internet connection sharing. It just asks what device is connected to the internet and which is on the lan. The only thing you will have to manully setup is ad-hoc mode using commands like iwconfig and ifconfig.

---

### Post by El_Virdi on 2006-06-11
[QUOTE=darkshadow]I just started playing with a firewall gui called firestarter that gives the option of starting internet connection sharing.[/QUOTE]


Thanks for the tip, mate. I had my internet connection shared with scripts before and this solution is way easyer, works like a dream and traffic monitor is great.

---

