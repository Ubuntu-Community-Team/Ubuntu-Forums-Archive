---
title: "Glitchy Webcam Image [MS VX-1000]"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by Joseph Duchesne on 2008-03-02
I'm trying to use my Logitech VX-1000 with Ubuntu 7.10 (unmodified kernel)
Here's what it looks like:
[IMG]http://myweb.dal.ca/th410663/WebcamMessup.png[/IMG]

It was like this when I simply installed Camorama to try the webcam out, and installing [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) didn't seem to help, although when I was trying my own webcam code (using openCV) it did display perfectly once. I haven't been able to duplicate that.

The image seems to be reading RGB as BRG or vise versa (the colors are off) and what appears to be static (or jpg artifacts) do not change from frame to fram, they stay still while the image moves. 

Is there anything I can install to get this webcam working? I've noticed that a few people around the forums have managed to get this webcam working with the spca5xx driver, but there doesn't seem to be further information on how exactly they did that.

Note: Playing with the image controls doesn't help.

---

### Post by linuxwizard on 2008-03-02
In the white box under effects > right click > add filter > color correction. See if that helps. Also try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. If that does not work post results of the command > lsusb

---

### Post by deadite66 on 2008-03-09
no luck for me either with this webcam
i tried updating the gspca drivers too.

```
[1051971.472423] usb 4-2.1: USB disconnect, address 23
[1051974.482666] usb 4-2.1: new full speed USB device using ehci_hcd and address 24
[1051974.575372] usb 4-2.1: configuration #1 chosen from 1 choice
[1051974.575778] usb 4-2.1: SN9C105 PC Camera Controller detected (vid:pid 0x045E:0x00F7)
[1051974.600369] usb 4-2.1: No supported image sensor detected for this bridge
[1051974.600399] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. SONIX JPEG (sn9c1xx) 

```

---

### Post by linuxwizard on 2008-03-09
deadite66
What have you tried using your webcam with ? Did you try Ekiga ? After updating driver did you reboot your computer ?

---

### Post by deadite66 on 2008-03-10
> **linuxwizard said:**
> deadite66
What have you tried using your webcam with ? Did you try Ekiga ? After updating driver did you reboot your computer ?

tried with camorama and vlc.
just tried with ekiga which detected it but can't how to see it without connecting to someone, just shows a round orange ball.

i rmmod and modprobe when updating the drivers.

---

### Post by linuxwizard on 2008-03-10
To test your webcam you can do this:

There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by deadite66 on 2008-03-10
yeah tried all that no good, suspected it might be down to all the driver messing around i've done so restored a partimage backup.

ekiga shows the same type of picture on OP.
just tried the new [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) driver but still mangled image.

---

### Post by linuxwizard on 2008-03-10
MicroSoft VX1000 is listed here > [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) > it shows that cam uses the gspcav driver.

---

### Post by deadite66 on 2008-03-10
> **linuxwizard said:**
> MicroSoft VX1000 is listed here > [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) > it shows that cam uses the gspcav driver.

i had tried that driver before, just installed again, still rubbish.

---

### Post by linuxwizard on 2008-03-10
Not sure what else to tell you. That mightbe the best picture you will get with that cam in Linux. You have tried different apps. same quality picture.

---

### Post by deadite66 on 2008-03-10
yeah this cam is junk in linux, shame.

---

### Post by scitech on 2008-05-06
If you try this
```
camorama -x 640 -y 480
```

the colors are slightly better, and if you add "Color Correction" with in camorama, they get a lot better.

Not sure how to do this on amsn and ekiga though.

Greetings.

---

