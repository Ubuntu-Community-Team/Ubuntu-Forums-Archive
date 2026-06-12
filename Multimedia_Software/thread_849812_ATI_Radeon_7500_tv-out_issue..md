---
title: "ATI Radeon 7500 tv-out issue."
date: 2008-07-04
forum: Multimedia Software
---

### Post by Hayesio on 2008-07-04
Hi everyone,

I have setup a Mythbuntu box on an old Dell GX269.  The machine has a ATI Radeon 7500 VGA card with tv-out (S-video).  I'm using the "Radeon" driver and it seems to work fine.  I want the machine to only use the tv as its display - no monitor!

Currently I have to type in the terminal:
```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xrandr --output S-video --set tv_standard pal
```
to make the s-video work.

Is there some way i can edit the xorg.conf file to only use the s-video as display and to do this automatically so i can take the monitor away?

---

### Post by Hayesio on 2008-07-07
Ok, I fixed my own problem.

To get the S-video to work on boot-up and without the VGA, I added this to my xorg.conf file:
```
Section "Device"
        Identifier      "ATI 7500"
        Driver          "radeon"
        Option "ForceTVOut" "true"
        Option "TVStandard" "pal"
EndSection

Section "Monitor"
        Identifier      "S-Video"
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI 7500"
        Monitor         "S-Video"
EndSection
```

I removed the VGA monitor settings altogether.:)

---

