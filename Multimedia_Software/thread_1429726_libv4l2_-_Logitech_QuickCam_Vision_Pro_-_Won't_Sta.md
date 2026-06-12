---
title: "libv4l2 - Logitech QuickCam Vision Pro - Won't Start"
date: 2010-03-14
forum: Multimedia Software
---

### Post by bomgd3 on 2010-03-14
I just installed Karmic on my iMac G5, and I must say, congratulations and thank you to all of the devs that have worked hard on this.  I can't believe how good of a release it is, and how complete the repos are.  I originally tried Fedora because PPC is still officially supported, but my experience was horrible--crappy driver support, lots of glitches, buggy install that took 3 tries to complete...  In comaparison, Ubuntu was a dream to set up.

I've got all of my hardware working well except for one thing: My QuickCam Vision Pro won't start up.  It works fine on my Thinkpad also running Karmic, but I don't think this is a PPC-specific bug because I saw others online with the same issue.

Basically, when I start up Cheese, I see the light on my camera turn on and then off, and I get this message in the terminal:

libv4l2: error setting pixformat: Device or resource busy
libv4l2: error requesting 4 buffers: Device or resource busy

Ekiga also does not work, so I think it's an issue with libv4l2.  Has anyone else had this issue?  Could anyone point me in the right direction to resolving it?  It seems like something else is using my webcam, but I'm not sure how to pinpoint the cause.  I tried fuser, but I'm not sure what to query with it.  I didn't get anything back when I did /dev/video0.

luvcview works, by the way.

---

### Post by no2498 on 2010-03-14
not sure this will help you but cheese says to do it
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to, x window system (no xv)
now try v4l1 and v4l2 click the bottom test button for each 1

wxcan may give you a better frame rate

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)
it comes in a deb if you like

---

### Post by bomgd3 on 2010-03-15
Thanks.  The v4l test didn't work at all, it said "could not get/set settings from/on resource".  The v4l2 test worked perfectly fine.  Seems to be a Cheese bug, not a v4l2 one.  wxcam doesn't seem to be available for PPC.  luvcview seems to be pretty decent even though the GUI is crappy and the image capture is buggy.  Are there any good image/video capture alternatives out there?  I don't really care about special effects or anything, I just want to be able to conveniently use my webcam.

Ekiga seems to be able to connect to /dev/video0, but the picture doesn't work...  very confused!

---

