---
title: "does mythbuntu need usbfs?"
date: 2008-04-15
forum: Mythbuntu
---

### Post by arjay1 on 2008-04-15
As part of my attempts to get an MS mce keyboard and mouse to work, I have been corresponding with the author of an alternative driver.

He asked me to send him the output of cat /proc/bus/usb/devices.  I found there was no content in /proc/bus/usb.  I then discovered (isn't linux wonderful for expanding your knowledge <g>)  that there was no content because usbfs was not being mounted.

I mounted it and - hey presto - I had the info he needed.

But my question is - is the mounting of usbfs in ubuntu/mythbuntu useful, helpful or what?  It clearly isn't necessary in mythbuntu for normal operation because mine works just fine and it is not mounted by default.  However I do have a couple of usb devices such as a mini-card reader and a microsoft beanbag for the remote etc which are usb devices.

Can anyone enlighten me?  The threads I have looked at in the forum do not appear to help much - they are mainly concerned with running VMware which i don't have.

TIA

---

