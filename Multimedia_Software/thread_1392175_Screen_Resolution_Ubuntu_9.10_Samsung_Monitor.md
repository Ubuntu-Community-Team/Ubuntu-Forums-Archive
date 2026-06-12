---
title: "Screen Resolution Ubuntu 9.10 Samsung Monitor"
date: 2010-01-27
forum: Multimedia Software
---

### Post by maxpulse on 2010-01-27
Hello
I am running Ubuntu 9.10 on a new HP PC (Pavilion p6240f PC).
This came with an Intel GMX X4500 Integrated graphics.

My monitor is Samsung SyncMaster 2333.

Initially I got a very bad resolution, Later I edited /etc/X11/xorg.conf (created the file) and added the following.(This was suggested in the forums)

Section "Monitor"
Identifier "Generic Monitor"
HorizSync 30 - 75
VertRefresh	56 - 61
EndSection


Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor	 "Generic Monitor"
DefaultDepth	24
SubSection "Display"
Depth 24
Modes "1920x1080" "1600x1200" "1280x1024"
EndSubSection
EndSection 

After reboot In the Display Preferences I get
1600 x 1200 (4:3)
1680 x 1080 (16:10 )
.
.
.
640 x 480 (4:3)

With both 1600 x 1200 and 1680 x 1080 I get the resolution but I see lots of shawdowing.(The letters are not crisp)

Do I need to upgrade any driver ?

Please suggest.

~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)



Thanks

---

### Post by akand074 on 2010-01-27
I'm not very sure how to solve this problem but have you already gone to System > Administration > Hardware drivers and installed any restricted proprietary drivers for your system?

---

