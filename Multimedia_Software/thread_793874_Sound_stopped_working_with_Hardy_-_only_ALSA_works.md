---
title: "Sound stopped working with Hardy - only ALSA works"
date: 2008-05-14
forum: Multimedia Software
---

### Post by ad_267 on 2008-05-14
I've been having weird problems with my sound. Everything has been fine and I've been using Hardy for a few weeks now but all of a sudden I'm having problems.  I've had a look around and there seems to be a few people having sound problems in Hardy and I've switched to using ALSA and everything seems to be working OK now.

What's happening is that if I boot into Ubuntu and play a song in rhythmbox then everything works fine and I can watch a video in Youtube and VLC but at some point all sound just stops working. If I switch everything to ALSA instead of auto detect or pulse audio then everything works fine. I guess I'm not exactly looking for a solution because I can use ALSA but I was wondering if this is a bug that is expected to be fixed soon or if there is some other reason that pulse audio isn't working that would fix this.

---

### Post by markbuntu on 2008-05-15
I had a similar problem. If I go into Sound Preferences and change from autodetect to anything it will freeze my system but would keep the change. Eventually I got it switched to ALSA and all my sound now works after some fiddling with the gnome alsa mixer. The alsamixergui does not have as many options as the gnome alsa mixer and once I enabled everything in the properties menu it all worked. Pulse audio still works though through ALSA, everything must go through ALSA.

I guess that ALSA is now the supreme emperor of the sound environment in Ubuntu.

---

