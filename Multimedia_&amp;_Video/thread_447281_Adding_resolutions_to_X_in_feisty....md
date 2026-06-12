---
title: "Adding resolutions to X in feisty..."
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by sloggerkhan on 2007-05-17
So in past Ubuntus, if I wanted more resolutions with fglrx, I could just add them in modes.
However, in feisty, I can not figure out how to add extra resolutions. I'd like to add 1440x900 and 1280x800 but can't seem to find a way. Using fglrx drivers.

---

### Post by leetcharmer on 2007-05-25
I've got the same problem, can anyone help us out?

---

### Post by Medieval_Creations on 2007-05-25
I have an nVidia GeForce so I'm not sure how much help I will be.  But you could try editing the xorg.conf and adding those resolutions.

sudo pico /etc/X11/xorg.conf

or

Make sure you have the most recent drivers installed , then try to reconfigure xorg.

sudo dpkg-reconfigure xserver-xorg

---

