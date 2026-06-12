---
title: "Video Export: Audio Scratch"
date: 2013-05-22
forum: Multimedia Software
---

### Post by iacoposk8 on 2013-05-22
Hello to all! I'm using this command to trim a video:
```
mencoder 0.ogv -ovc lavc -oac lavc -ss 00:00:00 -endpos 00:01:00 -o 0.mp4
```
and the output is:
```
MEncoder svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.

success: format: 0  data: 0x0 - 0xbe55000

libavformat version 53.21.1 (external)

Mismatching header version 53.19.0

libavformat file format detected.

[ogg @ 0xb6c8ab80]max_analyze_duration reached

[lavf] stream 1: video (theora), -vid 0

[lavf] stream 2: audio (vorbis), -aid 0

VIDEO:  [theo]  624x352  0bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)

[V] filefmt:44  fourcc:0x6F656874  size:624x352  fps:15.000  ftime:=0.0667

==========================================================================

Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders

libavcodec version 53.35.0 (external)

Mismatching header version 53.32.2

AUDIO: 22050 Hz, 1 ch, s16le, 90.0 kbit/25.51% (ratio: 11248->44100)

Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)

==========================================================================

Opening video filter: [expand osd=1]

Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1

==========================================================================

Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family

Selected video codec: [fftheora] vfm: ffmpeg (FFmpeg Theora)

==========================================================================

[mp2 @ 0xb6534120]bitrate 224 is not allowed in mp2

Couldn't open codec mp2, br=224.

Exiting...
```

half the stuff that is written is incomprehensible, but the last line suggests to me that has problems with the audio, so I did two tests
one with -oac mp3lame and one with -oac copy
in the first case (the best so far) the video is exported but the audio is very saturated, scratch a lot ... is not inaudible, but it bothers
in the second case, the audio is inaudible because it is fast, does not even feel the words

how come? how can I?

PS: I also tried kdenlive but the result is the same and avidemux does not open the file

---

### Post by andrew.46 on 2013-05-22
Not a lot of people use MEncoder any more as there is very little development, this has been the case for some years now. You could try FFmpeg or avconv and probably get a better result or if you are really keen on MEncoder try building a better copy[ from this guide]("http://www.andrews-corner.org/mplayer.html"). Native format for MEncoder is avi btw, I dimly remember that some syntactical gymnastics are required to output to mp4.

---

### Post by iacoposk8 on 2013-05-22
is embarrassing...
```
avconv -i 0.ogv -vcodec copy -acodec copy -ss 00:00:00 -t 00:01:00 1.ogv
```
works and in much less time than mencoder....
but if I write (to convert):
```
avconv -i 0.ogv -vcodec copy -acodec copy -ss 00:00:00 -t 00:01:00 1.avi
```
I get the following output:
```
avconv version 0.8.6-6:0.8.6-1ubuntu2, Copyright (c) 2000-2013 the Libav developers
  built on Mar 30 2013 22:23:21 with gcc 4.7.2
[ogg @ 0x9e19a20] max_analyze_duration reached
Input #0, ogg, from '0.ogv':
  Duration: 00:20:02.53, start: 0.000000, bitrate: 1327 kb/s
    Stream #0.0: Data: skeleton
    Stream #0.1: Video: theora, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 15 fps, 15 tbr, 15 tbn, 15 tbc
    Stream #0.2: Audio: vorbis, 22050 Hz, mono, s16, 89 kb/s
Output #0, avi, to '2.avi':
  Metadata:
    ISFT            : Lavf53.21.1
    Stream #0.0: Video: libtheora, yuv420p, 624x352 [PAR 1:1 DAR 39:22], q=2-31, 15 tbn, 15 tbc
    Stream #0.1: Audio: libvorbis, 22050 Hz, mono, 89 kb/s
Stream mapping:
  Stream #0:1 -> #0:0 (copy)
  Stream #0:2 -> #0:1 (copy)
Press ctrl-c to stop encoding
frame=  899 fps=  0 q=-1.0 Lsize=   10988kB time=59.99 bitrate=1500.4kbits/s    
video:10037kB audio:670kB global headers:0kB muxing overhead 2.633255%


```
and when I try to open the file tells me that is missing the following codecs: audio/x-avi-unknown

---

### Post by andrew.46 on 2013-05-23
I experimented a little and it looks like theora + vorbis is a bad choice for the avi container. Perhaps try an mp4 or mkv container instead?

---

### Post by SeijiSensei on 2013-05-23
The AVI container works best with older MPEG4 technologies like DivX/XviD.  Like Andrew, I'd pick mp4 or, my preference, mkv.  On the audio side, the standard codec for AVI is MP3.  You'll need to install ubuntu-restricted-extras to encode to that proprietary standard.

In general, I use XviD+MP3 in the AVI container, and H.264+AAC in the MKV container.

---

### Post by iacoposk8 on 2013-05-23
yes, so it converts but lose quality ... I'm okay even OVG anyway, thank you very much for helping me :)

---

