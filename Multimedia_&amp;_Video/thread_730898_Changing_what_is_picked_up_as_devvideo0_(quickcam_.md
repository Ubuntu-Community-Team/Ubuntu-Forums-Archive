---
title: "Changing what is picked up as /dev/video0 (quickcam STX)"
date: 2008-03-21
forum: Multimedia &amp; Video
---

### Post by xxchixorxx on 2008-03-21
I have a Logitech Quickcam STX and it works right out of the box with no problems on my laptop.  On my desktop, it will not work.  I am running Ubu 7.10 on both machines.  

I believe the desktop is picking up the TV tuner as /dev/video0 (not compatible with Linux either it seems).  So I rebooted Ubu after unplugging the TV tuner to hope the cam would now be picked up as /dev/video0, but that didn't work.  I tried a few things mentioned in here, but cannot get the desktop to pick up this cam as the correct device.

What can I do to fix this?

---

### Post by peterthebike on 2008-03-21
I think the response to [my problem]("http://ubuntuforums.org/showthread.php?t=730132") may help you.

---

### Post by xxchixorxx on 2008-03-21
All I want to do is have the webcam picked up as video0 so it'll work with Camorama, Skype, Cheese, etc.  Or somehow change where it looks for it, or find out what it is set up as.  In the /dev directory, I only have video0 showing, there is no video1 set up.

---

