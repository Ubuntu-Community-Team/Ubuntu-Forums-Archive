---
title: "No video mplayer, only audio. VLC works"
date: 2011-10-13
forum: Multimedia Software
---

### Post by FLCL on 2011-10-13
mplayer, and smplayer front-end do not display any video. I have tried every single codec option available and **none** give video. These are the errors I receive when loading a video in mplayer:
```
Too many buffered pts
[h264 @ 0xb68a7e20]AVC: nal size 2710337
[h264 @ 0xb68a7e20]no frame!
Error while decoding frame!
Too many audio packets in the buffer: (4101 in 2511707 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

```
The errors are repeated a ton of times, this is just the slimmed down version.
VLC works fine though. VLC uses "default" for video output

---

### Post by linux_burner on 2011-10-14
I am having the same problem as well...no front-end video on Totem (didn't try mplayer), but works well in VLC.

I really use Totem for its WMP type of interface (adding videos in to playlist on the go). Please help us trouble shoot this issue.

Thx,
- B

---

### Post by FLCL on 2011-10-16
yeah, vlc works but isn't great with subtitles and has issues with some encodes. I was using mplayer before the upgrade

---

### Post by SeijiSensei on 2011-10-17
Give [mplayer2](http://www.ubuntugeek.com/install-mplayer2-on-ubuntu-using-ppa.html) a try and see if it helps.

---

