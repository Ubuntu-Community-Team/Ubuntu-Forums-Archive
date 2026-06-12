---
title: "Miscolored DVD and Videos"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by chantron on 2008-03-08
I use VLC for playing dvds and most other videos. 

When I use the XVideo output module the colors are all off, everyone looks purple for example. This goes away when I change to X11 output but then the video looks pixelated which is better than purple but still annoying.

Does anyone have any suggetsions? I should mention that the colors are off in Xine, totem and mplayer as well. 

BTW, when switching to OpenGL, VLC crashes. This is what I see when I open it in a terminal:
```

chandler@chantron:~$ vlc
VLC media player 0.8.6c Janus
[00000298] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
No accelerated IMDCT transform found
[00000342] main private error: option glx-shm does not exist
[00000338] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
No accelerated IMDCT transform found
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  128 (GLX)
  Minor opcode of failed request:  31 ()
  Serial number of failed request:  49
  Current serial number in output stream:  50
chandler@chantron:~$
```

Thanks

---

