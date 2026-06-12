---
title: "GDM won't start after video card switch"
date: 2005-12-09
forum: Multimedia &amp; Video
---

### Post by lwinkenb on 2005-12-09
I was running a S3 PCI video card, but I swapped it out with a NVidia GeForce2 AGP video card.  In my xorg.conf file, I changed the "Device" section to the following:
> 
Section "Device"
   Identifier    "NVidia GForce2"
   Driver        "nv"
   BusID        "PCI:1:0:0"
   Option       "UseFBDev"    "true"
End Section

GDM still fails to start though.  The Xorg.0.log file says:
> 
(II) S3VIRGE driver (version 1.8.6) for S3VIRGE chipsets: ...
(II) Primary device is: PCI:1:0:0
(EE) No Devices Detected.

Fatal server error:
no screens found

Why does the Xorg.0.log file say it is still trying to load the S3VIRGE drivers for the card?  Can anyone point me in the right direction here?

---

### Post by codejunkie on 2005-12-09
[quote=lwinkenb]I was running a S3 PCI video card, but I swapped it out with a NVidia GeForce2 AGP video card.  In my xorg.conf file, I changed the "Device" section to the following:

GDM still fails to start though.  The Xorg.0.log file says:

Why does the Xorg.0.log file say it is still trying to load the S3VIRGE drivers for the card?  Can anyone point me in the right direction here?[/quote]
try running ```
sudo dpkg-reconfigure -phigh xserver-xorg
```from a terminal this should automatically detect and configure the card.

---

### Post by lwinkenb on 2005-12-09
I ran 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
But I still have the same problem.  It doesn't look like it changed any lines in xorg.conf, and Xorg.0.log says the same thing.

---

### Post by codejunkie on 2005-12-09
[quote=lwinkenb]I ran 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` But I still have the same problem.  It doesn't look like it changed any lines in xorg.conf, and Xorg.0.log says the same thing.[/quote]after you ran the command did you reboot the computer?

---

### Post by lwinkenb on 2005-12-10
Hehe, I guess you learn something new every day.  I didn't know you had to reboot after making changes to the xorg.conf file.  Everything seems to be working fine now, thank you for your help :)

---

