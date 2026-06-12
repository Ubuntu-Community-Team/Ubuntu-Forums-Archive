---
title: "Forcing default values in gstreamer at startup?"
date: 2012-08-13
forum: Multimedia Software
---

### Post by geekymaestro on 2012-08-13
AFAIK this question has not been posted before and I would appreciate someone's help with it.  I am a bit of a noob but I've used/installed Ubuntu before so I felt bad about posting in the AB section.

I'm running Ubuntu 12.04 LTS 64-bit on an AMD platform.  In my box I have a Sound Blaster X-Fi Titanium which at first didn't work.  I searched the forums and found the gstreamer-properties command which was extremely helpful in getting sound to work.  I normally select the ALSA plugin and then have to make sure the device is set to "Front/Wave In".  In case you were wondering the pipeline is alsasink device="hw:0,0".  

My problem is that if I don't manually go into gstreamer-properties at every boot up and set these values (other than the pipline which doesn't change), my sound card won't work, and doesn't even appear in "sound settings".

Is there a way I can set these values as default so I don't have to manually configure them at every boot?  Thanks!

---

