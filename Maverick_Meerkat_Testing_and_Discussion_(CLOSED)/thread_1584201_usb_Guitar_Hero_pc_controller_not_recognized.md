---
title: "usb Guitar Hero pc controller not recognized"
date: 2010-09-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by FishRCynic on 2010-09-28
Guitar Hero PC (xbox) usb controller is not recognized by maverick amd64
(wanted to see how FoFix works with controller)

Controller is recognized by lucid amd64

Has anyone else had issues with usb game controllers?
(or can advise if support for this controller has been dropped)

I will see if i still have some usb game pads and see what happens.

(usb keys seem to work fine for me but i have no other usb devices to try at the moment)

---

### Post by FishRCynic on 2010-09-28
it appears that the issue is not with the game controllers per se but with my card reader - after playing with the card reader cables
i now get

[ 4465.122534] usb 2-6: new full speed USB device using ohci_hcd and address 35
[ 4465.363552] Registered led device: xpad1
[ 4465.363686] input: RedOctane Guitar Hero X-plorer as /devices/pci0000:00/0000:00:0b.0/usb2/2-6/2-6:1.0/input/input7
[ 4465.640050] hub 2-0:1.0: unable to enumerate USB device on port 8
[ 4465.920077] hub 2-0:1.0: unable to enumerate USB device on port 8
[ 4466.200047] hub 2-0:1.0: unable to enumerate USB device on port 8
[ 4466.480091] hub 2-0:1.0: unable to enumerate USB device on port 8
[ 4466.760063] hub 2-0:1.0: unable to enumerate USB device on port 8
[ 4467.040068] hub 2-0:1.0: unable to enumerate USB device on port 8
[ 4467.320061] hub 2-0:1.0: unable to enumerate USB device on port 8

but no card reader drives
(my sd drive icons etc have disappered in Places Computer)

i will investigate this over the next few days - it is either the card reader (i did not test it previously), its cables or it is not supported

but there appears to be no problems with the usb controllers

---

### Post by FishRCynic on 2010-09-29
gremlins (i guess)
shut off the machine earlier, turned it on a few moments ago
(without changing anything)
and all is as it should be 
sd drive icon etc appear, and plugging in controllers finds the controllers
(didn't use the usb on the card reader this time, it is still possible it is the culprit-will test later)

now to setup fofix:guitar:

---

