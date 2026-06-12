---
title: "Is nouveau Xorg driver really this lame?"
date: 2010-11-30
forum: Multimedia Software
---

### Post by wkulecz on 2010-11-30
When I first installed 10.04 the nouveau Xorg driver installed by default for my Nvidia graphics had obvious visual problems so I installed the proprietary drivers and never looked back.  Doing another fresh install on a MB with built in Nvidia graphics everything seemed to work fine after all the updates, so I was thinking:  Great! The nouveau driver has been fixed or at least works on this older Nvidia chip.

But then I tried to use my video capture card.  Neither TVtime or XawTV would work.  Starting them in a terminal suggested the Xvideo extensions were not there :(

Installing the proprietary drivers cured the issue, again.

---

### Post by .... on 2010-11-30
[http://nouveau.freedesktop.org/wiki/XVideoStatus](http://nouveau.freedesktop.org/wiki/XVideoStatus)
Reverse-engineering ***** isn't easy, so don't knock the nouveau devs, who have Xv working for GeForce 6k cards and earlier, and are rapidly making progress on their driver. Thanks for this thread, though. Apparently, you like the nvidia binary driver. Very informative..

---

### Post by wkulecz on 2010-12-01
Thanks for the info.

I'm looking into using an RTAI patched kernel so obvioulsy binary drivers would be an issue.  I found the emc2 project which has a Ubuntu 10.04 liveCD with RTAI kernel.  It used nouveau as default for my system and seemed to work very well until I tried to do video capture.

I found a work around, I can use gstreamer to get the video and output it to its ximagesink for display.  Seems to work OK, but the capture/display program and Xorg process seems to take ~3X the cpu compared to using the binary drivers and xvimagesink.  Since I need two realtime video channels this could be a showstopper issue, unless we decide dual core is an acceptable minimum system requirement.

I've still got to learn more about RTAI to see if the whole scheme I have in mind is really viable or not.  The RTAI docs are not very good IMHO, so I'd have not even tried this approach had it not been for stumbling onto the emc2 project.

---

### Post by amauk on 2010-12-01
Nouveau has made astounding progress IMO

In 3 years, they've gone from nothing to now...

- Nouveau out performs & out-features nvidia's own 2D "open driver", so much so that nvidia have dropped their 2D driver

- 3D acceleration is available on most cards

Compiz works fine with Nouveau, but openGL games are still an issue
Nouveau's currently a lot slower than the binary blob for 3D acceleration, but it's getting closer with each iteration

Wine took 10 years of development before it became really usable
Apples & oranges I know, but still reverse engineering

---

