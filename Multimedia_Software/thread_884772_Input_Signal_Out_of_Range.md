---
title: "Input Signal Out of Range"
date: 2008-08-09
forum: Multimedia Software
---

### Post by tromort on 2008-08-09
I downloaded a demo of Quake Wars: Enemy Territory to see if it was worth to buy it. installation went fine, but when I try to run it i hear sound but get a black screen with the following error message: Input signal out of range.
-Nvidia drivers enabled.
-reconfigured Xserver Xorg
-Able to play Enemy Territory wolfenstein.
I've had this error before by changing setting of Enemy Territory, but after putting my original setting back it was always fixed. 
but since this is my first time running Quake Wars and not understanding that config file, Im downloading the windows version now, gonbe give it a try with wine.

Monitor: HannsG HC174D 1024 x 768 @ 75 Hz

---

### Post by chadoh on 2008-08-21
I just had a similar problem with an hp vs15 1024x768 monitor. After installing ubuntu on a friends computer, everything is working fine, but the initial ubuntu loading screen does not show up and the monitor says "Input Signal out of Range: Change settings to 1024 x 768 - 60Hz". This screen stays up until the login screen appears, which then works (a short message is displayed before it comes up: "auto configuring resolution" or something like that). It just makes the turning on/off process seem much more sloppy. Anyone know how to configure this?

Thanks.

---

### Post by olskar on 2008-10-30
> **chadoh said:**
> I just had a similar problem with an hp vs15 1024x768 monitor. After installing ubuntu on a friends computer, everything is working fine, but the initial ubuntu loading screen does not show up and the monitor says "Input Signal out of Range: Change settings to 1024 x 768 - 60Hz". This screen stays up until the login screen appears, which then works (a short message is displayed before it comes up: "auto configuring resolution" or something like that). It just makes the turning on/off process seem much more sloppy. Anyone know how to configure this?

Thanks.

I get this too..is a bug reported?

---

### Post by aeiah on 2008-10-30
> **tromort said:**
> I downloaded a demo of Quake Wars: Enemy Territory to see if it was worth to buy it. installation went fine, but when I try to run it i hear sound but get a black screen with the following error message: Input signal out of range.
-Nvidia drivers enabled.
-reconfigured Xserver Xorg
-Able to play Enemy Territory wolfenstein.
I've had this error before by changing setting of Enemy Territory, but after putting my original setting back it was always fixed. 
but since this is my first time running Quake Wars and not understanding that config file, Im downloading the windows version now, gonbe give it a try with wine.

Monitor: HannsG HC174D 1024 x 768 @ 75 Hz

have a look in the quake config file. you'll be able to change the resolution from there and run it. its probably a refresh problem or something. or you can set it to run in a window and mess with settings from within quake. you can edit it with a normal text editor but do some googling if it isnt obvious what you edit.

---

