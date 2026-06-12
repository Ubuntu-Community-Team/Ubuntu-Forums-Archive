---
title: "ffmpeg does Screencast: Video and Sound"
date: 2009-11-24
forum: Multimedia Software
---

### Post by produnis on 2009-11-24
I just figured out [here]("http://www.michaelphipps.com/using-ffmpeg-do-screen-cast") how to make a screencast with ffmpeg

My MacbookPro4,1 runs a 64bit Karmic Koala

If I type in:
```

ffmpeg -f alsa -i plughw:0 -f x11grab -s 1440x900 -r 24 -b 100k -bf 2 -g 300 -i :0.0 -ar 22050 -ab 128k -acodec libmp3lame -vcodec libxvid -aspect 1.6 -sameq MyScreencast.avi
```...it records my Screen and captures sound via built-in microphone.
Possibly, you need to change the screen size (mine is 1440x900) and the alsa device (for me, plughw:0 is good) 


To stop recording,  just hit "q".

The screencast is saved as a xvid-avi-video-file named MyScreencast.avi.
sound and video are in sync, there are no "running pictures" or any splitted sound.


This is quite good, as I never managed to make screencast which has sound and video in sync using recordmydesktop...

---

