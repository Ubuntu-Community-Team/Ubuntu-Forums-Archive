---
title: "DVD and movie-file playback errors"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by gjones on 2007-05-07
When I try and play movies and DVDs with either xine-ui, totem (-gstreamer and -xine) and vlc, I get the following error:

X Error of failed request:  BadAlloc (insufficient resources for operation)

(when run from the CL. The gui just crashes out).

I'm not sure when this stopped working, but I have been able to play movies and DVDs in the past, and I'm fairly sure it's not a codec issue- the error message certainly doesn't suggest it would be.

I've found people with the same error message asking for help, but none of the solutions that seemed to work for them help me, or they're using different hardware that newer drivers fix.

I found a help-message elsewhere with a response that suggested adding

 Option          "VideoRam"      "65536"
 Option          "CacheLines"    "1980"

to my xorg.conf. After doing that, some of the movie files I've been trying will now play, but only in Totem, and other files, and DVDs still give the error. This makes me think that this is at least along the right lines, but I don't really see why it would need more than 64MB shared memory to play DVDs...am I wrong?

I'm using a Matrox G450 graphics card, with the standard xserver-xorg-video-mga driver from the repositories- "mga" in my config file. It's a dual-head card, but I have it setup with just one monitor

Any suggestions?

---

