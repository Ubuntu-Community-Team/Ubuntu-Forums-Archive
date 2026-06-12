---
title: "Atheros wireless card not detected by dmesg"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by MisterInteger on 2009-08-24
I made the switch to Ubuntu a couple months ago, and initially had some WiFi issues. I ended up installing the madwifi drivers, and also the backports-modules package for Jaunty. So my wireless was working until today.
I think what caused the problem was an update, or something. I logged in, and found that my wifi wasn't working. Ethernet is working, or I wouldn't be posting this, but my wireless card is totally ineffective.

The first thing that came to mind was a problem with the driver, so I checked to see if the madwifi driver was still functioning/activated after the update. It wasn't even installed! So I reinstalled the latest version, but am still having the same issue, of the wireless card recognizing various (WPA and WPA2) networks but having difficulty connecting.

Obviously I've been looking all over for a fix, but in every thread I come across, someone is asking for the output of the dmesg command, which I of course ran. I get a longlonglong series of messages (enough to fill up the bash shell completely, to the point where I can no longer see the command as entered anymore) saying "wlan0: direct probe to AP f61016b8 timed out"

Does anyone have any advice for me? All help is deeply appreciated. And if you could keep technical responses to a level where a relative noob can understand, that would be awesome. :)

---

