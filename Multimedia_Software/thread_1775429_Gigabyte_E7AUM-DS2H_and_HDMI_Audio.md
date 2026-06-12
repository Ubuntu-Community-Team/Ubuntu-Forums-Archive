---
title: "Gigabyte E7AUM-DS2H and HDMI Audio"
date: 2011-06-04
forum: Multimedia Software
---

### Post by drumz on 2011-06-04
I just updated from 10.10 to 11.04 by doing a clean install and now my audio over HDMI isn't working.  I've verified in the BIOS that the on board audio is 'disabled' so the S/PDIF interface is disabled *but* when I run alsamixer that's the only thing that shows up.

I use this box exclusively as a MythTV frontend, and in MythTV under the setup area it gives me the following options after I 'Scan for audio devices':

Null
ALSA:dmix:CARD=Nvidia,DEV=3
ALSA:hdmi:CARD=NVidia,DEV=0
ALSA:hw:CARD=NVidia,DEV=3
ALSA:plughw:CARD-NVidia,DEV=3

None of them result in sound over HDMI.  It worked fine under 10.10 (and earlier).  The primary reason I did a clean install is because after performing an upgrade the system froze at the 'Mythbuntu' screen and I couldn't get any information out of it as to why.

---

### Post by drumz on 2011-06-05
Ok, after following various posts in regard to doing various things I made no headway.  But one thing that kept bothering me is that even though I did a complete fresh install, I had two Nvidia drivers installed but only the older one was being used.

I tried updating to the newer version of the driver using mythbuntu-control-center, but after rebooting I was experiencing the same thing as when I did the upgrade - the system would boot up until the Mythbuntu log would appear and then it would hang.  So I had to back down to the older 173.x version.

So today I tried updating to the latest Nvidia driver again using mythbuntu-control-center, rebooted expecting it to hang - and it didn't.  Expecting that it really hadn't upgraded it I 'cat /proc/driver/nvidia/version' and it was the new one.  And now audio over HDMI is working again - but I also haven't removed the .asoundrc in my home directory that I had placed there based on other threads so I do not know if that is contributing to it working along with the udpated Nvidia driver or not.

---

