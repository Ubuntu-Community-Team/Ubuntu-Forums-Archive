---
title: "Mikomi Webcam Drivers"
date: 2008-09-07
forum: Multimedia Software
---

### Post by w3rt on 2008-09-07
Okay so I have a mikomi AP-7121u, ubuntu detects it as a usb webcam, although it cannot detect the drivers for it, i have tried searching the net for drivers but as far as i can see there are none available for linux, anybody had any luck getting it to work on ubuntu?

---

### Post by linuxwizard on 2008-09-07
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

