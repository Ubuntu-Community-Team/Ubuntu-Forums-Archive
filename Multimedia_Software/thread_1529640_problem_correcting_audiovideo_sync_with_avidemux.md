---
title: "problem correcting audio/video sync with avidemux"
date: 2010-07-12
forum: Multimedia Software
---

### Post by andrewthomas on 2010-07-12
I have a video of a tv show that has audio/video sync issues.  It is not consistent, but varies after each commercial break (where it was cut/paused.) What I have done is split (with avidemux) the video up into segments that have different offsets of audio and video, and "fixed" by shifting the audio. Then I appended them all back together ( again using avidemux.) When I play back the file using avidemux, the audio and video are in sync.  However when I open up the file with totem or vlc the audio and video are not in sync.  

  ```
 Duration: 01:00:21.08, start: 0.000000, bitrate: 1412 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x368 [PAR 1:1 DAR 40:23], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 128 kb/s
```How can I get the audio to sync properly so I can play with a "regular" video player?
My end goal is to burn the synced file to DVD so I can watch it on a TV.

---

### Post by andrewthomas on 2010-07-14
Well, I got it to work, although I still don't understand why it was not working from the beginning.  I found that when playing back the files in totem, that I shifted the audio with avidemux, there was now a constant difference, whereas originally it was variable.  So, I loaded the segments in avidemux and found that if I now shifted the audio +250ms and saved with the video on copy and the audio on mp3(lame) into the avi container I could play the videos with sync in totem and vlc. For an unknown reason, I was unable to transcode the resulting file to a dvd suitable format using the Auto > Optical Disc > DVD presets, as it was resulting in a segfault.  So, I used Winff which worked perfectly.

---

