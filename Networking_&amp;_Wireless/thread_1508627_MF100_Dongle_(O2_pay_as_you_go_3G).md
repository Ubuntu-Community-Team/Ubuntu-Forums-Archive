---
title: "MF100 Dongle (O2 pay as you go 3G)"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by Upkeep on 2010-06-13
Hi everyone,

Just for fun I've been trying to get an O2 3G dongle (it's an MF100 HSDPA USB Stick) working for internet access when I'm not near a WiFi hotspot.

I'm running Netbook Edition 10.04 on an HP2133 Mini-note netbook and I'm having difficulty getting Network Manager to detect the dongle.

If the dongle is plugged in at startup, it shows as USB ZTE MMC Storage on the "boot from" list.

I have tried with and without usb-modeswitch installed, but it hasn't made any difference.

I have also attempted to turn off the usbdrive option by sending the AT+ZCDRUN=8 command as per this post:

[http://ubuntuforums.org/showthread.php?t=1359410](http://ubuntuforums.org/showthread.php?t=1359410)

Still no joy.

Now, I'm not sure if this next point is relevant, but I'll mention it anyway - whenever I plug in a USB memory stick, I see the following error message:

"DBus error org.gtk.private.remotevolumemonitor.failed an operation is still pending"

The memory stick mounts OK though.

So, to recap - I've turned off usbdrive option, I've tried with and without usb-modeswitch but the dongle is invisible to  Network Manager.  I know the dongle is working as I successfully connected to the internet using it on my Windows XP laptop.

Any top tips on what to try next?

Cheers
Upkeep :confused:

[Update] OK, here's a strange thing.  I also have 10.04 on a Lenovo laptop and hadn't tried fiddling around with it.  Plugging in the dongle it was recognised no problem.  Network Manager on my netbook doesn't offer the option to enable mobile broadband - it's just not there.

Any clues as to what I can do to reset network manager?  I've tried reinstalling the network manager package but it didn't help

---

