---
title: "Modeline in xorg.conf can't be used"
date: 2008-11-02
forum: Multimedia Software
---

### Post by Merlin_ua on 2008-11-02
Hi everybody,

I have the following problem with Sanyo PLV Z5 projector. It is the only output device attached to my box (I don't have monitor). It works in general, but I fail to set up the native 1280x720 video mode. I have taken the modelines for it here: [http://www.mythtv.org/wiki/index.php/Modeline_Database#Sanyo_PLV_Z4.2FZ5](http://www.mythtv.org/wiki/index.php/Modeline_Database#Sanyo_PLV_Z4.2FZ5)

I have edited the xorg.conf (Monitor section and Display subsection of Screen), but the desired mode is not available in the display settings screen. In /var/log/Xorg.0.log I see that my modes are parsed, but then comes:

Not using mode "1280x720" (no mode of this name)

Monitor configuration looks like this:

Section "Monitor"
        Identifier   "PLVZ5"
        HorizSync   30.0 - 62.0
        VertRefresh 50.0 - 85.0
        Modeline    "1280x720" 73.78 1280 1312 1592 1624 720 735 742 757
EndSection

Why can't it use the "1280x720" if I have the explicit modeline in Monitor?

Ubuntu 8.10 i386 desktop.

Thanks in advance!

---

### Post by Merlin_ua on 2008-11-03
So, no suggestions on this one? I just don't understand why my Modeline can't be used if I explicitly specify it...

---

