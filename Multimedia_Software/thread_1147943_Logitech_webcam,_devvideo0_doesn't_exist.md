---
title: "Logitech webcam, /dev/video0 doesn't exist"
date: 2009-05-03
forum: Multimedia Software
---

### Post by CTolley on 2009-05-03
I have a Logitech Quickcam Pro for Notebooks.  It shows up in lsusb.  I cannot mount it in VLC, Cheese, or Camorama.  I have been searching the forums for the past few days and have tried various things, but the wall I keep hitting seems to be the lack of /dev/video0 folder.  I don't have any /dev/video folders.  

Ubuntu 9.04
Compaq Presario desktop

I also have a really annoying mosquito bite right on a knuckle.  It's really annoying.

---

### Post by Cresho on 2009-05-04
how about /dev/video1

also lsusb and see what usb is using it.

---

### Post by CTolley on 2009-05-04
nope, no /dev/video1 either.

lsusb report:
> Bus 001 Device 007: ID 046d:08c3 Logitech, Inc. Camera (Notebooks Pro)
Bus 001 Device 006: ID 1058:1103 Western Digital Technologies, Inc. 
Bus 001 Device 004: ID 058f:6390 Alcor Micro Corp. USB 2.0-IDE bridge
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by CTolley on 2009-05-06
Okay, so using Nautilus, I created a /dev/video0 folder.  Using Camorama I now get the following error:

"Could not connect to video device (/dev/video0).  Please check connection"

I take that to mean that there should be something in the folder, now that it exists.  Is the something that should be there something I can make, or is this camera a lost cause?

---

### Post by CTolley on 2009-05-08
Fixed.  Video card on desktop is just a giant pile of garbage.  Got the laptop hooked up in inet and ran all of the updates, then I tried the webcam on it and it works like a champ with no other modifications.

---

