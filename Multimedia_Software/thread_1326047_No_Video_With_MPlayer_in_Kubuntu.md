---
title: "No Video With MPlayer in Kubuntu"
date: 2009-11-14
forum: Multimedia Software
---

### Post by Uncle Spellbinder on 2009-11-14
Odd. Fresh install (Clean, Not an Upgrade). Installed restricted extras and W32 codecs.


When clicking an AVI, I get this:
[IMG]http://i33.tinypic.com/vmyss6.jpg[/IMG]


Clicking "OK" gets me this:
[IMG]http://i36.tinypic.com/28asrar.jpg[/IMG]

---

### Post by andrew.46 on 2009-11-14
Hi Uncle Spellbinder,

This error usually indicates that the default *video out* that is selected is innapropriate for your setup. If you have a look in the preferences for MPlayer (or more correctly GMPlayer) there should be a section where you can select a setting such as x11. Once this is set see if the audio out error is still there, you may have to make a similar change to the *audio out* setting.

BTW I am a little jealous of the specs on your computer:

> HP Pavillion Elite * Intel Core 2 Quad (2.50GHz) * 8GB DDR2 RAM * nVidia GeForce 9800GT
NTSC TV tuner: Hauppauge WinTV HVR-1800 (Model 78xxx, Combo ATSC/QAM) 

I would not mind having a powerful machine like that :).

Andrew

---

### Post by somking95 on 2009-11-14
> **andrew.46 said:**
> Hi Uncle Spellbinder,

This error usually indicates that the default *video out* that is selected is innapropriate for your setup. If you have a look in the preferences for MPlayer (or more correctly GMPlayer) there should be a section where you can select a setting such as x11. Once this is set see if the audio out error is still there, you may have to make a similar change to the *audio out* setting.

BTW I am a little jealous of the specs on your computer:



I would not mind having a powerful machine like that :).

Andrew

Is there a recommended setting for audio and video?

---

### Post by andrew.46 on 2009-11-14
Hi somking,

> **somking95 said:**
> Is there a recommended setting for audio and video?

Not really, it depends on how your system is setup and sometimes on the limitations imposed by the distro itself. I have found that my 2 friends Trial and Error were the best help in such a choice :).

Andrew

---

### Post by somking95 on 2009-11-14
> **andrew.46 said:**
> Hi somking,



Not really, it depends on how your system is setup and sometimes on the limitations imposed by the distro itself. I have found that my 2 friends Trial and Error were the best help in such a choice :).

Andrew

I will have to play around with it and see what works best. Gnome movie player works, no problem. I tried look to see what settings it used but did not find them.

---

