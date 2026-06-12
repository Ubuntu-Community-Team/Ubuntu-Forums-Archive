---
title: "Winff script error - please look over and tell me whats missing?"
date: 2012-04-21
forum: Multimedia Software
---

### Post by AlexOnVinyl on 2012-04-21
I've been trying to convert a video over using both ffmpeg and winff gui and have had little to no success whatsoever with it.

I got all the codecs from Medibuntu and am running the latest WinFF.

So here's what I did:


```
alex@griever:~/Videos$ '/home/alex/Videos/script for immortals'
``` 

Here's my script: ```
#!/bin/sh
echo -n "\033]0; Converting tmp_8472517 (1/1)\007"
/usr/bin/ffmpeg -ss 00:01:00 -t 00:00:30 -i "/home/alex/Videos/Immortals.2011.720p.BRRip.x264-x0r.mkv" -f avi -r 29.97 -vf crop=iw:ih-58-62:0:58,scale=1280:690 -vcodec libxvid -vtag XVID -aspect 2.35 -maxrate 1800k  -b 700k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -trellis -aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame  -ar 41000 -ab 192k -ac 2  -vol 256 -an -passlogfile "/home/alex/tmp_8472517.log" -pass 1  -y /dev/null
/usr/bin/ffmpeg -ss 00:01:00 -t 00:00:30 -y -i "/home/alex/Videos/Immortals.2011.720p.BRRip.x264-x0r.mkv" -f avi -r 29.97 -vf crop=iw:ih-58-62:0:58,scale=1280:690 -vcodec libxvid -vtag XVID -aspect 2.35 -maxrate 1800k  -b 700k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -trellis -aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame  -ar 41000 -ab 192k -ac 2  -vol 256 -passlogfile "/home/alex/tmp_8472517.log" -pass 2  "/home/alex/tmp_8472517.avi"
/usr/bin/ffplay "/home/alex/tmp_8472517.avi"
rm "/home/alex/tmp_8472517.avi"
rm "/home/alex/.winff/ff120420212101.sh"
```

Here's the output:

> ffmpeg version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:29:10 with gcc 4.6.3
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).
[matroska,webm @ 0x9eae240] max_analyze_duration reached
[matroska,webm @ 0x9eae240] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 180000.00 (180000/1) -> 23.98 (24000/1001)
Input #0, matroska,webm, from '/home/alex/Videos/Immortals.2011.720p.BRRip.x264-x0r.mkv':
  Metadata:
    title           : Immortals.2011.720p.BRRip.x264-x0r
  Duration: 01:50:26.78, start: 0.000000, bitrate: 448 kb/s
    Stream #0.0(eng): Video: h264 (High), yuv420p, 1280x690 [PAR 1:1 DAR 128:69], 23.98 fps, 23.98 tbr, 1k tbn, 180k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s (default)
    Stream #0.2(eng): Subtitle: [0][0][0][0] / 0x0000 (default)
[buffer @ 0xa01d0a0] w:1280 h:690 pixfmt:yuv420p
[crop @ 0xa224800] w:1280 h:690 -> w:1280 h:570
[scale @ 0xa224840] w:1280 h:570 fmt:yuv420p -> w:1280 h:690 fmt:yuv420p flags:0x4
[libxvid @ 0xa287600] [Eval @ 0xbfd305ac] Undefined constant or missing '(' in 'aic'
[libxvid @ 0xa287600] Unable to parse option value "aic"
[libxvid @ 0xa287600] Error setting option trellis to value -aic.
Output #0, avi, to '/dev/null':
    Stream #0.0(eng): Video: mpeg4 (hq), yuv420p, 1280x690 [PAR 19:15 DAR 2432:1035], q=3-5, pass 1, 700 kb/s, 90k tbn, 29.97 tbc (default)
Stream mapping:
  Stream #0.0 -> #0.0
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
ffmpeg version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:29:10 with gcc 4.6.3
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).
[matroska,webm @ 0x8a4b240] max_analyze_duration reached
[matroska,webm @ 0x8a4b240] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 180000.00 (180000/1) -> 23.98 (24000/1001)
Input #0, matroska,webm, from '/home/alex/Videos/Immortals.2011.720p.BRRip.x264-x0r.mkv':
  Metadata:
    title           : Immortals.2011.720p.BRRip.x264-x0r
  Duration: 01:50:26.78, start: 0.000000, bitrate: 448 kb/s
    Stream #0.0(eng): Video: h264 (High), yuv420p, 1280x690 [PAR 1:1 DAR 128:69], 23.98 fps, 23.98 tbr, 1k tbn, 180k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s (default)
    Stream #0.2(eng): Subtitle: [0][0][0][0] / 0x0000 (default)
[buffer @ 0x8db7480] w:1280 h:690 pixfmt:yuv420p
[crop @ 0x8dc1720] w:1280 h:690 -> w:1280 h:570
[scale @ 0x8bba100] w:1280 h:570 fmt:yuv420p -> w:1280 h:690 fmt:yuv420p flags:0x4
[libmp3lame @ 0x8db6c60] Requested sampling rate unsupported using closest supported (44100)
[libxvid @ 0x8e24600] [Eval @ 0xbff465ec] Undefined constant or missing '(' in 'aic'
[libxvid @ 0x8e24600] Unable to parse option value "aic"
[libxvid @ 0x8e24600] Error setting option trellis to value -aic.
Output #0, avi, to '/home/alex/tmp_8472517.avi':
    Stream #0.0(eng): Video: mpeg4 (hq), yuv420p, 1280x690 [PAR 19:15 DAR 2432:1035], q=3-5, pass 2, 700 kb/s, 90k tbn, 29.97 tbc (default)
    Stream #0.1(eng): Audio: libmp3lame, 44100 Hz, 2 channels, s16, 200 kb/s (default)
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
avplay version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2003-2011 the Libav developers
  built on Mar 22 2012 05:29:10 with gcc 4.6.3
/home/alex/tmp_8472517.avi: Invalid data found when processing input


Any help is appreciated.

---

### Post by nothingspecial on 2012-04-21
*Thread moved to **Multimedia & Video**.*

---

### Post by FakeOutdoorsman on 2012-04-22
Where did you get this ffmpeg command? Is it a WinFF preset? Are you using Ubuntu Precise? What is your final target for the output file (web, a device, computer, etc)?

It's an odd command. It sets options for the audio and then tells the encoder to ignore the audio. It uses some old options that don't exist anymore or now have a new syntax.

---

### Post by BicyclerBoy on 2012-04-22
Pardon the noise..

The first pass (of 2) is ignoring the audio..that is correct?

Your ffmpeg is the Libav avconv variant..which could be slightly incompatible..
I believe ubuntu has gone the Libav route..

You can get the ffmpeg version of ffmpeg 0.9.1 from Jon Severinssons ppa
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)
This ppa seems to be complete (not stripped) & is avail for lucid to precise.

I use this ppa to keep the std installed packages happy & build ffmpeg as well.

---

