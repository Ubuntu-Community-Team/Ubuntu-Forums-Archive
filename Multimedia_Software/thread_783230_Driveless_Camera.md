---
title: "Driveless Camera"
date: 2008-05-05
forum: Multimedia Software
---

### Post by SecretSnack on 2008-05-05
I purchased a driverless usb video camera for cheap on eBay and I was very surprised that it worked, at least on Windows.  But when I plug it into my laptop with Ubuntu, nothing happens.  How do I get Ubuntu to recognize it?  Will I need a third-party program to record and save video files?  What should I use?

Thanks

---

### Post by davidfg4 on 2008-05-05
For a start, try installing camstream and cheese and see if either recognizes your camera.

---

### Post by SecretSnack on 2008-05-05
Just tried.  No luck.  I'll look around for some other cam apps.

---

### Post by davidfg4 on 2008-05-05
Or try this:
> **linuxwizard said:**
> Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. ( Video Plugin if it shows V4L change to V4L2 or if it shows V4L2 change to V4L.)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

