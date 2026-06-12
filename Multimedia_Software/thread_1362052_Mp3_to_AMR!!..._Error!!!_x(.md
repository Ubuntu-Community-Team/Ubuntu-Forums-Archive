---
title: "Mp3 to AMR!!... Error!!! x("
date: 2009-12-22
forum: Multimedia Software
---

### Post by gonzasepulveda on 2009-12-22
[FONT=Arial Black][SIZE=5][B]I used that
[/B][/SIZE][/FONT]
xxx@xxxxcore:/home/xxx/videolab$ ffmpeg -i 250-5625712252-0912110949.wav -acodec amr_nb -ar 8000 -ac 1 -ab 32 250-5625712252-0912110949.amr
[SIZE=5][B][FONT=Arial Black]
THIS IS THE ERROR !![/FONT][/B][/SIZE]

FFmpeg version SVN-r20761, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  built on Dec 22 2009 13:37:13 with gcc 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
  configuration: 
  libavutil     50. 5. 1 / 50. 5. 1
  libavcodec    52.42. 0 / 52.42. 0
  libavformat   52.41. 0 / 52.41. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 2 /  0. 7. 2
[wav @ 0x8a27380]max_analyze_duration reached
[wav @ 0x8a27380]Estimating duration from bitrate, this may be inaccurate
Input #0, wav, from '250-5625712252-0912110949.wav':
  Duration: 00:04:08.12, bitrate: 128 kb/s
    Stream #0.0: Audio: pcm_s16le, 8000 Hz, 1 channels, s16, 128 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'amr_nb'


[SIZE=4]i don't know that to doo...

help me!!!....[/SIZE]

---

### Post by ron999 on 2009-12-22
Hi
You've got two errors.
The first one is this:-

WARNING: **The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s**
In your command is **-ab 32**
Change this into **-ab 32k**

The next error is:-
[B]Unknown encoder 'amr_nb'
[/B]
This means that you haven't got the amr codec installed.
I don't know how to do this, maybe someone else will help.
But for now, see if you can cure the first error then post again.
:)

---

### Post by FakeOutdoorsman on 2009-12-22
> **gonzasepulveda said:**
> ```
FFmpeg version SVN-r20761, Copyright (c) 2000-2009 Fabrice Bellard, et al.
```
It looks like you compiled FFmpeg yourself.  Did you follow this guide?

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

If yes, then your command needs to be modified:
```
ffmpeg -i input.wav -acodec libopencore_amrnb -ar 8000 -ab 12.2k -ac 1 output.amr
```
or just simply:
```
ffmpeg -i input.wav -ar 8000 -ab 12.2k -ac 1 output.amr
```

For those of you using Ubuntu Karmic who don't want to compile, see option "C" here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by gonzasepulveda on 2010-01-13
Ok, i'll try :popcorn:

---

