---
title: "QuickCam® Pro for Notebooks"
date: 2008-09-23
forum: Multimedia Software
---

### Post by welder663 on 2008-09-23
hi folks how do I get the drivers for this cam to work in ubuntu,if this has been asked,sorry bout that.I love ubuntu but i am also very green when it comes to this operating system.thanks in advance.

---

### Post by linuxwizard on 2008-09-24
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

