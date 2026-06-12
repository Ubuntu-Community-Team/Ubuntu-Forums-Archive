---
title: "events/0 taking up 60-90% CPU, related to wireless driver woes?"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by Niomi on 2006-07-04
The first time I installed Ubuntu on my laptop, the version was Breezy or Hoary, my wifi card was detected and worked immediately. I bragged to friends that while Ubuntu detected my wifi card automatically, I had to download and install a driver to get my wifi card working on windows. Recently I wiped my laptop and set up a dual-boot system, XP on a small partition and Ubuntu to use as my primary OS. But on my recent Dapper install, my wireless internet device, ra0, is not working correctly.

ifup ra0 returns that the device is configured. With some difficulty, I can activate ra0 (the UI claims it's activated, anyway) in gnome-network-manager, but it doesn't appear to detect any wireless networks. It cannot connect to my network if I provide the ESSID.

Occasionally when I'm messing with gnome-network-manager, my keyboard will stop working, and I'll have to restart to use it again. The laptop connects fine with a wired connection into my router, and the wireless card is connecting fine to the network under windows.

Since I've been trying to fix this, process events/0 has been using up my CPU. My laptop battery life is usually around 3hrs, but with this process using my CPU the battery life is around an hour and a half. The PC is very warm and the fan will run constantly.

Doing a google search on events/0 has brought up this description, so I think the two difficulties may be related:

> Finally I have managed to fix the problem. I went into the bios and disabled all of the hardware on my laptop and it worked. I gradually re-enabled things (USB, WLAN, etc) until it happened again...the culprit is my LAN card, which uses the sky2 module.

Please help!

Ubuntu Dapper (upgraded from a previous version) was running fine on my laptop a few days ago and I really miss it. Windows just isn't home for me anymore >_<

---

