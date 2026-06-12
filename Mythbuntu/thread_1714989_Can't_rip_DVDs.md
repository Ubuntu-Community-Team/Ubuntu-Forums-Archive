---
title: "Can't rip DVDs"
date: 2011-03-26
forum: Mythbuntu
---

### Post by NautiusMaximus on 2011-03-26
This is a continuation of [another thread I started a while back]("http://ubuntuforums.org/showthread.php?t=1682011"). As there's quite a few replies there and I still haven't found a resolution, I thought it might be useful to summarise everything and start again.

I can't rip DVDs from my Mythbuntu system. I understand that this feature has been removed from recent releases, but I'm using Mythbuntu 10.04 with MythTV 0.23.1, which I understand should in theory still be able to rip them.

I can play DVDs, and I can browse the contents of the DVD from the Unbuntu desktop, so there doesn't seem to be any hardware problem or a problem mounting the drive. I just can't rip them, when I try to using the "Rip DVD" feature from the MythTV frontend. If I choose the "Rip DVD" menu item, I get a screen saying only "No jobs. Checking and/or waiting for DVD".

Here is what my mythfrontend log file was saying at the time I was trying:

```
2011-02-05 10:20:00.251 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2011-02-05 10:20:00.414 Loading menu theme from /usr/share/mythtv/themes/classic//mainmenu.xml
2011-02-05 10:20:00.426 Found mainmenu.xml for theme 'Mythbuntu'
2011-02-05 10:20:02.133 MythContext: Connecting to backend server: 172.16.100.20:6543 (try 1 of 1)
2011-02-05 10:20:02.133 Using protocol version 56
2011-02-05 10:20:02.316 'nice /usr/share/mythtv/mythweather/scripts/no_yrno/yrnoxml.pl -u SI -d /home/adam/.mythtv/MythWeather/yrno-XML United_Kingdom/England/Mitcham' has exited
2011-02-05 10:20:19.573 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2011-02-05 10:20:19.620 Loading menu theme from /usr/share/mythtv/videomenu.xml
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
2011-02-05 10:20:30.289 Failed to mount /dev/sdc.
2011-02-05 10:20:42.424 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/dvd-ui.xml
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
2011-02-05 10:21:00.322 Failed to mount /dev/sdd.
mount: can't find /dev/sde in /etc/fstab or /etc/mtab
2011-02-05 10:21:30.362 Failed to mount /dev/sde.
mount: can't find /dev/sdf in /etc/fstab or /etc/mtab
2011-02-05 10:22:00.402 Failed to mount /dev/sdf.
2011-02-05 10:22:22.912 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2011-02-05 10:22:23.140 MythVideo::ScanVideoDirectory Scanning (/media/disk2/mythtv/videos)
2011-02-05 10:24:05.339 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/dvd-ui.xml
mount: block device /dev/sr0 is write-protected, mounting read-only
2011-02-05 10:24:11.922 Detected MediaType MEDIATYPE_DVD
2011-02-05 10:26:16.595 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit
```

Any idea what the problem could be?

---

### Post by nickrout on 2011-03-26
which device do you have set as the dvd? It's in video player settins I think.

---

### Post by NautiusMaximus on 2011-03-27
I'm not 100% sure I understand what you mean by that question, but if I go to Setup / Videos Settings / Player Settings, then (among other things) I have DVD Player set as "Internal" and DVD Drive set as "/media/cdrom"

Is that what you meant?

---

### Post by nickrout on 2011-03-27
I believe that the DVD device should be set to a device, not a mount point. eg /dev/dvd or whereever your dvd appears under /dev

---

### Post by NautiusMaximus on 2011-04-03
Brilliant! That was indeed what the problem was. I changed that setting from "/media/cdrom" to "/dev/dvd", then then it just worked.

Thanks so much!

NM

---

### Post by calicommando on 2011-04-23
I'm having this same issue in 10.10.  I can't find where in Myth you make the correction.

Edit:  I found the setting, but it's already set to /dev/dvd.  Any other ideas?

---

### Post by klc5555 on 2011-04-23
> **calicommando said:**
> I'm having this same issue in 10.10.  I can't find where in Myth you make the correction.

Edit:  I found the setting, but it's already set to /dev/dvd.  Any other ideas?

Usually the OS will have symlimked /dev/dvd to /dev/sr0 at installation, but not always. So sometimes the DVD drive will spring to life in mythfrontend if you set this device to /dev/sr0 rather than /dev/dvd (or /media/cdrom, etc.)

---

