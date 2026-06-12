---
title: "Streaming Webcam Video w/ Data Overlay"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by Jivicin on 2007-07-11
I'm having some issues getting ffmpeg, mplayer, and my webcam to all play nice.

First off, I was successful getting ffmpeg to grab video from my webcam and dump it to an avi.  I'm trying to overlay the current webcam feed with text before I display it to the screen (e.g. date and time info).  I was able to use the video hooks with the latest release of ffmpeg and these guides to create a video with the information:

[http://ffmpeg.mplayerhq.hu/hooks.html](http://ffmpeg.mplayerhq.hu/hooks.html)
[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/)

Unfortunately, I haven't found anyway to get the "live" video with the overlay to mplayer.  There is no way to redirect ffmpeg's output.  The best I can do is save the video with the overlay (as a .mpg) and then open it with mplayer. This is still about a 15 second delay.

I was wondering if anyone had a better solution on overlaying live webcam feeds with data?

---

