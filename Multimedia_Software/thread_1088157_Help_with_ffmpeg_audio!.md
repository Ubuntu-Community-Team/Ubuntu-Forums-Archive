---
title: "Help with ffmpeg audio!"
date: 2009-03-05
forum: Multimedia Software
---

### Post by Chaosleet on 2009-03-05
Hey guys. I have a load of .avi files I want to convert to .flv for streaming on the web (for a new site I'm planning to make :)).

I have got all the .avi files saved, and I'm using WinFF as a GUI for the ffmpeg commands. When I convert a .avi video, it's perfect... the video is a very good quality and just how I want it... **BUT** it has no audio what so ever.

These are the settings I am using:
[img]http://i42.tinypic.com/2exc61k.png[/img]

Any help on the matter would be very gratefully appreciated :)

---

### Post by FakeOutdoorsman on 2009-03-05
What Ubuntu version are you using?  Show the outputs of:
```
ffmpeg -i 1.avi
```
and
```
ffmpeg -i the-output-file.flv
```

---

### Post by Chaosleet on 2009-03-06
Alright:
```
Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from '1.avi':
  Duration: 00:23:23.9, start: 0.000000, bitrate: 1048 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 576x432, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Must supply at least one output file
```

```
Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from '1.flv':
  Duration: 00:23:24.0, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: flv, yuv420p, 320x240, 15.00 fps(r)
Must supply at least one output file
```

Looks like it has audio on the source file but not the flv :)

---

### Post by FakeOutdoorsman on 2009-03-06
What version of Ubuntu are you using?  Can you show the full FFmpeg output from one of the above commands?

---

### Post by Chaosleet on 2009-03-06
I'm running Ubuntu Release 8.04 (Hardy).

Full output from the commands:
```
admin@ks359837:~/convert/$ ffmpeg -i 1.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from '1.avi':
  Duration: 00:23:23.9, start: 0.000000, bitrate: 1048 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 576x432, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Must supply at least one output file
```

```
admin@ks359837:~/convert/Season1$ ffmpeg -i 1.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from '1.flv':
  Duration: 00:23:24.0, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: flv, yuv420p, 320x240, 15.00 fps(r)
Must supply at least one output file

```

Thanks for the help thusfar :)

---

### Post by FakeOutdoorsman on 2009-03-06
I believe FFmpeg by default will encode mp3 audio when given the flv extension for output files, but FFmpeg from the Ubuntu repository doesn't support mp3 encoding.  You can use FFmpeg from the Medibuntu repository though.

See the "Details ffmpeg for Hardy" section of [WinFF Ubuntu Installation](http://code.google.com/p/winff/wiki/UbuntuInstallation).

Alternatively, since your input source already has mp3 audio, you can just copy that audio stream.  Open WinFF -> Options -> Additional Options.  Add **-acodec copy** to the Additional Command Line Parameters box.

---

### Post by Chaosleet on 2009-03-06
Thanks for the fast reply.

When I ran the conversion process with "-vcodec copy" it ended up converting within seconds (instead of taking about 10 minutes like normal) and this is the result:
```
frame=33660 q=0.0 Lsize=  155430kB time=1403.9 bitrate= 907.0kbits/s    
video:154904kB audio:0kB global headers:0kB muxing overhead 0.339643%
Press Enter to Continue
```

I'm going to take a look at the link for the repositories now :)

---

### Post by FakeOutdoorsman on 2009-03-06
Oops...  that should be **-acodec copy**, not -vcodec copy.  I corrected it in my above post.

---

### Post by Chaosleet on 2009-03-06
Thanks, but I get this error when I try and convert with that command:

```
Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from '/home/admin/convert/Season1/1.avi':
  Duration: 00:23:23.9, start: 0.000000, bitrate: 1048 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 576x432, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
File '/home/admin/convert/1.flv' already exists. Overwrite ? [y/N] y
Output #0, flv, to '/home/admin/convert/1.flv':
  Stream #0.0: Video: flv (hq), yuv420p, 576x432, q=2-31, 1093 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: 0x0055, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[NULL @ 0xb7f616e8]flv doesnt support that sample rate, choose from (44100, 22050, 11025)
Could not write header for output file #0 (incorrect codec parameters ?)
Press Enter to Continue
```

I have done some Google'ing and it turns out it's a problem with .FLV having to have a sample rate of 44100, 22050 or 11025.

If I enter ANY of the values above into the "Sample rate" field in WinFF it just gives me that error message again.

These are the settings I am using:
[img]http://imgkk.com/images/dtq6hks.png[/img]

Cheers.

---

### Post by FakeOutdoorsman on 2009-03-06
The **-acodec copy** option will not work if you want to change the sample rate because it just copies the audio stream without re-encoding or altering it.  You will need to re-encode the source audio, but to do that you will need to install FFmpeg from the Medibuntu repository.

---

