---
title: "Sound stopped working"
date: 2008-08-17
forum: Multimedia Software
---

### Post by suprakid24 on 2008-08-17
My sound was working, it would play the little music when I turned it on and everything. I went to play a video I had on my computer and it needed the codec package, so I installed these:

Installed the following packages:
gstreamer0.10-plugins-ugly (0.10.7-3ubuntu1)
liba52-0.7.4 (0.7.4-11ubuntu1)
libdvdread3 (0.9.7-8ubuntu1)
libid3tag0 (0.15.1b-10)
libmad0 (0.15.1b-2.1ubuntu1)
libmpeg2-4 (0.4.1-1)
libsidplay1 (1.36.59-4)

The video played fine, but that's the first time I noticed that I don't have sound anymore. Anyone know what happend?

---

### Post by suprakid24 on 2008-08-18
I tried this [http://ubuntuforums.org/showthread.php?t=892921](http://ubuntuforums.org/showthread.php?t=892921) but it didn't fix it, and I also tried [http://ubuntuforums.org/showthread.php?t=820959&highlight=alsa](http://ubuntuforums.org/showthread.php?t=820959&highlight=alsa) but didn't get very far becuase the folder didn't exist.

---

### Post by gjoellee on 2008-08-18
sometimes your speakers may not be plugged in, you might have forgot to put the sound on. Are you sure you are you are using the right driver...this might have been changed.

Go to System->Preferences->Sound and make sure it looks the same as my configuration does...

---

### Post by suprakid24 on 2008-08-18
thanks for the reply,

I am using a laptop, so my speakers can't come unplugged, and I'm sure my sound is up and not muted. The sound used to work before I installed a codec package for the videos. :???:

---

### Post by suprakid24 on 2008-08-18
did some more searching but still haven't solved it

---

### Post by suprakid24 on 2008-08-18
problem solved, I feel dumb now. 


I didn't know that you had to go to preferences to show all the channels for the speakers -- PCM-2 was muted. I unmuted and tested it and the sound works.

---

### Post by suprakid24 on 2008-08-18
well my sound works still, just not in firefox

---

### Post by eye208 on 2008-08-19
> **suprakid24 said:**
> well my sound works still, just not in firefox
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

### Post by suprakid24 on 2008-08-20
solved thanks to eye208, thanks!

---

