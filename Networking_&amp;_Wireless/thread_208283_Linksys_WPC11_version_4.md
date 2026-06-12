---
title: "Linksys WPC11 version 4"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by iamdigitalman on 2006-07-03
ok, figured I would make a new topic, as nobody is reading my old one, and this is wothy of a new topic.

a couple weeks back, I returned a belkin USB wifi stick that wasnt working. I was told by people on here that a linksys WPC11 would work, as it has a realtech chipset, and it's fully supported. so, I got it, installed it, and it appeared to be working. green light for power, when the system was starting up, I got lines of text marking that the card was installed and the driver initialized. upon boot, I was happy to see a wonderful wireless card entry in the networking panel, and it was showing up as wlan0. then, I was saddened to see that I was not able to connect. I rana few diagnostics, and according to one of the commands in the terminal, it is not broadcasting it's own IP address. I think this is needed to connect, as both my eth0 and l0 (loopback) were broadcasting thier IPs. wierd.

I have tried everything under the sun to get this stupid thing to work, from unplugging and reinserting the card, to disabling the eth0 connection. nothing works.

so, is there a way for the card to force it's IP? I cant even ping the stupid thing, and thus, I cant ping the router.

also, how do I get it to work with WPA-PSK TKIP? I see the networking control panel has support for WEP encryption, but what about WPA? 

oh, one thing that might swing the vote is that I am on a mac. so, everything might be truly plug and play with this card, but only on x86, but I doubt that. the PPC ubuntu is just a direct port, right?

specs:

Powerbook Wallstreet 1998
PowerPC 740 G3@ 233mhz.
160mb of physical ram, 256mb swap space
4.9gb hard drive, 4.4gb formatted.
20x CD-ROM (busted, had to load Ubuntu from my B&W G3 in a HDD adapter)
2x PCMCIA, 1x VGA, 1x S-Video, 1x SCSI, 1x Serial  1X ADB
Ubuntu 6.06 with all updates installed, 2.6.15-23-powerpc kernel.

thank you.

-digital ;)

---

### Post by iamdigitalman on 2006-07-08
well, I reinstalled dapper, except I loaded breezy on it first, then upgraded. odd that after the upgrade, kernel was still 2.6.12-9. so, I went to symantic, and grabbed 2.6.15-25.43, the latest and gratest, and it STILL doesnt work. same as before. looks like it isnt broadcasting the IP, but at bootup, with the splash turned off, I can see a bunch of WW text, so it IS loading the driver, but not broadcasting the IP. I have tried every encryption: none, WEP-open, WEP-restricted AND WPA-PSK TKIP. nothing.

note: I have wifi-radar, and kwifimanager installed, and kwifimanager says no AP found. wifi-radar says connected to <ssid> <ip address> and I can create a new connection, it says aquired IP address, but there is no signal.

perhaps somebody wiht extensive knowlage can help me locally. if anybody is avalible in southeast Michigan United States, send me a PM.

thanks. -digital ;)

---

### Post by iamdigitalman on 2006-07-10
well, after a bi more looking around, turns out my wired ethernet connection on the laptop is eth1...before I reloaded the OS, it was eth0. odd. dunno if this has anything to do with it, but it might help

-digital ;)

---

### Post by iamdigitalman on 2006-07-17
bumpy

---

### Post by Titus A Duxass on 2006-07-17
Configure the wireless card through (I think) Adminstration -> Networking.

Then edit /etc/apt/networking (do a search for an example).

---

