---
title: "user space wintv hvr 950Q"
date: 2016-03-25
forum: Multimedia Software
---

### Post by jabber00 on 2016-03-25
I have written a user space driver using libusb.  I need root privilege to run it.  I am guessing this is because a v4l kernel module has claimed the interface.  If I'm right is there a way to keep the v4l module from being loaded?  I've posted on both the hardware forum and ask ubuntu without getting any replies.  I'm using ubuntu 15.10.

---

### Post by jabber00 on 2016-03-27
From what I've found on the net it may be possible to get rid of the root privilege requirement by adding to the udev rules.  But the information is sketchy and old.   I've tried several rules without luck.  I would appreciate some suggestions on possible rules.  Also is it possible to keep the kernel driver from loading by adding rules.

---

### Post by jabber00 on 2016-03-28
I think I've solved the problem.  Copying a text file with the rule:

SUBSYSTEMS=="usb",MODE="0666" 

and name 99-haup.rules to /etc/udev/rules.d/ seems to have done the trick.

This seems like and overly broad rule but I could not get more specific rules to work.

---

