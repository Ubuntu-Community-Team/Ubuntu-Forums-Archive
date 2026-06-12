---
title: "how to adjust the  icon and character size in mythbuntu desktop?"
date: 2014-06-16
forum: Mythbuntu
---

### Post by madonion2 on 2014-06-16
Hello!!

I am the first time to install mythbuntu and the version is 14.04.  after the installation and boot up the system, I see the first screen of mythTV, it seems good.  but when I exit this first screen and go to the desktop of Ubuntu, everything in the screen is very small.  the icon and the character are not easy to read.


please see the attached print screen to show you the situation.  1920*1080 is match to my monitor.  P
lease anyone can let me know how to solve this problem?  thank a lot.;)

[IMG]http://n2.hk/d/attachments/day_140613/20140613_cef04909e6fbc8e1a05cZaHsMBTEojHT.jpg[/IMG]

---

### Post by cedyathome on 2014-06-30
Try adding the lines in bold to the Section "Device" in your xorg.conf. Let us know if it works. I had the same issue with 14.04.

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 610"
[B]    Option "UseEdidDpi" "False"
    Option "DPI" "100 x 100"
[/B]EndSection

---

### Post by madonion2 on 2014-07-07
> **cedyathome said:**
> Try adding the lines in bold to the Section "Device" in your xorg.conf. Let us know if it works. I had the same issue with 14.04.

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 610"
[B]    Option "UseEdidDpi" "False"
    Option "DPI" "100 x 100"
[/B]EndSection

do you mean input the above commend in the terminal?

---

### Post by madonion2 on 2014-08-24
Does anyone got any idea?  Please help!  thanks. ;)

---

### Post by Lester_Burnham on 2014-08-25
Go to settings > appearance > fonts
Then change custom DPI setting to 100

Or add info from the post earlier to /etc/xorg.conf

Lester

---

### Post by madonion2 on 2014-08-26
thanks a lot. let me try. ;)

> **Lester_Burnham said:**
> Go to settings > appearance > fonts
Then change custom DPI setting to 100

Or add info from the post earlier to /etc/xorg.conf

Lester

---

