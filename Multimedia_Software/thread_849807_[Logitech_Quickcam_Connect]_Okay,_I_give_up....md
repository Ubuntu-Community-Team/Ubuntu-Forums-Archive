---
title: "[Logitech Quickcam Connect] Okay, I give up..."
date: 2008-07-04
forum: Multimedia Software
---

### Post by TheKid965 on 2008-07-04
I have tried *everything* I know how to do to get this webcam working.  I've searched the forums.  I've tried EasyCam2.  I've tried compiling the spca5xx driver.  Nothing's worked.  I'm just not getting the necessary video device no matter what I do.

The camera in question was just purchased from Micro Center today - a Logitech Quickcam Connect E2500 series.  Here's the dmesg output from when I disconnect and then reconnect it:

```
[ 9014.227752] usbcore: registered new interface driver gspca
[ 9014.227759] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[ 9262.650686] usb 1-7: USB disconnect, address 5
[ 9287.213445] usb 2-3.4: new full speed USB device using ehci_hcd and address 8
[ 9287.322721] usb 2-3.4: configuration #1 chosen from 1 choice
```And here's the relevant lsusb line:```
Bus 002 Device 008: ID 046d:089d Logitech, Inc.
```I am literally about to go nuts trying to figure this out.  I was informed that Logitech Quickcams were generally supported out-of-the-box with Ubuntu, and now I'm discovering something quite the opposite.

Any help would be greatly appreciated.

---

### Post by linuxwizard on 2008-07-05
The webcam must be a new release from Logitech. I can't find anything on your webcam > Bus 002 Device 008: ID 046d:089d Logitech, Inc.  It is not even listed here > [http://www.quickcamteam.net/hcl/linux/logitech-webcams](http://www.quickcamteam.net/hcl/linux/logitech-webcams). Being a new product their might not even be a driver for it in Linux.

---

### Post by TheKid965 on 2008-07-05
> **linuxwizard said:**
> The webcam must be a new release from Logitech. I can't find anything on your webcam > Bus 002 Device 008: ID 046d:089d Logitech, Inc.  It is not even listed here > [http://www.quickcamteam.net/hcl/linux/logitech-webcams](http://www.quickcamteam.net/hcl/linux/logitech-webcams). Being a new product their might not even be a driver for it in Linux.

This is the conclusion I've come to myself, that at some point in recent memory Logitech changed something with this model camera that renders it unusable by the spca5xx driver.

I had been operating under the assumption that the Logitech Quickcam Connect had a vendor ID of 0x08d9, and was a retitled Express II, which *did* work with that driver.  Apparently this is no longer the case.

I guess I'll just have to exchange this for one that works (I understand the Quickcam Communicate line is more Ubuntu-friendly?) and chalk this one up to experience.

The moral of the story, I suppose, is to always confirm the lsusb output if you can; the camera you thought would work with the driver you compiled might in fact be an entirely different device under the skin.

---

### Post by linuxwizard on 2008-07-05
Hopefully Micro Center will let you exchange the webcam for another one. Being that I could not find anything and Logitech not showing that unit I just figured it was a new webcam. Good Luck

---

### Post by trjnhrse44 on 2008-07-18
have hope,
this cam is brand new rework of the qc connect from logitech,
the cam is probably supported by easycam or gspcav but the bridge and sensor need to be figured out and worked into the driver.  I am working on this myself but may not finish before someone else...
This shoul be fixed soon....

---

### Post by trueshanti on 2008-07-18
i recorded a usbmon-debug of the E2500 .. details here :


[http://forums.quickcamteam.net/showthread.php?tid=382](http://forums.quickcamteam.net/showthread.php?tid=382)

---

### Post by markbuntu on 2008-07-19
See if micorcenter will exchange it for a Communicate STX.

---

### Post by Eredeath on 2008-07-23
Yea i'm having the same issue, just bought the camera today... taking it back tomorrow. Hope things work out for you

---

