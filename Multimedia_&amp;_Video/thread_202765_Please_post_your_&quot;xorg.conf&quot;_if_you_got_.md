---
title: "Please post your &quot;xorg.conf&quot; if you got the unichrome drivers working"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by jeeves on 2006-06-24
I'm having very hard time getting the unichrome drivers to work. Would some folks who succeeded at this be willing to post their "xorg.conf" file(s). 

Thanks

I'm running Ubuntu 6.06 on a laptop with the S3 Graphics Unichrome Pro IGP integrated graphics. So far I have only been able to get the vesa drivers to work which are far too limited.

---

### Post by Tomy on 2006-06-24
xorg.conf is not normally the problem with the Unichrome **Pro. **There are other problems with the "via" driver and the **Pro. **The Unichrome IGP works well for me with this "Device" section in xorg.conf. I also have the Unichrome **Pro** IGP on a different motherboard  and use the same settings and it works but crashes certain programs.

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter" 
        Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "DisableIRQ"
        Option          "EnableAGPDMA"

EndSection

---

### Post by kulotzy on 2008-04-14
Bump.........

---

