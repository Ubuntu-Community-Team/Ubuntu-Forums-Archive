---
title: "Jerky video with nVidia 7050PV on Abit AN-M2HD"
date: 2008-05-14
forum: Multimedia Software
---

### Post by colinjones on 2008-05-14
Really hoping someone can help on this one, been trying to fix it for months!

Have an Abit AN-M2HD mobo which has the 630a/7050PV chipset. AMD 5200+ and 2GB RAM. Running Kubuntu 0710 - it is actually LinuxMCE media player.

All video media (HDMI out to TV) is jerky with motion (zoom, pan, etc) Not hugely jerky but very noticable on things like TV (esp. tickers scrolling). It is pretty erratic/random but seems to jerk between once and 4 times per second. 

I happens with all sources - so media files on the local HDD or over network and with video from my DVB-T tuner card for TV. EVEN with the LinuxMCE screen saver where it pans and zooms still jpgs! (this is not the same as the KDE screen saver). 

The behaviour is the same in KDE desktop as actually in LinuxMCE the application. I have installed the latest nVidia driver (169.12) and the latest BIOS for the mobo (19). 

Endlessly tweaked the xorg.conf file and looked for telltale messages in xorg.0.log, but I really don't know what I'm looking for!

I did have a problem with tearing as well, but that is pretty much gone (probably a driver update, or using nvidia-settings to set the Vblank/Vsync options) anyway that seems gone now, its just jerky and nothing I do seems to make any difference.

Watching top seems to indicate that I am not topping out CPU - often less than 20% with video and less for the screensaver. But I have no idea how to tell if the hardware acceleration is being used at all - I would have assumed that CPU would be high if it wasn't, but others think otherwise...

Can anybody give me some pointers, please, on what else I can do to resolve this? The 7050PV should have enough grunt at least for the screensaver to be smooth!! And I know of other people that have gotten this mobo working without jerkiness, but we don't seem to be able to identify what is different....

Getting desparate :) any help would be greatly appreciated....

Col

---

