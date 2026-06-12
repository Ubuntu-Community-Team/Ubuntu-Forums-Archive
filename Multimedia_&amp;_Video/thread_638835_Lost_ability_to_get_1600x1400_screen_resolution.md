---
title: "Lost ability to get 1600x1400 screen resolution"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by mblind on 2007-12-12
I have a NVIDIA Quadro NVS 140 and a Dell D830 Laptop. I use to be able to get 1600x1200 resolution but now I can only get 1440x900.. I am not sure what I did.. any idea how to get access to the higher resolution?

Thanks for the help

update: ANYONE?!!

---

### Post by elliotjreed on 2007-12-14
Calm down! Hehe!

Just try:

sudo dpkg-reconfigure xserver-xorg

Go through the list, selecting appropriet (usually what you already have), then it will come to a screen to select available resolutions, uncheck all but the one you want!

If that don't work, try[ http://www.linux.com/feature/118108]("http://www.linux.com/feature/118108") and scroll down to the resolution bit! The file you will need to edit is the xorg.conf.

---

### Post by mblind on 2007-12-23
Thank you very much.. also gksudo nvidia-settings did it too..

---

