---
title: "i-tec icam tracer webcam and ubuntu/linux"
date: 2009-12-26
forum: Multimedia Software
---

### Post by babarosa on 2009-12-26
Hi everyone!

Me and a lot of astronomers use these days the webcam model "i-tec icam tracer" to record movies from the planets and then by choosing the best pictures and stacking these, we create quite high resolution images.

As far as I know, **_actually nobody_** got it to work (uvc, v4l, pwc) with linux - neither with ubuntu nor any other linux distribution :(

"lsusb" delivers
Bus 001 Device 004: ID 2770:930b NHJ, Ltd CCD Webcam(PC370R)

Here is a link to a driver project [http://gkall.hobby.nl/sq930x.html](http://gkall.hobby.nl/sq930x.html) - I was not able to achieve any advancement.

Is there a genius spirit out there who could help me/us?

My thanks in advance,
Michael

---

### Post by Peets on 2010-01-07
Habe das selbe Problem. 
Ein weiterer Thread ist bei:
[http://forum.ubuntuusers.de/topic/webcam-trust-wb-3500t/](http://forum.ubuntuusers.de/topic/webcam-trust-wb-3500t/)

mit (PC370R) bei lsusb melden sich die Kameras 
"NHJ, Ltd CCD Webcam(PC370R)"
der Vertriebsmarken 
- "i-tec, iCam Tracer CCD"
- "Network CAM 4300" 
oder eine weitere mit demseben code aber anderem Namen:
"ORite  ORITE USB 2.0 CCD Webcam(PC370R)"
(weitere sind mir nicht bekannt)

Meine Treibersuche verlief ebenfalls negativ.
Habe die Kamera mal zerlegt und versuche die Fotos hier reinzustellen; man kann die Beschriftung der Chips erkennen. Wäre nützlich, wenn man einen Kontakt zu der Firma, die die Treiber geschrieben hat finden könnte.

---

### Post by Peets on 2010-01-07
... Ergänzung:

Die Chipbezeichnungen sind auf dem Foto nicht perfekt erkennbar, hier nochmal:
hinten:
- Sony, D1267AN, 20 Pin SO-Wide Gehäuse
- AD, 9943KCPZ, 32 Pin Q... Gehäuse
vorne:
- SQ, SQ930B-L

---

### Post by Benni123 on 2010-05-21
Hello, After exchanging some e-mails with the linux gspca maintainer.  the cam seems now to work somewhat. Although the driver is not ready and  still in development.

You can download the gspca_test tarball  here:
[http://moinejf.free.fr/](http://moinejf.free.fr/)

It would be good if  there are other testers who can help the gspca maintainer to complete  the driver for that cam.

It may also help, if there are people who  use this cam in windows. To develop a linux driver, USB traces are  interesting. Install a free usb sniffer  [http://benoit.papillault.free.fr/usbsnoop/](http://benoit.papillault.free.fr/usbsnoop/) and set it up for the webcam,  then connect the webcam and take some images and / or change some  settings of the driver. This gives helpful information of how the pc  must communicate to the cam.

Hopefully, we will soon have a good linux driver for  this interesting and light sensitive webcam.

---

### Post by jalemrubio on 2011-09-02
Ubuntu 11.04

Itec icam tracer working (?)with gspca - sq930x driver but i cannot set the fps. Cheese shows the image inverted but colors are ok. With guvcview we can hange gain and exposure values, size (320x240 or 640x480) but cannot set I420 compression nor fps values, asigned by default to 1fps (too low for capturing palnetary images!) 

but this works finally. White balance and fps is needed for astronomical use of this cam, so if anybody knows the trick...


Jaime Alemany
Ciudad Real, Spain

---

### Post by no2498 on 2011-09-02
you may try using v4l2ucp
if you install it it comes up in system preferences as video4linux control panel

hope it helps you

i more thing wxcam gives me more fps

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

---

### Post by jalemrubio on 2011-09-07
ok, i tried v4l2ucp with cheese and all is ok.  I have more fps ( exposure value limits fps, thats correct, but now i can take decent video captures )


thanks!

---

### Post by no2498 on 2011-09-07
wxcam has a lot of settings

---

