---
title: "Trying to convert.avi to .wmv with FFMPEG"
date: 2007-09-24
forum: Multimedia &amp; Video
---

### Post by phoenix23 on 2007-09-24
I used this command

ffmpeg -i movie.avi -vcodec wmv1 movie.wmv

But the video was barely watchable.

How might I go about converting .avi to .wmv so I can stream them to my 360?

---

### Post by kostkon on 2007-09-24
Why didn't you try the *wmv2* codec instead of the *wmv1*? Maybe you'll get better results. Also, I think you will have to play with bitrates, give it a video bitrate of at least 1000kbs.

---

### Post by bartsimson2315 on 2007-09-30
how do i change the ffmpeg bitrate?

---

### Post by blueorder on 2007-10-10
Here's a command that's worked for me:

```
ffmpeg -i movie.avi -s 320x240 -b 1000k -vcodec wmv2 -ar 44100 -ab 56000 -ac 2 -y movie.wmv
```

That command resizes the video to 320x240

---

### Post by bartsimson2315 on 2007-10-15
when i do that is says Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

---

### Post by jdzitro on 2007-10-18
I have been trying to find a solution for the AVI to WMV conversion as well.
(I want to put vids on my xbox)

I tried the example given and got the same output....

All I did before I plugged in my file to the example was 
*sudo apt-get install ffmpeg*

It installed and then I ran this.
*/media/disk/Movies/Heroes$ ffmpeg -i "Heroes S01 E03 - Kindred.avi" -s 320x240 -b 1000k -vcodec wmv2 -ar 44100 -ab 56000 -ac 2 -y HeroesS02E03.wmv*

It output this.
[I]FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, avi, from 'Heroes S01 E03 - Kindred.avi':
  Duration: 00:42:33.7, start: 0.000000, bitrate: 1159 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 624x352, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
Output #0, asf, to 'HeroesS02E03.wmv':
  Stream #0.0: Video: wmv2, yuv420p, 320x240, q=2-31, 1000 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: mp2, 44100 Hz, stereo, 56000 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[wmv2 @ 0xb7e7d508]removing common factors from framerate
[mp2 @ 0xb7e7d508]bitrate 56000 is not allowed in mp2
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
[/I]

Input file is actually XVID.

---

### Post by lowebb on 2007-10-18
[quote] Stream #0.1: Audio: mp2, 44100 Hz, stereo, 56000 kb/s[\quote]

This is where you are getting the issue. My bet is you want to encode the audio as mp3 and not mp2. You'll need lame installed (and you may need to reinstall ffmpeg, not sure).

Add to your command "-acodec mp3" (or something like that anyway

---

### Post by Oen386 on 2007-11-13
Any luck with this?

---

### Post by EdgePulse on 2007-11-16
The thing you need to know to be able to play .wmv's on a Xbox360 is that the audio needs to be encoded as .wma aswell. When the audio is not encoded as .wma your xbox360 will not play the video.

So my question to you guys is; how do i encode the audio as wma?

Thanks!

---

### Post by lowebb on 2007-11-16
The thing you need to know about ffmpeg is it uses a lot of different tools to do its encoding. If you install from source and add all the prefix'es you need there is no reason why wma encoding is not possible. Having never down it I can only guess the added section to the command would be 

'-acodec wma'

the only thing you need to do is find a tool which can be used to encode to wma. Check lame, it might do it

---

### Post by EdgePulse on 2007-11-17
I will try this as soon as i get home.
I'll keep u guys posted.

Thanks!

---

### Post by blueorder on 2007-11-18
To encode the audio to wma use the flag:

```
-acoded wmav2
```

The problem is that Zune uses wmv3 not wmv2. Well, at least that is the problem I am having.

---

### Post by blueorder on 2007-11-18
> **jdzitro said:**
> I have been trying to find a solution for the AVI to WMV conversion as well.
(I want to put vids on my xbox)

I tried the example given and got the same output....

All I did before I plugged in my file to the example was 
*sudo apt-get install ffmpeg*

It installed and then I ran this.
*/media/disk/Movies/Heroes$ ffmpeg -i "Heroes S01 E03 - Kindred.avi" -s 320x240 -b 1000k -vcodec wmv2 -ar 44100 -ab 56000 -ac 2 -y HeroesS02E03.wmv*

It output this.
[I]FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Input #0, avi, from 'Heroes S01 E03 - Kindred.avi':
  Duration: 00:42:33.7, start: 0.000000, bitrate: 1159 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 624x352, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
Output #0, asf, to 'HeroesS02E03.wmv':
  Stream #0.0: Video: wmv2, yuv420p, 320x240, q=2-31, 1000 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: mp2, 44100 Hz, stereo, 56000 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[wmv2 @ 0xb7e7d508]removing common factors from framerate
[mp2 @ 0xb7e7d508]bitrate 56000 is not allowed in mp2
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
[/I]

Input file is actually XVID.

Try the command like this:

```

ffmpeg -i "Heroes S01 E03 - Kindred.avi" -s 320x240 -b 1000k -vcodec wmv2 -ar 44100 **-acodec wmav2** -ab **56k** -ac 2 -y HeroesS02E03.wmv

```

I bolded the parts I changed or added.

**EDIT:** by the way, I had to recompile ffmpeg from svn to get encoding for wmav2.

---

### Post by ZooDirt on 2007-11-19
AWSOME!!!  I've been looking for this forever.    I'm just starting down the path of learning to convert from one format to another.   I thought H264 was required to get a hi-def picture,  Is there such a thing as hi-def wmv?

I'm sure I'm confused/ignorant/misinformed, can someone straighten me out?

Thanks again, Fellas!!!!

---

### Post by misconfiguration on 2007-11-20
So far from what I understand is the XboX 360 with the Spring update Firmware can support the MPEG-4 container with wma audio codec or FAAC. I've personally been using FAAC while using Avidemux to convert. My problem lies here;

I'm wanting to write a Perl script to convert all of my media from my NAS server to the format the 360 can support. I'm using ushare to host the media the xbox is able to see them once they're in the proper format. 

I'm trying to find a command line option with ffmpeg so I can convert all 150gb of my DVD-Backup collection so I can simply stream everything over to my TV.  I've had successful conversions by using MPEG-4 container, FAAC audio codec and saving the file as movie_name.mov.

The xbox  is able to see these file formats fine, now I'm in the process of automating my tasks!

---

