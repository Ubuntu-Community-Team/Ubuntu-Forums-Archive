---
title: "avconv avi to m4v headless server"
date: 2013-12-27
forum: Multimedia Software
---

### Post by andrew-blake3 on 2013-12-27
Does anyone have any guidance on the error I am getting trying to convert an avi file to m4v (ipod) format? I want all my files to be in this format and not mp4.  I am using my Ubuntu Server 12.04 headless (no monitor) and installed all of the ffmpeg and x264 codecs using the guide [here.]("https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide") My goal is to get a lossless video in ipod format for my apple devices. Lots of info for getting it to mp4 format but not m4v. I did not install libvpx or libopus since none of my files use these codecs (that I know of).

the command I am using is: **avconv -i somefile.avi -c copy somefile.m4v**

and the output is:
avconv version 0.8.9-4:0.8.9-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:08:00 with gcc 4.6.3
Input #0, avi, from 'somefile.avi':
  Metadata:
    encoder         : transcode-1.0.6
  Duration: 00:43:46.10, start: 0.000000, bitrate: 1117 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
File 'somefile.m4v' already exists. Overwrite ? [y/N] y
[COLOR=#ff0000][ipod @ 0xdcf460] track 1: could not find tag, codec not currently supported in container[/COLOR]
Output #0, ipod, to 'somefile.m4v':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], q=2-31, 2997003.00 tbn, 23.98 tbc
    Stream #0.1: Audio: U[0][0][0] / 0x0055, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
[COLOR=#ff0000]Could not write header for output file #0 (incorrect codec parameters ?)[/COLOR]

---

### Post by andrew.46 on 2013-12-27
Looks like you have possibly compiled and installed a local, static copy of FFmpeg (from the wiki site you have mentioned) but you are still using the fork avconv which has presumably come from the Ubuntu repositories...

---

### Post by FakeOutdoorsman on 2013-12-29
Use mp4 instead of m4v. I believe m4v uses an "ipod muxer" of questionable usefulness which is likely outdated (but I may be wrong here and I didn't look into it); unless your device can't decode mp3 audio in mp4 container but I don't see why it wouldn't. Also you should use the ffmpeg you compiled instead of avconv or the fake "ffmpeg" from the repo. It will have fewer bugs and will probably be faster too.

---

