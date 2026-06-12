---
title: "Is Ubuntu 11.10 wasting my time with Logitech webcam?"
date: 2011-10-21
forum: Multimedia Software
---

### Post by goreyduke on 2011-10-21
[FONT="Trebuchet MS"]Hello, my Logitech webcam has NEVER worked in Skype on any of four or five Ubuntu distros. Should I throw it away and buy another one to use U11.10 or stick to W7 where it works fine?

Or **CAN IT BE MADE TO WORK**??

Strangely, when I first tested the webcam in Ocelot, the camera came on perfectly, but with no sound. When I tried to correct the sound, the vision went. Weird, huh? 

I tried this work around - [http://ubuntuforums.org/showthread.p...ogitech+webcam](http://ubuntuforums.org/showthread.p...ogitech+webcam) - but only know how to use a terminal, not a "text editor", so am stumped.

Until I can get Skype and e-mails on Ubuntu, I will have to stay with Windows full-time. All advice considered. Thanks...[/FONT]

---

### Post by no2498 on 2011-10-21
install guvcview
open a terminal type dmesg click enter
after it stops type lsusb click enter
try the cam in guvcview
for skype try this in a terminal
this is only good for 32 bit
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by goreyduke on 2011-10-21
Thanks no2498, I gave both of those a go but not with much success.I recognised the Linux description of the webcam to line up the mic but the camera/video button just threw me out. Clicking guvcview now says "Unable to open device. Please make sure the camera is connected and that the correct driver is installed."

Opening a fresh terminal and pasting in the preload instruction produced: "permission denied".

It is a 32-bit pc, I know that much! Cheers

---

### Post by wolfen69 on 2011-10-21
> **goreyduke said:**
> [FONT="Trebuchet MS"]Should I throw it away and buy another one to use U11.10 or stick to W7 where it works fine?
[/FONT]

I wouldn't give up just yet, as there are many helpful people here. But for me personally, after trying to get it going and being unsuccessful, I would just buy a new compatible webcam. Well worth it to be free of windows. [Here]("http://www.ideasonboard.org/uvc/") is a list of compatible (the ones with the green check mark) webcams in linux. Good luck.

---

### Post by no2498 on 2011-10-22
goreyduke
look in your system startup programs see if cheese or skype is set to auto startup
turn them both off and restart the computer

---

