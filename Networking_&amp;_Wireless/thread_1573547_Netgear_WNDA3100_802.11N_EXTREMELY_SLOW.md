---
title: "Netgear WNDA3100 802.11N EXTREMELY SLOW"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by matt531320 on 2010-09-12
My wifi dongle is only willing to connect to my wireless G router (not my 802.11N router) and refuses to go beyond 20KB/s. I tried installing the drivers via ndiswrapper and it installed fine, but nothing changed. Any ideas?

---

### Post by MaindotC on 2010-09-12
Please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and let us know if you have any difficulty and precisely where so we can better help you.  It sounds like a driver issue but the guide will provide more insight.

---

### Post by matt531320 on 2010-09-12
I went through that (the whole thing) but none of it seemed to help and/or apply to me. Do you have any other ideas? BTW,this dongle works really fast in XP.

---

### Post by MaindotC on 2010-09-12
Try transferring a file or downloading a file to another machine on your network.  Is it still 20 kb/s?  The only other thing I could think of is to try using ndiswrapper but it was in the guide so you obviously already tried it.

---

### Post by matt531320 on 2010-09-12
If you look at my original post, I had already tried ndiswrapper ;). I changed the security of my 802.11G router to WEP (from WPA2) and the speed is slowly inclining. I'll post back again if anything changes, but right now the internet seems to be going at a decent speed. I hope an update will come out that fixes my trouble connecting to wireless N. Thanks though!

---

### Post by MaindotC on 2010-09-12
I re-suggest you try transferring files between two machines on the network and seeing if you get similar speeds.  If the transfer is faster - like at least 2mb/s - then I would propose it's a problem with your service provider.

---

### Post by zoundwave on 2010-09-20
The trouble probably is that your system is still trying to use the native "ar9170usb" driver which only seems to support up through Wireless-G. 

I too have been lamenting the incredibly poor network connectivity with this driver and have been trying my hardest to get ndiswrapper to work to no avail, seemingly because the driver package for Windows is actually designed to support a couple different implementations of the Atheros 9170 chipset that the WNDA3100v1 is built on.
Because of this, ndiswrapper actually fails to load the driver because 'too many sys files' are installed and somehow 'couldn't load the driver.'
Deleting the extraneous sys files got rid of the former error, "loadndisdriver: loadndisdriver: load_driver(325): too many .sys files for driver arusb_win7x", but the latter keeps getting thrown: "loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver arusb_win7x"
:(

In my searches, it sounded like the "otus" driver on which "ar9170usb" is based has the Wireless-N support we seek, but I can't figure out where one might acquire it.

---

