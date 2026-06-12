---
title: "Error encoding Audio"
date: 2014-01-22
forum: Multimedia Software
---

### Post by sayre on 2014-01-22
Hi Everyone, 
   
  I am having an issue trying to change the audio track on an .MKV  from ac3 to libmp3lame using  the following command and am having the below problem. 
   
  avconv -i input.mkv -vcodec copy -acodec libmp3lame output.mkv
   
  avconv version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
    built on Nov  9 2013 19:08:00 with gcc 4.6.3
  [matroska,webm @ 0xf109c0] Estimating duration from bitrate, this may be inaccurate
  Input #0, matroska,webm, from 'input.mkv':
    Duration: 00:42:33.60, start: 0.000000, bitrate: 384 kb/s
      Stream #0.0(eng): Video: h264 (High), yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 23.98 fps, 23.98 tbr, 1k tbn, 2k tbc (default)
      Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s (default)
      Stream #0.2: Subtitle: [0][0][0][0] / 0x0000 (default)
  File 'output.mkv' already exists. Overwrite ? [y/N] y
  Output #0, matroska, to 'output.mkv':
      Stream #0.0(eng): Video: libx264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], q=2-31, 90k tbn, 1k tbc (default)
      Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, 5.1, s16, 200 kb/s (default)
      Stream #0.2: Subtitle: [0][0][0][0] / 0x0000, 200 kb/s (default)
  Stream mapping:
    Stream #0:0 -> #0:0 (copy)
    Stream #0:1 -> #0:1 (ac3 -> libmp3lame)
    Stream #0:2 -> #0:2 (? -> ass)
  Error while opening encoder for output stream #0:1 - maybe incorrect parameters such as bit_rate, rate, width or height
   
   
  I have tried setting the bit rate to lower than 320 because I read that’s the max it can handle but I get the same error..  Any ideas?

---

### Post by andrew.46 on 2014-01-22
I will admit that I am not completely sure but I suspect the problem may lay with the 5.1 sound:

```
Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, **[COLOR="#FF0000"]5.1[/COLOR]**, s16, 200 kb/s (default)
```

I believe the avconv command for that is *-ac 2 *...

---

### Post by sayre on 2014-01-23
> **andrew.46 said:**
> I will admit that I am not completely sure but I suspect the problem may lay with the 5.1 sound:

```
Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, **[COLOR=#FF0000]5.1[/COLOR]**, s16, 200 kb/s (default)
```

I believe the avconv command for that is *-ac 2 *...

So I tried that and got a different error at the end.  

avconv -i input.mkv -vcodec copy -acodec libmp3lame -ac 2 -sn  output.mkv


avconv version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:08:00 with gcc 4.6.3
[matroska,webm @ 0xd809c0] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from 'input.mkv':
  Duration: 00:42:33.60, start: 0.000000, bitrate: 384 kb/s
    Stream #0.0(eng): Video: h264 (High), yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 23.98 fps, 23.98 tbr, 1k tbn, 2k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s (default)
    Stream #0.2: Subtitle: [0][0][0][0] / 0x0000 (default)
File 'output.mkv' already exists. Overwrite ? [y/N] y
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0(eng): Video: libx264, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], q=2-31, 1k tbn, 1k tbc (default)
    Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, 2 channels, s16, 200 kb/s (default)
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (ac3 -> libmp3lame)
Press ctrl-c to stop encoding
Input stream #0:1 frame changed from rate:48000 fmt:s16 ch:6 to rate:48000 fmt:s16 ch:2
[B][COLOR=#ff0000][matroska @ 0xd88760] pts < dts in stream 0
av_interleaved_write_frame(): Invalid argument[/COLOR][/B]


Is it possible to just setup my server to just covert .mkvs on the fly to mp4 when someone is trying to watch them?

---

### Post by FakeOutdoorsman on 2014-01-23
Try downloading a recent [build of ffmpeg](https://ffmpeg.org/download.html#LinuxBuilds) or [compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) and see if it works as expected.

For the lazy (notice the **./** before ffmpeg):
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz
./ffmpeg -i input ...
```

Please use the [code tag](http://ubuntuforums.org/misc.php?do=bbcode#code). It will help to differentiate your comments and command/console outputs.

---

