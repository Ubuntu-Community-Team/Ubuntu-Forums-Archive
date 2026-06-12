---
title: "Weird screen offset at 1360x768"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by gspr on 2007-08-07
Hi.

I have a Tatung 32" HDTV connected to an ATI Radeon 9700 using DVI/HDMI. After some fiddling with modelines (read: I went one page up from the tv's manual page called "specifications" and found the REAL specifications) it's running at its native 1360x768.

However, a problem arises that does NOT show up with two old Nvidia cards I have lying around: The screen is offset to the right, and the mouse points a position higher on the screen than the cursor indicates. Please see the two following links to see what I mean:

Offset: [http://folk.ntnu.no/spreeman/stuff/tatung_ati/cimg2447edited.jpg](http://folk.ntnu.no/spreeman/stuff/tatung_ati/cimg2447edited.jpg)
Mouse behaviour: [http://folk.ntnu.no/spreeman/stuff/tatung_ati/cimg2449edited.jpg](http://folk.ntnu.no/spreeman/stuff/tatung_ati/cimg2449edited.jpg)

Do note that the mouse behaviour subsides when moving towards the top of the screen. Once I reach the title bar of a window, the cursor and the real position have pretty much converged. 

This is so weird... Any help is appreciated.

---

### Post by jnorthr on 2007-08-07
The older cards may be thinking they are sending to a device of 1024 x 768 px, which as you say it is not. This may account for the offset appearance of the image on your screen and this may also explain mouse and other issues. Unless you can get a graphics card to generate exactly what the hardware device wants, 1280x1024, 1024x768, 1600x1200, etc. you may never see a correctly displayed image. Does your TV have any 'standard' settings that match one of these configurations that you could set it to ?

---

### Post by gspr on 2007-08-07
Yes, 1280x768, but the ATI card refuses to output that. The much older (2 and 3 years) nVidia cards do, however, correctly display 1360x768.

---

### Post by gspr on 2007-08-09
I gave up on the ATI card and went back to a trusty old nvidia card. Any future ideas about the ATI behaviour are still welcome, though.

---

