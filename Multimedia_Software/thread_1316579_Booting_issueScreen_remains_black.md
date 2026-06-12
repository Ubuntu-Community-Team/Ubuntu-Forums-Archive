---
title: "Booting issue:Screen remains black"
date: 2009-11-06
forum: Multimedia Software
---

### Post by harishsangwan on 2009-11-06
Hey guys..I am new to Linux...installed Ubuntu 9.10 on my desktop, dual boot with Windows XP...have Nvidia 7950GT graphic card for display...initially it booted normally and display was also fine, but then I wanted to use 'Extra Effects' in Visual Settings, for which I was asked to download/enable some nvidia related setting or file...which I did..then I was prompted to reboot for changes to take place, but since then every time time i try to boot into Ubuntu, the white colored ubuntu logo shows up and then nothing after that...screen remains black..I went into recovery mode but had no clue about what to do there...
So help me fix this issue guys..

---

### Post by Timbo24 on 2010-02-15
Ive had a similar problem;

My screen resolution was set to 1600x1200 when installing Ubuntu.  A week or two ago the resolution was 1280x960 when I started the computer; I don't know why, presumably following an update.

I went to change it back but the maximum resolution shown in System->Preferences->Display was 1280x1024.  I then went to System->Administration->Hardware Drivers and downloaded and activated the ATI/AMD (FGLRX) graphics driver.

This showed a max monitor resolution of 1600x1200 in the info window but the the maximum resolution available for selection was still 1280x1024.

Aftr searching the forums I ammended the xorg.config file, after making a backup, as below;

Section "Monitor"
    Identifier    "Viewsonic_VP211b"
        VendorName       "ViewSonic"
        ModelName        "VP211b"
    Modeline     "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
EndSection

The system appears to boot normally untill the login when the screen is black with a coloured speckled band at the top of the screen.  I can't log on and ctrl-alt-bckspc does nothing.

I used the live disk to reinstate the original xorg.config but this made no difference

I tried copying the xorg.conf.failsafe to xorg.conf but again the systemwould not display the login.

Does anybody have any advice?  I really dont want to reinstall as I am on a satelite internet conection with download limits.

I am using;
Ubuntu 9.04, kernel 2.6.28.11, Gnome 2.26.1
Asus P5QC motherboard, Intel E8500 processor, 4Mb RAM
Sapphire HD 3650 ATI graphics card, Viewsonic VP211b monitor

Thank you

---

### Post by fdmille on 2010-02-15
Can you login using failsafe mode?

---

### Post by Timbo24 on 2010-02-26
Thanks for responding, Sorry for the delay in replying,

No, I can't login using failsafe mode.

---

