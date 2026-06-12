---
title: "OGV to a normal format"
date: 2009-04-21
forum: Multimedia Software
---

### Post by ephracis on 2009-04-21
Ok, so now I have recorded some stuff using my webcam and Cheese. The format is of course ogg video (ogv). Don't know the actual codec, though.

As we all know there are no good video editing tools for Linux so I figured I would just put it on my Windows box and use Movie Maker. Well, Windows doesn't care for open formats, so Movie Maker can only use the common formats like avi, mpg, etc. So I need to convert my files.

I did some Googling and found, on this forums, people with the same problem.

It didn't work:


First some mencoder tips:
```

**$ mencoder -idx input.ogv -ovc -lavc mp3lame -o output.avi**
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option ovc: Unknown suboption -lavc
Error parsing option on the command line: -ovc

Exiting... (error parsing command line)

```
Yeah, a command option that doesn't work. Dead stop there.

Next some ffmpeg magic:
```

**$ ffmpeg -i input.ogv output.avi**
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
Input #0, ogg, from 'input.ogv':
  Duration: 00:14:10.6, start: 0.000000, bitrate: 1749 kb/s
    Stream #0.0: Video: theora, 320x240 [PAR 0:0 DAR 0:0], 30.00 tb(r)
    Stream #0.1: Audio: vorbis, 44100 Hz, mono, 80 kb/s
swScaler: Unknown format is not supported as input format
Cannot get resampling context

```
Yeap, that didn't work either.

Please, if you insist on using open containers and codecs can you at least give me some tool to convert it to a format that works with the rest of the world? I would love some easy GUI-based app that just works. I tried avidemux (gtk) and all I get is "cannot open file". So that's a dead end as well.

How can I make my files usable?

---

### Post by regala on 2009-04-21
> **ephracis said:**
> 
First some mencoder tips:
```

**$ mencoder -idx input.ogv -ovc -lavc mp3lame -o output.avi**


well, you should read better the man pages for mencoder, the cmdline should be:
[code]
$ mencoder -idx input.ogv -ovc lavc -lavcopts vcodec=mpeg4 -oac mp3lame -o output.avi

```

(you did not tell mencoder what video codec to use and did not give -ovc an argument)

---

### Post by regala on 2009-04-21
> **regala said:**
> well, you should read better the man pages for mencoder, the cmdline should be:
```

$ mencoder -idx input.ogv -ovc lavc -lavcopts vcodec=mpeg4 -oac mp3lame -o output.avi

```

(you did not tell mencoder what video codec to use and did not give -ovc an argument)

to explain:

-oac specifies the audio codec, here mp3lame, you can then add -lameopts to specify details about how the mp3lame codec will perform
-ovc specifies the video codec, here avcodec (lavc), you can then add -lavcopts to specify details about how libavcodec will perform (here i added vcodec=mpeg4)

---

### Post by ephracis on 2009-04-21
```

**$ mencoder -idx input.ogv -ovc lavc -lavcopts vcodec=mpeg4 -oac mp3lame -o output.avi**
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0xb1725c1
[Ogg] stream 0: video (Theora v3.2.1), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  320x240  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:320x240  fps:30.00  ftime:=0.0333
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 80.0 kbit/11.34% (ratio: 10000->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x88433b0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (320x240 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
MP3 audio selected.

Too many audio packets in the buffer: (4096 in 778282 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:      nan kbit/s  (-2147483648 B/s)  size: 0 bytes  0.000 secs  0 frames

Audio stream:  104.615 kbit/s  (13076 B/s)  size: 6832 bytes  0.522 secs

```
Trying to play the output file gives error "Could not demultiplex stream."

---

### Post by ctsdownloads on 2009-04-27
And yes, this is still a problem!

[http://ubuntuforums.org/showthread.php?p=7163674#post7163674](http://ubuntuforums.org/showthread.php?p=7163674#post7163674)

---

### Post by edgarinventor on 2010-02-18
I'm just trying Winff...

Works! :D

Converted it to youtube's flv, but there's more...

[http://www.newbox.tv/index.php?option=com_hwdvideoshare&task=viewvideo&Itemid=1&video_id=1144]("http://www.newbox.tv/index.php?option=com_hwdvideoshare&task=viewvideo&Itemid=1&video_id=1144")

---

### Post by tubunu on 2010-03-10
When I convert ogv to any other format I can only hear the sound, I have a black screen for video. Any tips?

---

### Post by OSLinuxFreak on 2010-04-28
> **regala said:**
> well, you should read better the man pages for mencoder, the cmdline should be:
```

$ mencoder -idx input.ogv -ovc lavc -lavcopts vcodec=mpeg4 -oac mp3lame -o output.avi

```

(you did not tell mencoder what video codec to use and did not give -ovc an argument)

This worked perfectly for me regala :). I just started working with trying screen cast and had same issue wit the .ogv. Thanks for sharing you knowledge.

---

### Post by edgarinventor on 2010-06-08
> **tubunu said:**
> When I convert ogv to any other format I can only hear the sound, I have a black screen for video. Any tips?

I got a fake-colored one, tried this, and worked.
[http://gtk-apps.org/content/show.php?content=90837]("http://gtk-apps.org/content/show.php?content=90837")
Worked on a 3 minutes 17 seconds Video!
[http://faz-voce-mesmo.blogspot.com/2010/06/como-sacar-o-som-do-youtube-no-ubuuntu.html]("http://faz-voce-mesmo.blogspot.com/2010/06/como-sacar-o-som-do-youtube-no-ubuuntu.html") :biggrin:

---

### Post by Spirit of Yggdrasill on 2010-07-26
> **regala said:**
> 
```

$ mencoder -idx input.ogv -ovc lavc -lavcopts vcodec=mpeg4 -oac mp3lame -o output.avi

```


Worked like a charm. Big thanks, I was biting my nails...:D
btw I was looking for: "ubuntu convert ogv for youtube"

Cheers,
Ivan :-)

---

### Post by FakeOutdoorsman on 2010-07-26
You can also use FFmpeg to convert videos from recordMyDesktop, but you'll need to use a more recent version than what Lucid and previous releases provide. Fortunately you can compile FFmpeg fairly easily:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by karmila on 2010-07-27
> **OSLinuxFreak said:**
> This worked perfectly for me regala :). I just started working with trying screen cast and had same issue wit the .ogv. Thanks for sharing you knowledge.

worked for me too :D

---

### Post by karmila on 2010-07-27
> **FakeOutdoorsman said:**
> You can also use FFmpeg to convert videos from recordMyDesktop, but you'll need to use a more recent version than what Lucid and previous releases provide. Fortunately you can compile FFmpeg fairly easily:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

thanks for the tips.

I can't figured out why ffmpeg is not working and the tips sorted it out ;)

---

### Post by alanmoore78 on 2010-10-09
I tell you what, I was trying so many different things to make ffmpeg work but mencoder took care of the problem.  My .ogv file at 53MB that would play great audio but showed a static green screen once uploaded is now a .avi at 34MB and it uploaded and displays properly on YouTube.

THANKS!  I made a video with recordMyDesktop to show my parents a few cars they wanted to find at local car dealers so I was able to visit the local dealer sites and show them what was in inventory and it works great!  I'll be using the mencoder from now on, it's simple, it does the job, and I like playing on the command line.

---

