---
title: "MOD video files from JVC video camera"
date: 2009-02-07
forum: Multimedia Software
---

### Post by jonathanku on 2009-02-07
Hi - I've got a bunch of video files from a JVC video camera.

Having a couple of struggles editing them, but the bottom line is, I'd like to be able to convert them to something more standard that will be more widely compatible. I am able to play the video in a couple of media players - but I do get errors during playback (and crashes in Cinelerra).

From my reading, the **video is MPEG-2**
And the **audio is MP2** (MPEG-1 Audio Layer II)

Can you suggest an ffmpeg command to convert them? I suspect I need another audio codec, but I'm not sure. Any help before my hair get torn out would be much appreciated. What video/audio to use? 

Thanks,
JK

---

### Post by andrew.46 on 2009-02-07
Hi,

FFmpeg would definitely be the tool although I will admit that I have never encountered the .mod format that apparently many camcorders use. (Hopefully FFmpeg can read these files!) Can you examine the file with FFmpeg to show the contents? The command would be:

```
ffmpeg -i myfile.mod
```

Following this the choices range from simply *copying* both video and audio into a new container, which may be sufficient for your needs, to *transcoding* audio and video into the container of your choice.

There are several FFmpeg experts on these forums who will have some concrete advice once the contents of your mod files are known.

Andrew

---

### Post by mc4man on 2009-02-07
you may try, for curiosity sake, changing the ext. of the files to .mpeg or .mpg and see if that helps

---

### Post by jonathanku on 2009-02-08
> **mc4man said:**
> you may try, for curiosity sake, changing the ext. of the files to .mpeg or .mpg and see if that helpsYeah, thanks, tried it already. It didn't change how the file is handled by the video applications, just changes how the file-manager determines the default app. I think.

---

### Post by jonathanku on 2009-02-08
> **andrew.46 said:**
> Can you examine the file with FFmpeg to show the contents?
Thanks Andrew.46,

Here's the output:
```
 ffmpeg -i mov04a.mod
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mpeg, from 'mov04a.mod':
  Duration: 00:00:11.8, start: 0.197522, bitrate: 9418 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 8900 kb/s, 25.00 fps(r)
  Stream #0.1[0x80]: Audio: 0x0000, 48000 Hz, stereo, 384 kb/s
Must supply at least one output file
```

---

### Post by andrew.46 on 2009-02-08
Hi jonathanku,

> **jonathanku said:**
> 
```
Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 8900 kb/s, 25.00 fps(r)
Stream #0.1[0x80]: Audio: 0x0000, 48000 Hz, stereo, 384 kb/s
```

FFmpeg has choked a little with the audio for some reason, I do not understand that part. You could try *specifying* MP2 sound and perhaps decreasing the huge audio and video bitrates a little:

```
ffmpeg -i mov04a.mod -vcodec mpeg2video -b 1200k -acodec mp2 \
-ab 192k -ar 44100 -ac 2 -f mp4 testing.mp4
```

That encodes to an mp4 container which I think is universal enough these days. Video bitrate of 1200k and audio of 192k should be sufficient but can always be adjusted. I suspect '-vcodec copy' might do the job as well. There are better video and audio codecs available but perhaps this simple change might be enough.

I usually prefer to test such syntax myself as I am something of an FFmpeg n00b but I cannot get access to similar files so this is *not* solidly tested by me....... Where is the Fakeoutdoorsman when you need him :-).

Andrew

---

### Post by mc4man on 2009-02-08
I would think that with that audio and video format ffmpeg would show something more like this (in this case ntsc vs. pal

>  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 8000 kb/s, 29.97 tb(r)
 Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 384 kb/s


maybe it's having an 'issue' with 
 Stream #0.1[[COLOR="Red"]0x80[/COLOR]] (expecting ac3, dts or lpcm ..?

---

### Post by jonathanku on 2009-02-08
It's still not happy with it for some reason:
```
VideoCam/sd_video$ ffmpeg -i mov04a.mod -vcodec mpeg2video -b 1200k -acodec mp2 \
> -ab 192k -ar 44100 -ac 2 -f mp4 testing.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mpeg, from 'mov04a.mod':
  Duration: 00:00:11.8, start: 0.197522, bitrate: 9418 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 8900 kb/s, 25.00 fps(r)
  Stream #0.1[0x80]: Audio: 0x0000, 48000 Hz, stereo, 384 kb/s
Output #0, mp4, to 'testing.mp4':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x576, q=2-31, 1200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: mp2, 44100 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=86020) for input stream #0.1
```

---

### Post by jonathanku on 2009-02-08
I also found this post - [Aspect Ratio and Kino]("http://ubuntuforums.org/showthread.php?p=4002851#post4002851"). ddenedy says that Kino for example uses mencoder/mplayer to decode the video/audio, but ffmpeg might not have the same codecs etc. (that might explain why Cinelerra will open and play them to a certain extent).

Think I'll try mencoder, unless anyone else thinks there's a solution.

One question - if you don't have the right codec for ffmpeg, do you need to recompile ffmpeg from scratch, or can you install additional codecs afterward? The ffmpeg doc's just seem like one massive page of text!!

---

### Post by andrew.46 on 2009-02-08
Hi,

In which case there is a problem. FFmpeg does not recognise the audio codec in your original file and subsequently decides not to transcode it. Even so just check your copy of FFmpeg does encode to mp2:

```
ffmpeg -formats | grep -i mp2
```

although mp2 sound is pretty basic and will almost definitely be there. There are still a few options left:

[LIST=1]
[*]I note on google that the 'unidentified audio stream problem' that has appeared can be related to a copy of FFmpeg that has very few sound options enabled. This is certainly the case with your copy. The solution to this is to have a look at [using a more current version]("http://ubuntuforums.org/showthread.php?t=786095") with a few more options.
[*]A less probable solution is to simply copy the audio and video streams, I have seen one report of success with this on ffmpeg-users. It is a little primitive but this would involve:
```
ffmpeg -i mov04a.mod -vcodec copy -acodec copy -f mp4 testing.mp4
```
But it would be better to *identify* the audio stream.
[*]Can you upload at least a piece of one of these videos somewhere? If they are all huge you can carve a piece off with dd:
```
dd if=mov04a.mod of=sample.mod bs=1024k count=5
```
I am a little curious to see one of these problem files :-).
[/LIST]

I hope you have not lost patience with this one? A solution exists, it is just a matter of finding it :-).

Andrew

---

### Post by jonathanku on 2009-02-08
Thanks again Andrew - good information there.
Correct - MP2 appears in the formats list:
[b]  E mp2             MPEG audio layer 2
 DEA    mp2[/b]

Not checked into your option 1 yet, but option 2 did seem to give me something:
```
VideoCam/sd_video$ ffmpeg -i mov04a.mod -vcodec copy -acodec copy -f mp4 testing2.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mpeg, from 'mov04a.mod':
  Duration: 00:00:11.8, start: 0.197522, bitrate: 9418 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 8900 kb/s, 25.00 fps(r)
  Stream #0.1[0x80]: Audio: 0x0000, 48000 Hz, stereo, 384 kb/s
Output #0, mp4, to 'testing2.mp4':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x576, q=2-31, 8900 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 384 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=  300 q=0.0 Lsize=   12899kB time=12.0 bitrate=8835.3kbits/s
video:12333kB audio:562kB global headers:0kB muxing overhead 0.031565%
```
So the audio is ac3 it looks like. This should be a start. I'll now try and convert testing2.mp4 to something else.

---

### Post by andrew.46 on 2009-02-08
Hi jonathanku,

> **jonathanku said:**
> So the audio is ac3 it looks like. This should be a start. I'll now try and convert testing2.mp4 to something else.

A small triumph of linux over this horrible .mod format :-). Since you have a high bitrate mpeg2 video and high bitrate ac3 sound you should be pretty right to convert to a wide variety of formats, limited only by the constraints of the Ubuntu FFmpeg.

If you were keen to experiment a little more you might be able to force the original .mod file to *show* itself as ac3 by using the -atag option and this might get around some of the software problems you have had. (Hope somebody laughed at my 'fourcc' pun?). This is only a really good idea if the sound is *definitely* ac3, although a little googling seems to indicate that this is probably correct for these cameras. Something like:

```
ffmpeg -i mov04a.mod -vcodec copy -acodec copy [COLOR="Red"]**-atag AC3**[/COLOR] test.mod
```

Not sure if this would work but it might be worth a go. I perhaps should have mentioned that if you are using multiple tests you can use the -y option to overwrite the output file each time. BTW is FFmpeg an absolutely fascinating program or what :-).

Andrew

---

### Post by jonathanku on 2009-02-08
So after that copy - the audio reports as:
  Stream #0.1(und): Audio: 0x20736d, 48000 Hz, stereo

But trying a conversion still gives an error. Well on the "output stream". Not sure whether the -acodec flag sets the output audio codec or the input audio codec.

Anyway - try downloading this file:
[mov048.mod]("http://www.jonathankerr.co.uk/mov048.mod") (3.35MB)

---

### Post by xc3RnbFO8P on 2009-02-08
Renaming the file to mov048.mpg works fine,
I encoded it to mpeg with Devede.

---

### Post by andrew.46 on 2009-02-08
Hi jonathanku,

> **jonathanku said:**
> Anyway - try downloading this file:
[mov048.mod]("http://www.jonathankerr.co.uk/mov048.mod") (3.35MB)

Great! Is that part of the original file? The svn FFmpeg identifies this file as follows:

```

andrew@skamandros~/Desktop$ ffmpeg -i mov048.mod 
FFmpeg version SVN-r16866, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter
 --enable-pthreads --enable-libtheora --enable-libvorbis --enable-swscale 
--enable-x11grab --enable-libmp3lame --enable-libxvid --enable-libx264 
--enable-libschroedinger --enable-libfaac --enable-libfaad 
--enable-libamr-wb --enable-libamr-nb --enable-libgsm --enable-nonfree 
--enable-gpl
  libavutil     49.14. 0 / 49.14. 0
  libavcodec    52.11. 0 / 52.11. 0
  libavformat   52.25. 0 / 52.25. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 3. 0 /  0. 3. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 31 2009 10:45:47, gcc: 4.2.4
Input #0, mpeg, from 'mov048.mod':
  Duration: 00:00:02.84, start: 0.197522, bitrate: 9877 kb/s
[B][COLOR="Red"]    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 16:15 DAR 4:3], 8900 kb/s, 25.00 tb(r)
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 384 kb/s[/COLOR][/B]
At least one output file must be specified

```

The svn MPlayer has no trouble playing this one with no modification and I have attached a screenshot of this happening. So a simple modification as follows:

```

 ffmpeg -i mov048.mod -s 320x240 -vcodec mpeg4 -vtag XVID -b 1200k \
-acodec libmp3lame -ab 128k -ar 44100 test.mp4

```

worked nicely and produced a file small enough to attach to this message. This produces mpeg4 video labelled as xvid and mp3 sound. I attach this little file to this message archived up to keep the forum happy :-).

Andrew

---

### Post by FakeOutdoorsman on 2009-02-08
FFmpeg from Hardy isn't able to decode ac3, although you should still be able to copy the ac3 audio stream.  To be able to decode ac3, you can either get FFmpeg from the [Medibuntu](http://medibuntu.org/) repository, or compile FFmpeg yourself as Andrew has mentioned:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

> **jonathanku said:**
> Not sure whether the -acodec flag sets the output audio codec or the input audio codec.
It depends where you put acodec.  In this example, it applies to the input file:
```
ffmpeg -acodec ac3 -i input.mod output.mp4
```
This one applies it to the output (although this may be a bad example because I'm not sure if ac3 in mp4 container is standard):
```
ffmpeg -i input.mod -acodec ac3 output.mp4
```

---

### Post by andrew.46 on 2009-02-08
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> FFmpeg from Hardy isn't able to decode ac3, although you should still be able to copy the ac3 audio stream.  To be able to decode ac3, you can either get FFmpeg from the [Medibuntu](http://medibuntu.org/) repository, or compile FFmpeg yourself as Andrew has mentioned: [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

There are time that I wish I could forget that I am a card carrying member of the Ubuntu Beginners Team and tell everybody that I think the policy of Ubuntu in distributing crippled versions of MPlayer and FFmpeg not only sux but it creates far too many problems for Ubuntu users. The fully featured, uncrippled and recent versions of FFmpeg and MPlayer can handle almost any media and freely convert between them.

Then I remember the perceived legal problems, particularly in the United States, and my own position in the Beginners Team, and I become a little quieter :-). Mostly .....

Andrew

**Edit:** I have started a discussion on these issues [here]("http://ubuntuforums.org/showthread.php?t=1064470"). Might be interesting if not perhaps particularly useful?

---

### Post by jonathanku on 2009-02-09
Guys - thanks a lot. I'll try one of your suggestions - probably getting that other version of ffmpeg installed... but not tonight. Bed time now.

---

