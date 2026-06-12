---
title: "Natty Mplayer/FFMpeg Missing AC3/DTS Support"
date: 2011-05-31
forum: Mythbuntu
---

### Post by cheuschober on 2011-05-31
Hi.

The Natty build of mplayer / ffmpeg is missing support for AC3/DTS which is a pretty big deal for media-centric applications like myth, especially for those like me who just copy the audio tracks when transcoding from other formats.

A bug report was filed on launchpad but has failed to gain any traction ([https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/750623](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/750623)).

Any hope of getting a proper build in the mythbuntu repositories until / if the ubuntu team picks it up? Even a reversion would be preferable at this stage.

---

### Post by FakeOutdoorsman on 2011-06-01
FFmpeg from the repository supports AC3 decoding. Installing the **libavcodec-extra-52** package will enable support for AC3 encoding in FFmpeg:
```
$ ffmpeg -codecs 2>&1 | grep -i ac3
 DEA    ac3             ATSC A/52A (AC-3)
 D A    eac3            ATSC A/52B (AC-3, E-AC-3)
```

DTS decoding is supported:
```
$ ffmpeg -codecs 2>&1 | grep -i dts
 D A    dca             DCA (DTS Coherent Acoustics)
```

If you want to encoding support as well you will have to compile FFmpeg:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

