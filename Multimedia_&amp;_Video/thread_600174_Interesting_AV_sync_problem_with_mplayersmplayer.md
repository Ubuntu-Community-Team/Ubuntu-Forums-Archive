---
title: "Interesting A/V sync problem with mplayer/smplayer"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by FG123 on 2007-11-02
I have one video file, just one, which has this problem. I'm guessing it's related to how it was encoded, but I never saw this problem elsewhere, even on Windows.

What happens is, whenever the file is played through mplayer, smplayer or totem for that matter with the gstreamer codecs, after a few seconds of playback the audio and video are out of sync by about 600 ms. Also, if you seek to any point in the file, the A/V are resynced, but after about two seconds they fall back into a 600 ms delay, no matter where you seek to in the file.

Since this is only with one file and it's rare enough, the easy solution is when using smplayer, just to hit the minus key six times to delay the audio by 600 ms, forcing the sync myself, since the delay is consistant through the film. So, when seeking the situation becomes reversed - it's immediately out of sync for 2 seconds and they can be watched perfectly because it remains in sync due to the forced delay.

WTF could be causing this?

---

### Post by Light- on 2007-11-02
The encoder may have been drunk, or the file didnt mux properly, You could try and demux/remux and see if that fixes it

---

### Post by disturbed1 on 2007-11-02
As above, a simple remux might fix the problem. Most likely the avi index is corrupted.

Use Avidemux, or *mencoder yourfile.avi -ovc copy -oac copy -o yournewfile.avi*

---

