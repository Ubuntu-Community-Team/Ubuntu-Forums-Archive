---
title: "[SOLVED] problems with video output driver (i.e X11 XV)"
date: 2008-08-05
forum: Multimedia Software
---

### Post by El Conquistador on 2008-08-05
ok so while i was having trouble playing .rmvb files i started doing some research and found a couple "fixes". so i installed SMplayer and i noticed that the video was kinda bright and blurry and apparently its because it was using the XV driver but it played my .rmvb files which was strange to me since it is only a front end to Mplayer and Mplayer refused to play the files. so then i went to Mplayer and started messing with the settings in that now all my videos play the same ugly way SMplayer played them. i went back to X11 and that seems to have fixed the uglyness but now i cant watch my videos in full screen mode. to make things worse it seems that this affeted all my players because Totem, VLC, do the same thing, along with Mplayer (SMplayer)

so my question is how do i go back to how it was before? / what is the default setup? 

if possible maybe someone can tell me what i did wrong?

As always all help is apreciated!

---

### Post by rvm4000 on 2008-08-05
smplayer when plays a video sets the contrast, brightness, hue and saturation to 0, which should give a normal image, but some people have reported that that actually produces a very bright or contrasted image (maybe because of a problem/bad configuration in xv?).

There are several ways to fix this:

* open the video equalizer and adjust the controls until the image is ok, and then click on the "Set as default values" button

* edit the config file (~/.smplayer/smplayer.ini), look for **dont_use_eq_options** and set it to true. That'll prevent smplayer to use the -brightness, -contrast... options.

* install the latest version from svn ([ftp://ftp.berlios.de/pub/smplayer/ubuntu/](ftp://ftp.berlios.de/pub/smplayer/ubuntu/))

---

### Post by El Conquistador on 2008-08-05
> **rvm4000 said:**
> smplayer when plays a video sets the contrast, brightness, hue and saturation to 0, which should give a normal image, but some people have reported that that actually produces a very bright or contrasted image (maybe because of a problem/bad configuration in xv?).

There are several ways to fix this:

* open the video equalizer and adjust the controls until the image is ok, and then click on the "Set as default values" button

* edit the config file (~/.smplayer/smplayer.ini), look for **dont_use_eq_options** and set it to true. That'll prevent smplayer to use the -brightness, -contrast... options.

* install the latest version from svn ([ftp://ftp.berlios.de/pub/smplayer/ubuntu/](ftp://ftp.berlios.de/pub/smplayer/ubuntu/))

Hey thank you very much!!! that fixed the ugly contrast. now i might actually consider trying out SMaplyer...i thought it just sucked! lol

as for my other problems after much googling they are now fixed. Thanks again!

---

