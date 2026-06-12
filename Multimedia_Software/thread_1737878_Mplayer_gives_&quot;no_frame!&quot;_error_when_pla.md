---
title: "Mplayer gives &quot;no frame!&quot; error when playing H264"
date: 2011-04-24
forum: Multimedia Software
---

### Post by Luke has no name on 2011-04-24
ubuntu natty 64 bit with official NVidia drivers. Installed SMPlayer and vdpau-va-driver, set SMPlayer to use vdpau.

I can't play some ffh264 files. I get a "No frame!" error in the mplayer output. These files all played in Maverick. Any ideas?

---

### Post by coolercooler on 2011-04-24
Think this might be the problem with current ffmpeg, I had and older version which works a bit better with x264.  Try an older version of ffmpeg if you can get it.

Are you getting errors like this

```
[h264 @ 0x9d6e420] illegal short term buffer state detected
[h264 @ 0x9d6e4a0] mmco: unref short failure
[h264 @ 0x9d6e4a0] mmco: unref short failure
[h264 @ 0x9d6e4a0] reference picture missing during reorder
[h264 @ 0x9d6e4a0] Missing reference picture
[h264 @ 0x9d6e4a0] reference picture missing during reorder
[h264 @ 0x9d6e4a0] Missing reference picture
[h264 @ 0x9d6e4a0] reference picture missing during reorder
[h264 @ 0x9d6e4a0] Missing reference picture
[h264 @ 0x9d6e4a0] reference picture missing during reorder
[h264 @ 0x9d6e4a0] Missing reference picture
[h264 @ 0x9d6e4a0] reference picture missing during reorder
[h264 @ 0x9d6e4a0] Missing reference picture
[h264 @ 0x9d6e4a0] reference picture missing during reorder
[h264 @ 0x9d6e4a0] Missing reference picture
[h264 @ 0x9d6e4a0] mmco: unref short failure
[h264 @ 0x9d00810] mmco: unref short failure
[h264 @ 0x9d00810] mmco: unref short failure
[h264 @ 0x9d00810] mmco: unref short failure
[h264 @ 0x9d00810] mmco: unref short failure
[h264 @ 0x9d00810] Missing reference picture
[h264 @ 0x9d00810] Missing reference picture
[h264 @ 0x9d00810] Missing reference picture
[h264 @ 0x9d00810] Missing reference picture
[h264 @ 0x9d00810] Missing reference picture
[h264 @ 0x9d00810] Missing reference picture
[h264 @ 0x9d00810] mmco: unref short failure
[h264 @ 0x9d00810] mmco: unref short failure

```

---

### Post by Luke has no name on 2011-04-24
No. Its main error is
```

[h264 @ 0x7f4187913120]AVC: nal size 9793
[h264 @ 0x7f4187913120]no frame!

```

When I play the video using VLC, it seems to work. Note that VLC isn't set up to use VDPAU; could this be an issue? What about new X server and nvidia driver versions?

---

