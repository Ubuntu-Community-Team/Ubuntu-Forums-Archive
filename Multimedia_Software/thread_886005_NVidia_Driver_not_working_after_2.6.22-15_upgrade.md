---
title: "NVidia Driver not working after 2.6.22-15 upgrade"
date: 2008-08-10
forum: Multimedia Software
---

### Post by NuttinButNet on 2008-08-10
Hi,

I'm running Gutsy and the 2.6.22-15 kernel.  I'm running this machine mostly as a MythTV box (98%), but Myth isn't the problem and I can run the gnome GUI too. 
I was running 2.5.22-14 with the proprietary the NVidia drivers and it was working fine.  After a minor upgrade, the Nvidia driver wouldn't run and I found out that the kernel upgraded on me.  OK fine, I download the latest Nvidia drivers and recompiled them using the Nvidia installer.  No complaints from the Nvidia installer.

I just can't get X running. My Xorg.0.log and my Startx show the same thing.
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.


I've been playing the my xorg.conf and even regenerated it using nvidia.xconfig, but none of it seems to work.

Here is a the screen sections of my xorg.conf

Section "Monitor"
        Identifier "Monitor0"
        VendorName "Mitsubishi"
        ModelName "HC1500"
        HorizSync 15.73 - 68.68
        VertRefresh 50 - 75
        Modeline "1280x720@60"  74.48  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x720@60"
    EndSubSection
EndSection

This was the configuration before the upgrade.

I can run the "nv" driver and it works, but it doesn't work well.
The NVIDIA drivers were much better.
I've looked at threads on the board for this problem and none of the solutions seem to help me.  I've tried resticting the nv module and checking for corrupted edid. Neither solution help.

Thanks

---

### Post by NuttinButNet on 2008-08-10
I found the solution myself.

After I posted this I found the problem after reading
[http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=139&p_created=1099953286&p_sid=ehXXC-aj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzgsMzgmcF9wcm9kcz0yJnBfY2F0cz01OCZwX3B2PTEuMiZwX2N2PTEuNTgmcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWxpbnV4&p_li=&p_topview=1]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=139&p_created=1099953286&p_sid=ehXXC-aj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MzgsMzgmcF9wcm9kcz0yJnBfY2F0cz01OCZwX3B2PTEuMiZwX2N2PTEuNTgmcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PWxpbnV4&p_li=&p_topview=1")

After the upgrade the nvidia module wasn't loading anymore.
After a 
modprobe -i nvidia
X started just fine.

---

