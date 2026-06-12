---
title: "VLC and wmv3 codec"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by raeb on 2007-05-06
I'm having trouble as to why VLC won't play this avi.  It uses the Windows Media Video 3 codec (for wm9 I'm guessing?).  I have the w32codecs installed and did a bit of googling but came up with nothing usefull.  Is there something I'm missing?

```
VLC media player 0.8.6 Janus
[00000303] ffmpeg decoder error: cannot open codec (Windows Media Video 3)
[00000303] main decoder error: no suitable decoder module for fourcc `WMV3'.
VLC probably does not support this sound or video format.
[00000280] main playlist: stopping playback
```

---

### Post by skipo on 2007-05-10
I'm having the same problem.

From [www.videolan.org:](www.videolan.org:)

> WMV-3 / WMV-9 / VC-1 playback will be available through the FFmpeg-library in VLC 0.8.6. It is already enabled in the nightly builds. The playback of some videos can still be problematic due to the pre-beta nature of the decoder.

Can anyone tell what this FFmpeg-library is? I have the w32codecs and gstreamer0.10-ffmpeg installed.

---

### Post by raeb on 2007-05-11
Seems like we're just going to have to wait until the program gets updated  :(

---

### Post by skipo on 2007-05-11
I tried to play the file with mplayer and it worked perfectly. Maybe you should try that.

---

### Post by raeb on 2007-05-12
> **skipo said:**
> I tried to play the file with mplayer and it worked perfectly. Maybe you should try that.

MPlayer works fine.  However searching through the movie isn't as smooth, and watching the video windowed only allows for one size  (vlc lets you resize the actual movie image during playback).

---

