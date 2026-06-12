---
title: "Logitech webcam support"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by rajus on 2007-01-16
Logitech QuickCam Chat is apparently supported in 6.06, but I'm not having much luck. lsusb shows the device OK ("Bus 001 Device 003: ID 046d:092e Logitech, Inc."), but Camorama tells me "Could not connect to video device (/dev/video0).".  It's right - video0 doesn't exist, but creating it with mknod doesn't appear to make much difference (although I could of course have made a mistake in mknod). Any ideas?

---

### Post by Fitzy_oz on 2007-01-17
> **rajus said:**
> Logitech QuickCam Chat is apparently supported in 6.06, but I'm not having much luck. lsusb shows the device OK ("Bus 001 Device 003: ID 046d:092e Logitech, Inc."), but Camorama tells me "Could not connect to video device (/dev/video0).".  It's right - video0 doesn't exist, but creating it with mknod doesn't appear to make much difference (although I could of course have made a mistake in mknod). Any ideas?

Have you installed the kernel driver for the webcam - It's not supported out of the box unfortunately.  At least it wasn't for me.

Check out [this thread]("http://ubuntuforums.org/showthread.php?t=303330&highlight=logitech+webcam") for instructions on how to install the kernel module.

To save you some time [click here]("http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz") for the driver download

Good Luck :)

---

### Post by rajus on 2007-01-18
Well I loaded spca5xx (and I think dmesg showed me that it had loaded ok), but that had no useful effect. Is the lack of the video0 device caused by the lack of the correct driver in the kernel, or are they two separate problems that have to be solved?

---

### Post by Merlin 3 on 2007-01-20
Hi Rajus...have you had any luck installing this webcam?   I was thinking of installing the same ...

---

### Post by rajus on 2007-01-23
No mate, it's a dud so far. I *presume* if the driver worked then the video0 device would be created and then we'd be in business, in which case I've presumably gone wrong in the driver installation. Dunno for sure tho'.

---

### Post by rajus on 2007-01-25
Thanks Fitzy Oz
Using the driver download that you pointed to built me gspca.ko, which I presume was what was intended. When I try to load it (from the ...usb/media directory (which is where I copied it to)), it says "FATAL: Module gspca not found.".  It has the same permissions all the other modules in there, and they load OK, so I'm baffled.

---

### Post by Doug11 on 2007-01-27
> **rajus said:**
> Thanks Fitzy Oz
Using the driver download that you pointed to built me gspca.ko, which I presume was what was intended. When I try to load it (from the ...usb/media directory (which is where I copied it to)), it says "FATAL: Module gspca not found.".  It has the same permissions all the other modules in there, and they load OK, so I'm baffled.

I get the same error when I try the modprobe comand

---

