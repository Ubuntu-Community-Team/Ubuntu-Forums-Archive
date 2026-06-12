---
title: "ffmpeg to resample audio but leave video unchanged"
date: 2010-03-01
forum: Multimedia Software
---

### Post by sojyujai on 2010-03-01
I'm trying to write a bash script for gpodder to automatically convert video podcasts to play on my media player.  I'm using ffmpeg for the conversions (compiled myself with all codecs enabled).  

I'd like to avoid resampling the video or audio whenever it's unnecessary but ffmpeg seems to want to resample my video even if I only give it audio parameters to change.

For example I have a test video with the following parameters:
```
Stream #0.0(eng): Video: h264, yuv420p, 640x480, 1394 kb/s, 29.97 fps, 29.97 tbr, 2997 tbn, 5994 tbc
Stream #0.1(eng): Audio: aac, 44100 Hz, stereo, s16, 159 kb/s
```

I'd like to change the audio to mp3 but not change the video so I try this command:
```
ffmpeg -i test.mp4 -acodec libmp3lame -ar 44100 -ab 64000 -ac 2 test_mp3_audio.mp4
```

with no options for the video.  But what ffmpeg outputs is a video with the following parameters:
```
Stream #0.0(eng): Video: mpeg4, yuv420p, 640x480, q=2-31, 200 kb/s, 30k tbn, 29.97 tbc
Stream #0.1(eng): Audio: libmp3lame, 44100 Hz, stereo, s16, 64 kb/s
```

So the video is being resampled and it's visibly worse quality. Is there a way to force ffmpeg to not resample the video?

---

### Post by mc4man on 2010-03-01
use -vcodec copy

---

### Post by sojyujai on 2010-03-01
Awesome.  Thanks!

---

