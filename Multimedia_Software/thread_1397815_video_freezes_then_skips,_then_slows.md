---
title: "video freezes then skips, then slows"
date: 2010-02-03
forum: Multimedia Software
---

### Post by pickarooney on 2010-02-03
Since upgrading to 9.10 I'm having major playback issues with video files.
SMPLAYER - after abotu 10 minutes the video freezes, then the video skips forward a few seconds in fast motion, then plays with lots of skipped frames. I've set audio to pulse audio and video is set to **user-defined: xv,**

In VLC the sound is terrible, completely choppy and unlistenable. I haven't tested xine or totem enough to see, but the sound appears OK at first glance.

I've uninstalled and reinstalled the 185 and 173 drivers several times, with no discernible improvement.

Should I reformat and revert to Jaunty to make things easier?

---

### Post by pickarooney on 2010-02-04
What video driver should I use for output? Currently it's xv

---

### Post by pickarooney on 2010-02-05
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

---

