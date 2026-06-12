---
title: "Yet another webcam thread (works, but not in Skype)"
date: 2010-10-12
forum: Multimedia Software
---

### Post by uziel on 2010-10-12
After hours of looking for a solution I decided to write about my problem, although lots of similar have been posted on this and other forums.

I have a cheap webcam with device ID 0ac8:3420. Under Karmic, it responded properly to the test in gstreamer-properties, worked as expected with Cheese, and even with Gmail Video Chat (in-page). [Digression: surprisingly, the video feed was correctly captured by the application and transmitted to the other users who have seen me, I did not see anything, however - this must have been some trouble with displaying the video in my configuration.] However, it failed to cooperate with Skype (see below for details).

After an upgrade to Maverick (via Lucid) things are almost the same (gstreamer-properties zoom in ridiculously, but who cares; video display in Google Chat works, so I can at least use this app). Skype still fails in the following manner: when I attempt to do a video chat with someone (or do a video test), Camera Monitor says that "Camera is On", but instead of a view on myself I get a blank gray rectangle.

Most common workarounds, like running skype with LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so or LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so do not work, the same with medibuntu (or other unofficial) skype packages. What I have now is a clean install of skype (from partner repo) after purging some other version of skype and skype-common.

What may be interesting, the webcam DID WORK with skype a few Ubuntu updates ago (possibly with some workarounds). That was a year and a half ago, but I can't tell if I had the most recent (ie. Hardy) version installed. (I just can guess I did, as it was an LTS.)

---

### Post by mtopro on 2010-10-14
uziel
I had the same issue on 64bit.  Think that could be the problem?  The solution was the path to the 32bit libraries and that can be found here:
[http://ubuntuforums.org/showthread.php?t=993262&page=4](http://ubuntuforums.org/showthread.php?t=993262&page=4)
Hope that helps!

---

### Post by uziel on 2010-10-17
Umm, yeah, I should have probably mentioned that I have a 32-bit system. I have seen that thread already, too. Thanks for help nonetheless.

---

