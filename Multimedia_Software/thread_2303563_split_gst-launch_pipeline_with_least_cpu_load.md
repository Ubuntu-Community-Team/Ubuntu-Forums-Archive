---
title: "split gst-launch pipeline with least cpu load"
date: 2015-11-19
forum: Multimedia Software
---

### Post by dave_anderson2 on 2015-11-19
For my on-going videomixer project, I use Blackmagic decklink SDI capture cards to capture 1080 video, with the following:

```
/usr/bin/gst-launch-1.0 decklinksrc mode=9 connection=0 device-number=0 ! v4l2sink device=/dev/video0
```

I have my video now in a v4l2 source and link it to the mixer program. I also need to preview the video, and I can do so with mplayer or vlc, but latency and CPU usage are issues, and my framerate drops off. So I played with gstreamer..... as follows:

```
gst-launch-1.0 videotestsrc ! tee name=t ! queue ! v4l2sink device=/dev/video0 t. ! queue ! autovideosink
```

which works with a nice test pattern on a resizeable window, and output to v4l2. Combining the two does NOT work:

```
gst-launch-1.0 decklinksrc mode=9 connection=0 device-number=0 ! tee name=t ! queue ! v4l2sink device=/dev/video0 t. ! queue ! autovideosink
WARNING: erroneous pipeline: could not link queue0 to v4l2sink0
```

Granted, I'm dealing with 1080, so therein may be the issue, but I don't understand the error.

---

