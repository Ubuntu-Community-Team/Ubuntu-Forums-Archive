---
title: "warning error when disconnecting camera"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by vbdanl on 2007-11-01
Hi.  First, let me say a BIG THANKS to all the Ubuntu developers and supporters.  It is a great linux distro, and keeps getting better.
I recently ran into a snag with my digital camera.  I am running Feisty 7.10 and also Celena.  An older version of Ubuntu worked perfectly with my sony camera.  With these versions, gthumb doesn't even pop up when i plug it in.  After a lot of searches, I finally found this [link]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/91250") that talks about usb problems, and ways to solve them.
I ended up installing gthumb and updating the file /etc/udev/rules.d/45-libgphoto2.rules as indicated in the above link.  Now gthumb pops up, and I can import the pictures.  Only problem is after I close the window with the pictures, then turn off or disconnect the camera, I get the error warning message about it is unsafe to unplug the camera, etc. 
It works to umount the /dev/media/sda1 (or whatever it was mounted as) before turning it off.  I was wondering if there is a script I can update that will automatically do the umount when I close the window that contains the pictures?

---

