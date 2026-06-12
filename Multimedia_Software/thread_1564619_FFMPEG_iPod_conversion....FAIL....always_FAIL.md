---
title: "FFMPEG iPod conversion....FAIL....always FAIL"
date: 2010-08-30
forum: Multimedia Software
---

### Post by PDA1 on 2010-08-30
I've been trying to convert flv videos to MP4 so that I can load them onto my iPod Classic 160 G (video).

So far no program has successfully converted an flv file to a usable mp4.

I've tried Avidemux (both gtk and qt), Kdenlive, WinFF, Mobile Media Converter, DownloadHelper (FireFox addon) Tragtor and of course the King of them all- FFMPEG.
Not one of the previously mentioned programs has successfully and consistently converted an FLV to mp4 for my ipod.

It could be that I'm doing something wrong with FFMPEG or don't have the correct codecs (whatever the heck they are?!)  installed or that I voted for McGovern in '68.  The &quot;help&quot; from FFMPEG both IRC and their obnoxious email list is beyond deplorable.  

Anyway, I need to know a reliable and consistent way to turn flv or any other videos into an MP4 format that will run on my iPod.  The program must reside on my machine and not some online converter service.  If I have to use FFMPEG (which I understand most programs use as their core) I need to know how to do it....and for God's sake don't tell me to read the online documentation at FFMPEG......that stuff's not written for anyone but techno-geeks to understand and it's certainly not helpful.  

Any ideas?

---

### Post by FakeOutdoorsman on 2010-08-30
See my iPod example for FFmpeg here:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

If you use my example and recieve an error like this (it will probably be in [color=#FF0000]red[/color]):
```
[color=#FF0000][libx264 @ 0x30a0d30] width or height not divisible by 2 (320x181)[/color]
```
Then simply change the scale height value to the closest even number:
```
-vf 'scale=320:180'
```

---

### Post by PDA1 on 2010-08-31
I just installed the stuff mentioned under this-

[SIZE=1]Note: Those who are uncomfortable compiling can still enable additional encoders in the repository FFmpeg:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283")


I selected the Mediabuntu stuff.


Is that all I need do?

I've read many of your posts here and they are always helpful.  

Thank you
[/SIZE]

---

### Post by PDA1 on 2010-08-31
I used your example, below, and changed the input and output file names to the ones I'm working with- 

ffmpeg -i t.flv -acodec libfaac -aq 100 -ac 2 -vcodec libx264 -vpre fastfirstpass -vpre ipod640 -crf 26 -map_meta_data 0:0 -vf scale=640:-1 -threads 0 output.mp4


The error message that came back was-

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 59.75 (239/4)
Input #0, flv, from 't.flv':
  Duration: 00:02:00.06, start: 0.000000, bitrate: 285 kb/s
    Stream #0.0: Video: flv, yuv420p, 400x226, 253 kb/s, 59.75 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 32 kb/s
ffmpeg: unrecognized option '-vf'


Any idea how to fix this?

---

### Post by FakeOutdoorsman on 2010-08-31
> **PDA1 said:**
> I used your example, below, and changed the input and output file names to the ones I'm working with- 

ffmpeg -i t.flv -acodec libfaac -aq 100 -ac 2 -vcodec libx264 -vpre fastfirstpass -vpre ipod640 -crf 26 -map_meta_data 0:0 -vf scale=640:-1 -threads 0 output.mp4


The error message that came back was-

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 59.75 (239/4)
Input #0, flv, from 't.flv':
  Duration: 00:02:00.06, start: 0.000000, bitrate: 285 kb/s
    Stream #0.0: Video: flv, yuv420p, 400x226, 253 kb/s, 59.75 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 32 kb/s
ffmpeg: unrecognized option '-vf'


Any idea how to fix this?
FFmpeg libraries from Medibuntu are currently too old (Lucid and older) to use the *-vf scale* option.  You can simply manually provide an output size with *-s* instead.  Also, you probably should not use the *fastfirstpass* preset unless you're doing a two-pass encode.  I changed it to *fast* in this ipod640 example.
```
ffmpeg -i t.flv -acodec libfaac -aq 100 -ac 2 -vcodec libx264 -vpre fast -vpre ipod640 \
-crf 26 -map_meta_data 0:0 -s 640x480 -threads 0 output.mp4
```
or for ipod320:
```
ffmpeg -i t.flv -acodec libfaac -aq 100 -ac 2 -vcodec libx264 -vpre fast -vpre ipod320 \
-crf 26 -map_meta_data 0:0 -s 320x240 -threads 0 output.mp4
```
*-vf scale* can automatically determine the appropriate width or height while *-s* can not do this.  For example, *-vf scale=640:-1* tells FFmpeg to make the output video 640 pixels wide, and then automatically resize the height to preserve the aspect ratio.  If you want to use this option, then you will either need to use Ubuntu Maverick Meerkat, or compile FFmpeg:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

**Update:** I think [Handbrake](http://handbrake.fr/downloads.php) may have an iPod preset.  I'm not sure though.  Did you try Handbrake?  If you prefer a GUI, it might be worth a try.

---

### Post by PDA1 on 2010-08-31
I followed the installation per your link- [HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")


Yes, I tried out Handbrake with the same poor results.

I'll try out your code recommendations later and will get back to you.

Thanks for the help.

---

### Post by PDA1 on 2010-08-31
I tried the code- 

[B]ffmpeg -i t.flv -acodec libfaac -aq 100 -ac 2 -vcodec libx264 -vpre fast -vpre ipod640 \
-crf 26 -map_meta_data 0:0 -s 640x480 -threads 0 output.mp4 [/B]

Here are the results......


[B]bob@bob-laptop:~/Desktop$ ffmpeg -i t.flv -acodec libfaac -aq 100 -ac 2 -vcodec libx264 -vpre fast -vpre ipod640 \
> -crf 26 -map_meta_data 0:0 -s 640x480 -threads 0 output.mp4
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr  --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib  --enable-libgsm --enable-libschroedinger --enable-libspeex  --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib  --disable-stripping --disable-vhook --enable-runtime-cpudetect  --enable-gpl --enable-postproc --enable-swscale --enable-x11grab  --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (2997/50) -> 29.92 (359/12)[/B] [B]
Input #0, flv, from 't.flv':
  Duration: 00:02:56.00, start: 0.000000, bitrate: 820 kb/s
    Stream #0.0: Video: h264, yuv420p, 640x356 [PAR 1:1 DAR 160:89], 820 kb/s, 29.92 tbr, 1k tbn, 59.94 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
File for preset 'fast' not found
bob@bob-laptop:~/Desktop$ 
[/B] 

I notice that FFMPEG returned the error that the preset 'fast" wasn't found.  

Is it correct to  assume the only h264 presets I have are located in my folder /usr/share/ffmpeg?

Below is a picture of my presets.

So, since the 'fast' preset doesn't appear in my** /usr/share/ffmpeg** folder I assume the code you provided with the -vpre 'fast' would indeed produce the error provided above.  Is that correct?

When I let Terminal run the following code-

[B]ffmpeg -i t.flv -acodec libfaac -aq 100 -ac 2 -vcodec libx264 -vpre default -vpre ipod640 \
-crf 26 -map_meta_data 0:0 -s 640x480 -threads 0 output.mp4[/B]

I read someplace on here to just do the following command;

**ffmpeg -i INPUT_FILE.flv  -sameq OUTPUT.MP4**

Why not just use that code instead?

I got the result I was looking for.  However, I haven't loaded the converted mp4 over to iTunes (windows).  I'll do that tomorrow morning.

---

### Post by FakeOutdoorsman on 2010-09-01
> **PDA1 said:**
> 
```
File for preset 'fast' not found
```
The *fast* preset isn't working for you because you're using FFmpeg from the Ubuntu repository as shown by *FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1*.  FFmpeg from the Ubuntu repository is too old to use the *fast* preset, but the following presets will work: *hq*, *default*, or *normal*.

> **PDA1 said:**
> Is it correct to assume the only h264 presets I have are located in my folder /usr/share/ffmpeg?
Yes.

> **PDA1 said:**
> I read someplace on here to just do the following command;
```
ffmpeg -i INPUT_FILE.flv -sameq OUTPUT.MP4
```
Why not just use that code instead?
That may work for you, but there are several things to be aware of.  The *-sameq* option does not always work as expected.  Your input and output must use the same "quantizer scale" for it to work effectively.  For example, a Theora input and a H.264 output should not use *-sameq* because they do not share the same quantizer scale.  A better option in most cases to to use *-qscale* instead of *-sameq*.  For MPEG-1/2/4 outputs (such as your example above) *-qscale 2* is just about visually lossless, and 3-5 is a good balance between quality and output file size.

The audio quality of that command will suffer because by default FFmpeg will encode with an audio bitrate of 64 kbits/s which is low for most inputs.

That command may also result in a significantly larger file size for a similar quality level and it won't necessarily be a faster encode.

---

### Post by PDA1 on 2010-09-01
I'm going to give your ideas a try.   I really appreciate you taking the time to help me out with this problem.

I'll go back and re-do the installation you recommended previously.  I thought I did it correctly.  

What I SHOULD do is completely remove FFMPEG from my machine. 

If I remove it via Synaptic would that completely remove everything related to FFMPEG or are there infinite parts of the program all over my machine?

Thanks.


P.S.  What I haven't mentioned is that TragTor converts flv's to MP4's with no trouble at all.  I just want to be able to use FFMPEG in all of it's glory by itself and with other problems like Avidemux, etc.

---

### Post by llawwehttam on 2010-09-01
I use:

```
ffmpeg -i input.flv -acodec libfaac -ab 96k -ac 2 -vcodec libx264 -vpre hq -vpre ipod320 -threads 0 -crf 22 output.mp4
```

And it works OK. Quality is not amazing though.

Sorry if you saw the un-edited post. I copied and pasted the wrong line.

---

### Post by andrew.46 on 2010-09-01
Hi llawwehttam,

> **llawwehttam said:**
> Quality is not amazing though.

Just for curiosity can I ask what was the quality like for the original file?

Andrew

---

### Post by PDA1 on 2010-09-01
I hope you folks have a sense of humor.......

I just installed FFMPEG and all the other stuff from your suggestions link in your FakeOutdoorsman first reply.

Guess what?  You won't believe this....but the FFMPEG I had installed I got off of a Youtube video made by some foul mouthed guy and his method of installing it.  Well, it was the wrong one.  I thought I had installed it per Fake's method.....but that was my other machine...and it works fine (I guess.....I don't use the other rig much).

Thanks for your patience- your solution, hopefully, solved my problem.  I let you know tomorrow if the conversions I did will load onto my iPod.

---

### Post by FakeOutdoorsman on 2010-09-01
> **PDA1 said:**
> I'll go back and re-do the installation you recommended previously.  I thought I did it correctly.
You can still use FFmpeg from the repository if you don't want to compile.  You will just need to get a package from the Medibuntu repository as shown here (see *Option C: Medibuntu*):

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

This will allow you to keep using any program that depends on FFmpeg.  You will just need to use one of the older presets that I mentioned before: *hq*, *default*, or *normal*.

> **PDA1 said:**
> What I SHOULD do is completely remove FFMPEG from my machine.
It depends on how you installed it, but most of the time you can just go into Synaptic and remove it from there.  Anything that depends on FFmpeg will also be removed.  They can be easily installed later.  Ubuntu keeps a cache of downloaded packages so you may not need to re-download them.

> **PDA1 said:**
> P.S.  What I haven't mentioned is that TragTor converts flv's to MP4's with no trouble at all.  I just want to be able to use FFMPEG in all of it's glory by itself and with other problems like Avidemux, etc.
I've never used TragTor.  Keep in mind that .mp4 is a container format and can handle several types of video formats such as MPEG-4 and H.264.  I took a look at TragTor and it seems unable to encode to H.264.

---

### Post by PDA1 on 2010-09-03
So far so good.  The processing of various flv files to mp4 worked perfectly and could be loaded onto my iPod using iTunes.

Thanks for the help.

---

