---
title: "Tevion 1.3mp Webcam Problems"
date: 2008-05-14
forum: Multimedia Software
---

### Post by pevans91 on 2008-05-14
Hey All!

This being my first post, i'm posting in hope for a solution to the problem of my webcamera not working. I'm a Linux noobie unfortunately, but have quite a lot of computing knowledge with erm.... another operating system =p. The webcam i'm trying to get working is a Tevion 1.3mp webcamera, i've tried using EasyCam2 but it simply finds no webcam present. 

Any help would be appreciated =)

When using lsusb the computer finds the webcamera as Z-Star Microelectronics... It is not

```
Bus 005 Device 009: ID 0ac8:0323 Z-Star Microelectronics Corp. Luxya WC-1200 USB 2.0 Webcam

```

And when inserting the camera i get...

```
[ 4231.590432] usb 5-2: new high speed USB device using ehci_hcd and address 9
[ 4231.754652] usb 5-2: configuration #1 chosen from 1 choice
[ 4231.755199] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(VC0323) 

```

Where do i go from here?

Thanks

---

### Post by iswa on 2008-05-15
Hi pevans91,

Sorry but I have no experience with webcams on Ubuntu, but I found a few links that may be of use:

[http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon-2/](http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon-2/)
[http://www.debianadmin.com/how-to-configure-webcam-in-debian-linux.html](http://www.debianadmin.com/how-to-configure-webcam-in-debian-linux.html)
[http://ubuntuforums.org/showthread.php?t=322218](http://ubuntuforums.org/showthread.php?t=322218)

Note that none are for your specific model (or even for Hardy), but they may point you in the right direction.

Have you tried:
```
sudo modprobe gspca
```

HopeThisHelps.

---

