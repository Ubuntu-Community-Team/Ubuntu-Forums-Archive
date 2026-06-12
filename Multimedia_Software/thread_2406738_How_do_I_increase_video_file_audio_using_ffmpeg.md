---
title: "How do I increase video file audio using ffmpeg"
date: 2018-11-24
forum: Multimedia Software
---

### Post by jacatone on 2018-11-24
Been trying to figure out how to increase a video file's audio without re-encoding the file using ffmpeg. Created a test file called "test".

jacatone@OptiPlex-755:~/Downloads$ ffmpeg -i test -hide_banner
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'test':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    encoder         : Lavf58.12.100
  Duration: 00:29:08.44, start: 0.011000, bitrate: 1405 kb/s
    Stream #0:0(und): Video: h264 (High) (avc1 / 0x31637661), yuv420p, 800x450 [SAR 1:1 DAR 16:9], 1271 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc (default)
    Metadata:
      handler_name    : VideoHandler
    Stream #0:1(und): Audio: aac (LC) (mp4a / 0x6134706D), 48000 Hz, stereo, fltp, 127 kb/s (default)
    Metadata:
      handler_name    : SoundHandler
At least one output file must be specified

---

### Post by Yellow Pasque on 2018-11-25
Increase/Raise the volume? Or are you talking about something else?

---

### Post by SeijiSensei on 2018-11-25
You mean increase the playback volume? I don't see how you could change the volume of an existing audio file without re-encoding.

For playback you need to look at your audio settings.

---

### Post by TheFu on 2018-11-25
There is a gain setting in some file format headers that can be modified, but it is highly dependent on the specific audio encoder involved.  For example, [http://mp3gain.sourceforge.net/](http://mp3gain.sourceforge.net/) and [https://sjeng.org/vorbisgain.html](https://sjeng.org/vorbisgain.html)

Perhaps I misunderstand the goal?

---

### Post by jacatone on 2018-11-25
My goal is to find a terminal command or program to just increase a video file's volume without re-encoding the whole file. Then I can play the file using a media player on my TV.

---

### Post by viewera on 2018-11-25
[https://trac.ffmpeg.org/wiki/AudioVolume]("https://trac.ffmpeg.org/wiki/AudioVolume")

---

### Post by TheFu on 2018-11-25
> **jacatone said:**
> My goal is to find a terminal command or program to just increase a video file's volume without re-encoding the whole file. Then I can play the file using a media player on my TV.

And both those links should do that, if the audio files are in the correct format using the supported codecs.

---

### Post by dinkidonk on 2018-12-02
You need to re-encode the audio if you want to change the volume, this should increase the volume by 50% (or multiply volume by 1.5):

```
ffmpeg -i video.mp4 -af "volume=1.5" -c:v copy -c:a audio-codec video_louder.mp4
```

---

