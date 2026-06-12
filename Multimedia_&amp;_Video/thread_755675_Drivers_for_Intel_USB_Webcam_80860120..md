---
title: "Drivers for Intel USB Webcam 8086:0120."
date: 2008-04-15
forum: Multimedia &amp; Video
---

### Post by sradhakrishna on 2008-04-15
Hi,

I have got an Intel USB webcam for which lsusb outputs 8086:0120. I've tried gspca drivers, but doesn't seem to work. The list of supported devices on [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) doesn't list out this device, so, guess this was expected.

My queries:
1.   Has anyone figured out how to get this webcam to work??
2.   I would want to contribute to gspca by enabling this webcam. Can anyone point me in the right direction to see where to start??

Thanks in advance.

Regards,
Radha.

---

### Post by linuxwizard on 2008-04-15
Post the complete results of > lsusb

Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

