---
title: "Video card &amp; monitor not detected?"
date: 2009-05-12
forum: Multimedia Software
---

### Post by NeatO7364 on 2009-05-12
Hi all,

I have Ubuntu 9.04 installed on the computer I'm currently using.  I had never tried before but was inspired to try and get a cool looking desktop setup.  After a few hours spent toying around, I realized that my monitor & graphics card are not being detected by Ubuntu and I'm not sure how to install the drivers.  I have a legacy ATI video card here but I'm not sure what model it is.  This motherboard also has onboard video that I could enable if needed (although I'm not sure how to do this).  The motherboard is an MSI KM4M-V.  I tried installing the proprietary drivers with EnvyNG and that completely screwed up my graphics.  Also, my xorg.conf file looks surprisingly slim:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

And that's IT!  

Any help/advice would be greatly appreciated.  Thanks!

---

### Post by overdrank on 2009-05-12
Hi and if you look under system, administration, hardware drivers to see if you can enable any drivers for your graphics.
You may also use the command in the terminal located under applications, accessories. ```
lspci | grep VGA
``` to identify your graphics model will help.

---

### Post by NeatO7364 on 2009-05-12
lspci returns the following:
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

Hardware Drivers says: No proprietary drivers are in use on this system.

---

### Post by overdrank on 2009-05-12
> **NeatO7364 said:**
> lspci returns the following:
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

Hardware Drivers says: No proprietary drivers are in use on this system.

Hi  and that ATI graphics I believe will not support the desktop effects.
The onbaord graphics for the mother board are S3 Graphics UniChrome I believe and they will not support them either. :(

---

