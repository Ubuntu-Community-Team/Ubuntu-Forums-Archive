---
title: "Proprietary ATI Drivers Mostly Working on Dell D810 Laptop"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by hashstat on 2006-06-20
I have successfully installed the ATI 8.25.18 (fglrx) modules with Ubuntu 6.06 on my Dell Latitude D810 laptop with ATI Mobility Radeon X600 video card.  The driver works completely when the laptop is undocked, but only partially when docked.  When undocked, I can use the LCD or LCD + VGA.  When docked, I can use the LCD, LCD + DVI, or just the DVI.  However, I can not get the DVI + VGA combination to work.  The DVI and VGA monitors, along with their valid modes, are detected (both are Dell 1905FPs), but only the DVI receives output and the following error is logged in /var/log/Xorg.0.log.

[INDENT][FONT="Fixedsys"](EE) fglrx(0): No valid mode found for secondary display[/FONT][/INDENT]

Does anyone have any idea about how to correct this error?

I have the open source ati driver working with both external displays.  I use a boot-time script to switch out xorg.conf files depending on my docked status.  I would like to use the fglrx modules for both modes though.

I have tried multiple xorg.conf files using aticonfig and hand editing.  The attached xorg.conf file produced the attached Xorg log file (trimmed and split into three files to meet size restrictions).

Thanks in advance.

---

### Post by hashstat on 2006-06-27
The issue is resolved with the ATI 8.26.18 driver.

---

