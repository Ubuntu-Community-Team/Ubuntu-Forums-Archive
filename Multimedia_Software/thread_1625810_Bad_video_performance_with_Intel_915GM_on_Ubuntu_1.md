---
title: "Bad video performance with Intel 915GM on Ubuntu 10.10"
date: 2010-11-19
forum: Multimedia Software
---

### Post by fsallstrom on 2010-11-19
Hi
I recently installed Ubuntu 10.10 on my Aopen "Mini" to use as my TV entertainment system. My TV is a Samsung LCD LE40F7 with full HD resolution. 

At the beginning I could only get a very low resolution (no high-res options were available from the monitor settings. I manage to solve that by manually entering a modeline setting through xrandr. I made the config persistent by adding it to /etc/gdm/Init/Default

The modeline Im using is for 1920x1080 60Hz.

However, when watching DVDs (or any other video format) I get a very bad performance. I have tried different media players, including VLC and gnome media player with all bad results. If I go to full-screen mode the media player allocates 100% CPU and finally I have to reboot. In window mode, the movie flickers allot.  

So to the specs: the computer is an Aopen Mini PC with 1 GB of ram, CPU is pentium M 1,86 MHz and the video card is an integrated Intel 915GM chipset (Intel mobile 915GM/GMS/910GML express graphics controller).

I have not installed any proprietary drivers, I assume the latest intel driver is included in Ubuntu 10.10 (kernel is 2.6.35-22-generic). The video driver loaded is "i915"

I have read some posts regarding issues with the 915GM chip but could not find anything that relates to my problem. 

Should my hardware spec being able to handle this resolution at all? I will try to find another modeline setting for my LCD with a lower  resolution (it was not easy to get this one working, so I doubt I will  succeed) to see if that helps.

Any help would be highly appreciated.

//Fred

---

### Post by naviathan on 2010-11-19
1. the i915 doesn't do high res very well.  This is the reason Nvidia put out the ION chipset for the Atom processors.
2. That old Pentium M processor isn't going to handle the video processing that the graphics adapter won't do.
 
Bring it down to a 720p setting and you should see a marked improvement.  Even then though, you're still going to get some chop with flash based video.  Turn off window decorations and remove compiz to save some resources.

---

### Post by fsallstrom on 2010-11-19
Update to my previous post: 

After resetting to lower resolution (1024x768) the problem remains. The CPU does not go above 50%, still the picture is "jerky" when watching movies on VLC or Gnome player.

---

### Post by owain123 on 2010-11-19
I was having the same problem. After I switched the 'Visual Effects' to 'extra', in the Appearance properties, the problem disappeared. I can now watch 720p movies without it lag.

---

