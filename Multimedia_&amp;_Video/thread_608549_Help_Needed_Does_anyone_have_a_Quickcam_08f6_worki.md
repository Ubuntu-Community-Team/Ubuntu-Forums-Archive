---
title: "Help Needed: Does anyone have a Quickcam 08f6 working in Gutsy?"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by Limulus on 2007-11-10
Trying to help my neighbor's family; I got them using Ubuntu (hurrah! :) and they wanted a webcam.  I suggested Logitech; coincidentally there was a nice sale on at a local store where you could get a Logitech "BuddyCam" two pack for $30.  So I bought it for them and they will pay me back... assuming I can get them working.  And that's the catch ^_-;  So perhaps someone can help me.

```
$ lsusb 
[...]
Bus 004 Device 013: ID 046d:08f6 Logitech, Inc.
```

[http://home.mag.cx/messenger/](http://home.mag.cx/messenger/) identifies them as "Quickcam Messenger Plus"  For the life of me though, I can't seem to compile a kernel module from that or any other source (e.g. the qc-usb-source package) which works on Gutsy.

Has anyone out there gotten a 046d:08f6 to work on Gutsy?  If so, what method did you use? A walk-through would be appreciated if possible :)

---

### Post by acturneruk on 2007-11-12
I got mine working by following this thread:-

[http://ubuntuforums.org/showthread.php?t=191770](http://ubuntuforums.org/showthread.php?t=191770)

However, the colour is screwed up in Camorama, and it doesn't seem to work with the new beta version of Skype with video support for Linux.

---

### Post by Limulus on 2007-11-13
I followed the basic instructions from the thread (running quickcam.sh from qc-usb-messenger-1.7 as root).

Eventually got an error that qcset couldn't find the camera.

Ran sudo make install and I ended up with:

/lib/modules/2.6.22-14-generic/misc/quickcam.ko
/usr/local/bin/qcset

sudo modprobe quickcam
seems to work since lsmod returns:

Module                  Size  Used by
quickcam              110920  0
[...]

However, Camorama says "Unable to capture image"

Ubuntu's Multimedia Systems Selector complains that it "Could not synchronize on resource"

Which is how far I got last time :(

Any specifics of what I might be doing wrong?

Does it work for you with the "cheese" package?

Edit: running the script with the changes in [http://ubuntuforums.org/showthread.php?t=191770&page=4](http://ubuntuforums.org/showthread.php?t=191770&page=4) makes no difference :(

---

### Post by jeromio on 2007-11-14
This won't be helpful, but I had a very old Logitech QuickCam that worked great in Feisty and doesn't work at all in Gutsy. It shows up in the list of attached USB devices, but as Unknown (0x46D).

This is on the same system - upgraded from Feisty to Gutsy, rebooted and webcam no longer works....

---

### Post by Limulus on 2007-11-15
> **jeromio said:**
> This won't be helpful, but I had a very old Logitech QuickCam that worked great in Feisty and doesn't work at all in Gutsy. It shows up in the list of attached USB devices, but as Unknown (0x46D). This is on the same system - upgraded from Feisty to Gutsy, rebooted and webcam no longer works....

0x46d is Logitech; if you run lsusb, what is the output?

---

