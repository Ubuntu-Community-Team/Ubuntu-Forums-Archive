---
title: "Trying to get Canon Rebel XT 350D to talk to Edgy"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by pspotts on 2007-01-03
Folks,

I'm trying to get my new Canon Rebel XT 350D to play with Edgy. I've checked a couple of threads, with no success. USBView sees the camera, as does gthumb. Gthumb gives me the correct camera button when I select File=>Import.

But I also get an error message: 

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to this device.

So:

1. How do I test to make sure those kernel modules are not the problem?
2. How do I ensure I have read/write access to a device that Edgy can't claim?
3. And what is interface 0 anyway?

Thanks in advance for any light anyone can shed on this...

Pete

---

### Post by WillCooke on 2007-03-10
Hi,

I've got/had the same problem.  It used to work perfectly on Dapper, but now seems to be broken with the camera in both PTP and PC mode.

In the end I got a cheapo 7 in 1 card reader and used that to get the pictures on to the computer, with the added benefit of not needing any charge in the camera.

Sorry I can't help fix your problem, but at least you've got a work around.

Cheers, Will

EDIT:  A bit more searching found this post:

[http://ubuntuforums.org/showthread.php?t=375010](http://ubuntuforums.org/showthread.php?t=375010)

which should fix it.

---

### Post by pspotts on 2007-03-10
Thanks Will. I broke down and bought a 4-in-1 with CFI and II capability a couple of weeks ago...ah, the workarounds!

Pete

---

### Post by dist0rtedwave on 2007-03-18
The above link failed for me.  What worked was downgrading libgphoto2-2 and libgphoto 2-port0 in synaptic (package->force version).

Hope that helps if you are still playing with this.

---

### Post by kemalcakmak on 2007-03-22
I have also the same problem. How long you guess that it will be fixed?

---

### Post by h0ax on 2007-03-30
Just fixed the problem guys
There's a bug on it where you need to go in a file and change a line

go to
> gksudo gedit /etc/udev/rules.d/45-libgphoto2.rules

change the line (Line #3)
> 
BUS!="usb*", GOTO="libgphoto2_rules_end"

change this to 
> 
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"


Fixed my problem with 350D

---

