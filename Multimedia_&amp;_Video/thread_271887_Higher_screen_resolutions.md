---
title: "Higher screen resolutions?"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by CostasX2 on 2006-10-05
Hi,

I recently installed Dapper Drake on an older machine I had but I can't set the screen in higher resolution than 1024x768. When I go to the screen resolution preferences I only get three options: 1024x768, 800x600, 640x480.

I have an old Asus V7100 Pro SE (nVidia GeForce 2 MX-400) graphics card, AMD Sempron 2600+ (s754, 1600 MHz), 512 MB DDR RAM (one module), Chaintech Zenith Value Edition VNF3-250 (nForce 3), and an EIZO FlexScan L551 17" (LCD-TFT) monitor (shared - through a KVM switch - with a newer machine).

I downloaded and installed the nvidia-glx package from the official ubuntu repository and enabled it.

How can I change the resolution from 1024x768 to 1280x1024 (or higher)?

Just doing my first (deeper) steps into the Linux world so any help will do.

Thank you.

---

### Post by kkm1978 on 2006-10-05
This is what I did and it works for me.

Edited /etc/X11/xorg.conf

Modified thsi section to include **1280x1024**

> Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
        Monitor         "SyncMaster"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Restart X

---

### Post by CostasX2 on 2006-10-05
As I originally suspected but didn't want to risk it...

Thank you, it worked fine - in gnome!

---

