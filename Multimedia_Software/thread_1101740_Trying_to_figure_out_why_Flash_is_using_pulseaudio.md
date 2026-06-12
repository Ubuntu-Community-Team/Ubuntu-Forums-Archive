---
title: "Trying to figure out why Flash is using pulseaudio server"
date: 2009-03-20
forum: Multimedia Software
---

### Post by itsJim on 2009-03-20
Ok, so I've got a file server that I was trying to setup mpd/pulseaudio with. After never being able to get any sound to my desktop I decided to say '**** it' and set all my sound settings back to alsa.

A few days later I was trying to watch some flash videos in firefox and I wasn't getting sound. I fired up totem and played a few flac albums just fine.

I've been trying to get flash to work for about an hour now and figured that pulse had something to do with it even though my sound settings say I should be using alsa for everything. Eventually I set my sound server to localhost instead of my file server, restarted firefox, and everything started working.

I checked for an ~/.asoundrc and /etc/asoundrc and none exist. I don't see anywhere to change audio options from within flash. Anyone have any ideas why I'm using pulseaudio for only my flash videos?

---

### Post by cygnusx4 on 2009-03-22
i've a similar problem. mpd runs fine until some flash app starts running. one minute later mpd stops playing and won't resume until x is restarted. then it works fine. until some app starts running...
any help would be greatly appreciated.

---

### Post by zika on 2009-03-22
System->Preferences->Sound->Devices->Music and Movies->Alsa ?

---

### Post by neu2buntu on 2009-03-22
another possibility ... open terminal do code ```
gstreamer-properties
``` and change settings here to alsa

---

### Post by cygnusx4 on 2009-03-22
tried it. didn't work.

---

