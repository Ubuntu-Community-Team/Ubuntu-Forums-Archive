---
title: "problem converting video with ffmpeg"
date: 2009-09-15
forum: Multimedia Software
---

### Post by ApEkV2 on 2009-09-15
I can't get ffmpeg to convert mp4 video to mp3 sound anymore.
Since I installed Jaunty, it creates an empty output file.

Any other way to separate audio from video other than ffmpeg?

Here's the command:

[color=red] ffmpeg -i '/home/mccarty/dwhelper/Trance/Firewave - Sky Blue.mp4' -vn -ac 2 -ab 320000 audio1.mp3 [/color]

Here's the output:

[color=blue] Seems stream 1 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/mccarty/dwhelper/Trance/Firewave - Sky Blue.mp4':
  Duration: 00:04:58.63, start: 0.000000, bitrate: 212 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x270, 23.98 tbr, 23.98 tbn, 47.95 tbc
Output #0, mp3, to 'audioFire.mp3':
    Stream #0.0(und): Audio: 0x0000, 44100 Hz, stereo, s16, 320 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0 [/color]

---

### Post by FakeOutdoorsman on 2009-09-15
You need to enable restricted encoders in FFmpeg.  Follow section "B" of this guide:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Now for the command to convert the AAC audio to MP3:
```
ffmpeg -i '/home/mccarty/dwhelper/Trance/Firewave - Sky Blue.mp4' -ab 192k output.mp3
```

You can also copy the audio stream without re-encoding by using "-acodec copy", but it will stay the same format as the original:

```
ffmpeg -i '/home/mccarty/dwhelper/Trance/Firewave - Sky Blue.mp4' -acodec copy output.aac
```

---

### Post by ApEkV2 on 2009-09-15
Yup just got the ubuntu-restricted-extras downloaded and installed now it's working fine.  Thanks solved

---

