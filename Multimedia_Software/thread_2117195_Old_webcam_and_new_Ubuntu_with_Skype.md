---
title: "Old webcam and new Ubuntu with Skype"
date: 2013-02-17
forum: Multimedia Software
---

### Post by def_mornahan on 2013-02-17
I did a lot of googling to try to fix this problem myself without finding it, so I'm putting this out there in case it helps anyone else speed up the process.

I have a Logitech QuickCam Express (lsusb ID 046d:0840 ).  It's older than dirt.  Meanwhile, I'm running Quantal / 12.10 with GNOME.  I plugged the camera in, installed skype, and like a fool, expected it to work.  No image on the video device screen.  For some reason Cheese is fatally broken on my system.  I google and find the Ubuntu webcam page and try:

vlc v4l2:///dev/video0

Now this works.  So I root around some more and find a page that tells me to try

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

I'm told this can't be preloaded.  I install v4l-utils (and you should too) but this doesn't fix the problem.  After a lot of googling and trying different things like gstfakevideo, which I cannot even get to compile on my system, I decide to investigate whether this path even exists.  Lo and behold, someone has moved things around and the proper path is now

LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so

So either export this or write a script to run skype with that environment variable.  Also, the above is what you want, not x86_64-linux-gnu and not v4l2convert.so.

---

