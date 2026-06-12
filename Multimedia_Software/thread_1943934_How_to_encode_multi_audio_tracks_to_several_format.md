---
title: "How to encode multi audio tracks to several formats at the same time with ffmpeg"
date: 2012-03-20
forum: Multimedia Software
---

### Post by Luca Borrione on 2012-03-20
Hello,

I'm trying to encode a dvd using ffmpeg.
```
$ffmpeg -i VTS_01_1.VOB
Input #0, mpeg, from 'VTS_01_1.VOB':
  Duration: 00:38:06.52, start: 0.287267, bitrate: 3756 kb/s
    Stream #0:0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x576 [SAR 64:45 DAR 16:9], 9800 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0:1[0x80]: Audio: ac3, 48000 Hz, 5.1(side), s16, 384 kb/s
    Stream #0:2[0x81]: Audio: ac3, 48000 Hz, 5.1(side), s16, 384 kb/s
    Stream #0:3[0x82]: Audio: ac3, 48000 Hz, 5.1(side), s16, 384 kb/s
    Stream #0:4[0x83]: Audio: ac3, 48000 Hz, mono, s16, 96 kb/s
    Stream #0:5[0x28]: Subtitle: dvd_subtitle
    Stream #0:6[0x29]: Subtitle: dvd_subtitle
    Stream #0:7[0x23]: Subtitle: dvd_subtitle
    Stream #0:8[0x24]: Subtitle: dvd_subtitle
    Stream #0:9[0x26]: Subtitle: dvd_subtitle
    Stream #0:10[0x27]: Subtitle: dvd_subtitle


```

From the above streams I'm interested in keeping two audio streams : number 1 and 4.
As you can see the number 4 is already 96kbps so I tried to execute a command which could treat the two streams in a different way:
```

cat VTS_01_1.VOB | nice ffmpeg -i - -s 640x368 -vcodec libtheora -r 25 -b:v 1200k -an -metadata title="My Title" -pass 1 -passlogfile "/media/data/outputlog" -f ogg -y /dev/null

cat VTS_01_1.VOB | nice ffmpeg -i - -map 0:0 -s 640x368 -vcodec libtheora -r 25 -b:v 1200k -async 1 -metadata title="My Title" -map 0:1 -acodec libvorbis -ac 6 -ar 48000 -b:a 192k -metadata title="english" -map 0:4 -acodec libvorbis -ac 2 -ar 48000 -b:a 96k -metadata title="commented" -pass 2 -passlogfile "/media/data/outputlog" "/media/data/output.ogv"

```

I would like to obtain:
```
Input #0, ogg, from 'output.ogv':
  Duration: 00:38:07.20, start: 0.000000, bitrate: 1360 kb/s
    Stream #0:0: Video: theora, yuv420p, 640x368 [SAR 46:45 DAR 16:9], 25 fps, 25 tbr, 25 tbn, 25 tbc
    Stream #0:1: Audio: vorbis, 48000 Hz, stereo, s16, **192** kb/s
    Stream #0:2: Audio: vorbis, 48000 Hz, stereo, s16, **96** kb/s

```

Instead with the above command I obtain:
```
Input #0, ogg, from 'output.ogv':
  Duration: 00:38:07.20, start: 0.000000, bitrate: 1360 kb/s
    Stream #0:0: Video: theora, yuv420p, 640x368 [SAR 46:45 DAR 16:9], 25 fps, 25 tbr, 25 tbn, 25 tbc
    Stream #0:1: Audio: vorbis, 48000 Hz, stereo, s16, **96** kb/s
    Stream #0:2: Audio: vorbis, 48000 Hz, stereo, s16, **96** kb/s

```

So how can I specify different params for multiple audio streams?

BTW: I'm on lubuntu oneiric with the latest ffmpeg from git
```
ffmpeg version git-2012-03-05-1007a80 Copyright (c) 2000-2012 the FFmpeg developers
  built on Mar  5 2012 09:40:09 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab --enable-libxvid --enable-libvpx
  libavutil      51. 41.100 / 51. 41.100
  libavcodec     54.  8.100 / 54.  8.100
  libavformat    54.  2.100 / 54.  2.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 63.100 /  2. 63.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  7.100 /  0.  7.100
  libpostproc    52.  0.100 / 52.  0.100

```
Thanks in advance for any help!! :)

---

### Post by FakeOutdoorsman on 2012-03-20
The *-b* option can now support stream specifiers (see the stream specifiers section in *man ffmpeg* for an explanation). From the [Changelog](git.videolan.org/?p=ffmpeg.git;a=blob;f=Changelog):
> It is now possible to precisely specify which stream should an AVOption apply to. E.g. -b:v:0 2M sets the bitrate for the first video stream, while -b:a 128k sets the bitrate for all audio streams.
Your command can be modified slightly to (this is untested):
```
cat VTS_01_1.VOB | nice ffmpeg -i - -map 0:0 -s 640x368 -vcodec libtheora -b:v 1200k -async 1 -metadata title="My Title" -map 0:1 -acodec libvorbis -b:a:0 192k -metadata title="english" -map 0:4 -ac 2 -b:a:1 96k -metadata title="commented" -pass 2 -passlogfile "/media/data/outputlog" "/media/data/output.ogv"
```
I removed some redundant options such as *-ar* and *-r*. Your input already contained the same parameters as what these options were setting. FFmpeg attempts to inherit the same frame rate, etc, from the input where applicable.

Why are you using cat instead using ffmpeg to access the input file directly?

---

### Post by Luca Borrione on 2012-03-23
Hello and thank you so much for your reply.
You pointed me to the right direction, for the cat part too.
If I can remember right I think I used it because sometimes I noticed a wrong duration time in the output file using direct access with ffmpeg while not using cat.

I played a while and it seems to be no difference if using cat or direct access with ffmpeg.
So my last command is been modified to

```
ffmpeg -i merged-vobs.mpeg -map 0:0 -s 640x368 -f ogg -vcodec libtheora -r 25 -b:v 1200k -metadata title="My Title" -acodec libvorbis -ar 48000 -map 0:1 -ac:a:0 6 -b:a:0 192k -map 0:4 -ac:a:1 2 -b:a:1 96k -async 1 -pass 2 -passlogfile "outputlog" "output.ogv"
```

And the output is correctly
```
Input #0, ogg, from 'output.ogv':
  Duration: 00:41:27.76, start: 0.000000, bitrate: 1442 kb/s
    Stream #0:0: Video: theora, yuv420p, 640x368 [SAR 46:45 DAR 16:9], 25 fps, 25 tbr, 25 tbn, 25 tbc
    Stream #0:1: Audio: vorbis, 48000 Hz, 5.1, s16, 192 kb/s
    Metadata:
      TITLE           : My Title
      ENCODER         : Lavf54.2.100
    Stream #0:2: Audio: vorbis, 48000 Hz, stereo, s16, 96 kb/s
    Metadata:
      TITLE           : My Title
      ENCODER         : Lavf54.2.100
 
```

Thank you very much for your support.

As a last note, I would like to share with you my experience with metadata.
I tried to find out a command in order to have different titles for each track like:
```
Input #0, ogg, from 'output.ogv':
  Duration: 00:41:27.76, start: 0.000000, bitrate: 1442 kb/s
    Stream #0:0: Video: theora, yuv420p, 640x368 [SAR 46:45 DAR 16:9], 25 fps, 25 tbr, 25 tbn, 25 tbc
    Stream #0:1: Audio: vorbis, 48000 Hz, 5.1, s16, 192 kb/s
    Metadata:
      TITLE           : English
      ENCODER         : Lavf54.2.100
    Stream #0:2: Audio: vorbis, 48000 Hz, stereo, s16, 96 kb/s
    Metadata:
      TITLE           : Italian
      ENCODER         : Lavf54.2.100
 
```

So I tried something as:
```
ffmpeg -i merged-vobs.mpeg -map 0:0 -s 640x368 -f ogg -vcodec libtheora -r 25 -b:v 1200k -metadata:s:v:0 title= "Video Title" -acodec libvorbis -ar 48000 -map 0:1 -ac:a:0 6 -b:a:0 192k -metadata:s:a:0 title="Track1 Title" -map 0:4 -ac:a:1 2 -b:a:1 96k -metadata:s:a:1 title="Track2 Title" -async 1 -pass 2 -passlogfile "outputlog" "output.ogv"
```

It starts promising
```
Output #0, ogg, to 'Video Title':
  Metadata:
    encoder         : Lavf54.2.100
    Stream #0:0: Video: theora, yuv420p, 640x368 [SAR 46:45 DAR 16:9], q=2-31, 1200 kb/s, 25 tbn, 25 tbc
Output #1, ogg, to 'output.ogv':
  Metadata:
    encoder         : Lavf54.2.100
    Stream #1:0: Audio: vorbis, 48000 Hz, 6 channels, flt, 192 kb/s
    Metadata:
      ENCODER         : Lavf54.2.100
      title           : Track1 Title
    Stream #1:1: Audio: vorbis, 48000 Hz, 2 channels, flt, 96 kb/s
    Metadata:
      ENCODER         : Lavf54.2.100
      title           : Track2 Title
Stream mapping:
  Stream #0:0 -> #0:0 (theora -> libtheora)
  Stream #0:1 -> #1:0 (vorbis -> libvorbis)
  Stream #0:2 -> #1:1 (vorbis -> libvorbis)
Press [q] to stop, [?] for help

```

But at the end of the process NO title will be shown at all :(
```

Input #0, ogg, from 'output.ogv':
  Duration: 00:41:27.76, start: 0.000000, bitrate: 1442 kb/s
    Stream #0:0: Video: theora, yuv420p, 640x368 [SAR 46:45 DAR 16:9], 25 fps, 25 tbr, 25 tbn, 25 tbc
    Stream #0:1: Audio: vorbis, 48000 Hz, 5.1, s16, 192 kb/s
    Metadata:
      TITLE           : 
      ENCODER         : Lavf54.2.100
    Stream #0:2: Audio: vorbis, 48000 Hz, stereo, s16, 96 kb/s
    Metadata:
      TITLE           : 
      ENCODER         : Lavf54.2.100

```

I really don't care too much about that anyway, but it would be nice to have the ability to manage tags sometimes.

Cheers

---

### Post by FakeOutdoorsman on 2012-03-23
My guess is that Ogg does not allow per-stream metadata or FFmpeg does not implement it properly. vorbiscomment (in **vorbis-tools** package) might be useful here, but I'm not sure if can do per-stream metadata. Matroska (.mkv) output container should allow this though.

Also, you may want to look into using a quality-based instead of bitrate-based rate control method, unless of course you're trying to achieve a certain file size:

[http://ubuntuforums.org/showpost.php?p=11530735&postcount=2](http://ubuntuforums.org/showpost.php?p=11530735&postcount=2)

---

