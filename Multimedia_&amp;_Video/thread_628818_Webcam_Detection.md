---
title: "Webcam Detection"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by Spyderizer on 2007-12-01
Hi

Using a logitech communicate STX, 

lsusb says 
Bus 002 Device 002: ID 046d:08ad Logitech, Inc. 
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. 

Skype says "No video devices found"
Camorama says "unable to connect to /dev/video0/"

webcam however says: 
$ sudo webcam
reading config file: /home/mark/.webcamrc
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [24 bit TrueColor (LE: bgr)]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320

...and the blue light on top of the web cam comes on.

...any ideas?

---

### Post by Spyderizer on 2007-12-01
Figured it out, didn't have write access to /dev/video0.

Do'h!

---

