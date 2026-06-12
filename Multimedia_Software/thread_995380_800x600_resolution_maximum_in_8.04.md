---
title: "800x600 resolution maximum in 8.04"
date: 2008-11-27
forum: Multimedia Software
---

### Post by Kerrigans_Zerg on 2008-11-27
I finally got an installation of Ubuntu to work with WPA wireless, but now my video is all messed up. I have an Nvidia Geforce 7300 LE and a monitor with a native resolution of 1600x1080. But for some reason, no matter what I do, the maximum resolution that I can get is 800x600, so everything is all out of proportion. I checked online earlier and ran 
sudo apt-get install nvidia-glx
and
sudo nvidia-xconfig --add-argb-glx-visuals --composite 
based on what I found. But it didn't seem to change anything. Please help!
Oh, also,  wasn't entirely sure where to post this. So if this is the wrong area, please let me know.

*
Ok, I fixed the resolution problem using gksu displayconfig-gtk to change the monitor type. But there's still a problem. The screen is set to LCD 1600x1050, which is correct. the resolution is set to 1280x1024 which is fine, but even with the restricted nvidia drivers enabled, there are bars of my monitor on either side of the display about 2.5 inches wide each where there's no display. How do I fix this?

---

### Post by m_l17 on 2008-11-27
Give this a try:

[http://ubuntuforums.org/showthread.php?t=975058]("http://ubuntuforums.org/showthread.php?t=975058")

---

