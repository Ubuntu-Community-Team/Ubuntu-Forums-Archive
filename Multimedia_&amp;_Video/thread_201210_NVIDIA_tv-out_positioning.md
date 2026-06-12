---
title: "NVIDIA tv-out positioning"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by RekkaAuto on 2006-06-21
Hi

My tv-out picture is not centered so i was just wondering if there is a way to move tv-out picture horizontaly and verticaly. I'm able to zoom tv-out in and out with TVOverscan option, but i haven't found any way to move picture with nvidia drivers.
In windows tv-out is fully movable so maby there is a way to do it with in linux too.

I have Dapper 6.06 and nvidia lates drivers installed.
Current xorg tv-out configuration looks like this:

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
    Option  	   "NoLogo"        "true"
    Option  "RenderAccel"   "true"
    Option "TwinView" "true"
    Option "TwinViewOrientation" "Clone"
    Option "ConnectedMonitor" "CRT,TV"
    Option "TVOutFormat" "COMPOSITE"
    Option "TVStandard" "PAL-B"
    Option "SecondMonitorHorizSync" "30-50"
    Option "SecondMonitorVertRefresh" "60"
 #Option "MetaModes" "1280x1024,1024x768;1280x960,1024x768;1024x768,1024x768"
    Option "TVOverScan" "0.5"
EndSection

---

### Post by RekkaAuto on 2006-06-23
Any ideas,somenone? ](*,)

---

### Post by tseliot on 2006-06-23
Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")

---

### Post by RekkaAuto on 2006-06-23
Ok I will,thanks.

---

