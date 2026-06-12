---
title: "second monitor in FULL HD res. problem"
date: 2009-10-07
forum: Multimedia Software
---

### Post by argento81 on 2009-10-07
Hi,

I have instaled Ubuntu on my laptop ASUS A6Rp 
graphic: Xpress 200 

connected LCD LG TV 32'' (FULL HD) via VGA

and unable to switch this LCD to FULL HD 1920x1080 resolution, when I adjust resolution to full HD, lcd will turn off (NO SIGNAL) problem is maybe in frequency (60hz) I had this problem  on windows and solve it downgrade frequency to 56 ?? maybe .. cant remember..

this is my xorg.conf after install :

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 3200 1080
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection
```please help how to adjust screen resolution of LCD to 1920x1080

thank you

---

