---
title: "new monitor out of range"
date: 2009-10-27
forum: Multimedia Software
---

### Post by md389 on 2009-10-27
Hey everybody, 
   I just installed a new monitor today and it worked just fine when I plugged it in. Then I rebooted my computer this morning and suddenly 1280x1024 was gone. So I added Modes "1280x1024""1024x768""800x600" to my xorg.conf saved and rebooted. This didn't work so I checked my xorg.conf and saw that all of my old configurations were completely gone and the whole file had 2 sections (one for the monitor which was wrong and one other for something else). So I rebooted the computer and ran xfix and now ubuntu keeps booting to an "out of range" error following the splash screen. My dear computer is now completely unusable. Please help =[

---

### Post by md389 on 2009-10-27
Also, just as an example of just how messed up my xorg.conf is here is what it looks like at this moment:

Section "Device"
      Identifier "Configured Video Device"
EndSection

Section "Monitor"
      Identifier "Configured Monitor"
EndSection

Section "Screen"
      Identifier "Default Screen"
      Monitor "Configured Monitor"
      Device "Configured Video Device"
EndSection

where is my video card?! what the hell happened?

---

