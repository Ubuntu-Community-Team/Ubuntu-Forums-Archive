---
title: "Vaio Camera Internal Camera not Working"
date: 2008-12-19
forum: Multimedia Software
---

### Post by dls156 on 2008-12-19
Any suggestions or help with this would be great. I have tried both F-Spot, Cheese, and Skype. All of them say they can't find a camera. Reading through the forums it seemed that most people with this problem didn't have it showing up with lsusb, I do:

Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The Ricoh one is my camera and I found the latest package and installed it... help:confused:

Please type slowly, I'm a noob with Linux. Thanks in advance!

---

### Post by Charidan on 2011-09-12
I've got the same problem, except I don't even know if I have drivers for the camera installed or not. I don't suppose you know how to check that or install the drivers?

My readout looks almost identical:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 004 Device 002: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:1833 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I have a Sony VAIO PCG-8V1L or VGN-AR150G. I think that's a zero but it might be an O.

---

### Post by no2498 on 2011-09-12
you need to get the driver for the Ricoh cams
i dont think ubuntu/linux has made any for the kernel yet
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

is a link in that that may help

---

### Post by Charidan on 2011-09-12
Doesn't look like it. Theoretically the laptop is made by Sony, but I don't see any Sony webcams on the support list. I'll try some searching to see if my camera is made by someone else and grafted into the VAIO body.

In the meantime I just found the Skype Webcam help on the [Ubuntu wiki]("https://wiki.ubuntu.com/SkypeWebCams%22")  and it looks like they have our camera there. Do a text search (CTRL+F)  for "Ricoh" and you'll find the camera in the list with a link to [userspace tools]("https://bitbucket.org/ahixon/r5u87x/").  He's got some detailed instructions there. It seems to work except that  my specific camera is only halfway compatible because of its type. Apparently he's been trying to fix that for a while and isn't really sure what's up with the problem in the first place.

EDIT: Nope, it looks like the camera is a legitimate Sony part specific to the laptop model. Given that the only support the wiki offers on Sony products is for playstation eyetoy I don't really think I'm gonna find too much help in that direction.

---

### Post by Charidan on 2011-09-12
[http://www.arakhne.org/ricoh/](http://www.arakhne.org/ricoh/)

Check this out. It has the separate driver for WDM devices. Looks like a win, but haven't tested it yet.

---

