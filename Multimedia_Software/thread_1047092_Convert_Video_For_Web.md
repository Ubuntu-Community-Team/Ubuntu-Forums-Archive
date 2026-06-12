---
title: "Convert Video For Web"
date: 2009-01-22
forum: Multimedia Software
---

### Post by spikoley on 2009-01-22
I am a noob to video editing and need advice on converting a .mov file to be smaller for the web.  What program and file type should I use to convert the file without taking too much bandwidth and not sacrificing quality?

---

### Post by binbash on 2009-01-22
You should convert it to flv.If i am not wrong, avidemux does this, correct me if i am wrong.

---

### Post by spikoley on 2009-01-22
I found a [blog]("http://worldtv.com/blog/guides_tutorials/flv_converter.php") that recommended using ffmpeg.  The blog is written for Windows but it is well done and shows command line examples to convert video.   Ffmpeg did a great job on the conversion.

---

### Post by spikoley on 2009-01-23
I was able to play the file, but when I sent it to my buddy he could not play it in XP.  Any ideas on what I need to do?  Here is the command I ran.

```
ffmpeg -i 16mmreel2.mov -ar 22050 16mmreel2.flv
```

---

### Post by mdewet on 2009-01-23
> **spikoley said:**
> I was able to play the file, but when I sent it to my buddy he could not play it in XP.  Any ideas on what I need to do?  Here is the command I ran.

```
ffmpeg -i 16mmreel2.mov -ar 22050 16mmreel2.flv
```

Maybe he doesn't have the correct codecs / software to play .flv videos

---

### Post by spikoley on 2009-01-23
> **mdewet said:**
> Maybe he doesn't have the correct codecs / software to play .flv videos

He is able to play videos on YouTube and I just tested it and had the same issue on an XP box.  It does sound like a codec issue.  How can I make it a default .flv where this codec issue does not come up?

---

### Post by andrew.46 on 2009-01-23
Hi,

Can you run ffmpeg over one of the .mov files? The command will be:

```
ffmpeg -i myfile.mov
```

Perhaps either video or sound need to be altered for the flv container. If you are keen to have your flv similar to a youtube one the newer ones have h264 video and aac sound. Older ones have h263 video and mono mp3. Have a look at:

[http://en.wikipedia.org/wiki/YouTube](http://en.wikipedia.org/wiki/YouTube)

and have a look at the 'Format and quality comparison table' towards the bottom.

Andrew

---

### Post by spikoley on 2009-01-23
> **andrew.46 said:**
> Hi,

Can you run ffmpeg over one of the .mov files? The command will be:

```
ffmpeg -i myfile.mov
```

Perhaps either video or sound need to be altered for the flv container. If you are keen to have your flv similar to a youtube one the newer ones have h264 video and aac sound. Older ones have h263 video and mono mp3. Have a look at:

[http://en.wikipedia.org/wiki/YouTube](http://en.wikipedia.org/wiki/YouTube)

and have a look at the 'Format and quality comparison table' towards the bottom.

Andrew

I ran the command you supplied and got an error.

```
ffmpeg -i 16mmreel2.mov 
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 2997.00 (2997/1) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '16mmreel2.mov':
  Duration: 00:16:33.9, start: 0.000000, bitrate: 30310 kb/s
    Stream #0.0(eng): Video: dvvideo, yuv411p, 720x480 [PAR 0:1 DAR 0:1], 29.97 tb(r)
    Stream #0.1(eng): Audio: pcm_s16be, 48000 Hz, mono, 768 kb/s
    Stream #0.2(eng): Audio: pcm_s16be, 48000 Hz, mono, 768 kb/s
Must supply at least one output file
```

In order to convert the video I have to use the switch -ar 22050.  That conversion runs great on my machine, but not on XP.  Do you think if I use a different number after the switch it might work?  When I do not use a switch it give me the error: > Sample rate must be 11025, 22050 or 44100 Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

---

### Post by spikoley on 2009-01-23
I created a test file for others to test.  Get it [here]("http://www.badongo.com/cvid/1001010/1") or [here]("http://www.badongo.com/vid/1001010").

---

### Post by FakeOutdoorsman on 2009-01-23
Your test.flv video should work in Windows, although I didn't test this, if you use a web Flash player such as [JW Player](http://www.longtailvideo.com/players/jw-flv-player/) or [Flowplayer](http://flowplayer.org/).  Both are free for non-commercial users.  Of course you need access to a web server.  If you use mp3 audio instead of adpcm_swf, your video will work in [VLC player](http://www.videolan.org/) for Windows.  The following ffmpeg command will create a flv with mp3 audio:
```
ffmpeg -i 16mmreel2.mov -acodec libmp3lame -ar 44100 output.flv
```
You will need the package **libavcodec-unstripped-51** to enable the libmp3lame encoder in ffmpeg.

---

