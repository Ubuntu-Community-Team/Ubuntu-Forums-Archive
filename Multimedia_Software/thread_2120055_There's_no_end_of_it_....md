---
title: "There's no end of it ..."
date: 2013-02-25
forum: Multimedia Software
---

### Post by Langstracht on 2013-02-25
I think that:

ffmpeg -ss 00:02:22 -t 3126 -i infile.m4v -acodec copy -vcodec copy out.m4v

should cull 52 minutes and 6 seconds out of infile.m4v starting at 2 minutes and 22 seconds from the start of the file and write a new clip to out.m4v.

In the event it does not.

The out.m4v clip starts at 2:22 ... but it finishes at the end of the infile.m4v some 7 minutes later.

So:

am I misunderstanding this capability?

or, is my command incorrect?

or, is this a known problem?

TIA

---

### Post by FakeOutdoorsman on 2013-02-25
Please include the complete ffmpeg console output.

---

### Post by Langstracht on 2013-02-25
If, by that, you mean what appeared in the window as the command ran, I am afraid I cannot, as I did not save it.

Unless perhaps it's stored away in a log file somewhere, the location of which I am unaware of.

I take it from your reply that the command line "is correct" and therefore "should work".

If that's so I will try it with another file and save the listing.

But confirmation of the above would be most appreciated.

TIA

---

### Post by FakeOutdoorsman on 2013-02-25
Your command could be correct, but you could be encountering a bug. The output contains useful information including your ffmpeg version. Note that ["-ss" behavior](http://stackoverflow.com/a/12208967/1109017) changes depending if it is used as an input option (before "-i") or an output option.

---

### Post by evilsoup on 2013-02-25
> **FakeOutdoorsman said:**
> Your command could be correct, but you could be encountering a bug. The output contains useful information including your ffmpeg version. Note that ["-ss" behavior]("http://stackoverflow.com/a/12208967/1109017") changes depending if it is used as an input option (before "-i") or an output option.

Also, -t is only an output option - so it should be placed after all the inputs. I don't think that's the cause of the OP problem, though; the OP is using -t with a time value longer than the input file, so of course ffmpeg stops at the end of the input file.

Langstracht, what exactly are you trying to accomplish? Are you trying to add black video & silent audio to the end of the video, or something else?

---

### Post by Langstracht on 2013-02-26
I tried the command again before I read the "-t" location "issue".

The result was the same, it did not stop/cut off after the -t value.

Here's the listing:

ffmpeg -ss 00:38:24 -t 6756 -i infile.m4v -acodec copy -vcodec copy out.m4v
FFmpeg version SVN-r0.5.9-4:0.5.9-0ubuntu0.10.04.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.9-0ubuntu0.10.04.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 24 2013 19:42:21, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 180000.00 (180000/1) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'infile.m4v':
  Duration: 03:00:15.14, start: 0.-133467, bitrate: 698 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 352x480, PAR 20:11 DAR 4:3, 29.97 tbr, 90k tbn, 180k tbc
    Stream #0.1(und): Audio: aac, 48000 Hz, stereo, s16
    Stream #0.2(und): Subtitle: text / 0x74786574
Output #0, ipod, to 'out.m4v':
    Stream #0.0(und): Video: libx264, yuv420p, 352x480 [PAR 20:11 DAR 4:3], q=2-31, 90k tbn, 90k tbc
    Stream #0.1(und): Audio: 0x0000, 48000 Hz, stereo, s16
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=254837 fps=8795 q=-1.0 Lsize=  736428kB time=8510.89 bitrate= 708.8kbits/s    
video:563168kB audio:166268kB global headers:0kB muxing overhead 0.958563%

I will go try again with the -t in the "right" place.

I had thought that what I have been trying to do was obvious.  Sorry that it was not.

I am trying to get (in this latest case) 01:52:36 of video out of a file which is 03:00:15 starting at 00:38:24.  Just lop off the ends - nothing else.

Be back at ya after I get my "t".

---

### Post by Langstracht on 2013-02-26
O.K. I did it again with -t 6756  at the end.

Alas it made no difference.

---

### Post by FakeOutdoorsman on 2013-02-26
What is wrong with "out.m4v", exactly, from your latest command?

FFmpeg version SVN-r0.5.9-4:0.5.9 is old. I'm not totally clear right now as to what the issue is, but using a newer version is always a good idea when things are not working as expected. You can try a [recent static build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds). No need to install or compile: just download the archive file, extract, and run the binary.

Wrapping the console outputs in the [code] tags will make it easier to differentiate from your comments.

---

### Post by Langstracht on 2013-02-26
I profusely apologize - evidently my English is a whole lot less competent than I thought.

At the risk of being tautological and pedantic, I have a video file which is 03:00:15 long.

I wish to extract a segment 01:52:36 from this file, starting at 00:38:24 and continuing for 6752 seconds.

When I execute the above command, instead I get a file which commences at the aforementioned 00:38:24 but does NOT stop after 6752 seconds.  Instead continuing to the end of the file - resulting in an out.m4v of 02:21:51.

If this is STILL unclear please do ask for further clarification.

I would be happy to download the archive file, extract, and run the binary.  Unfortunately I don't know how to "run the binary".

I understand that "Wrapping the console outputs in the [code] tags will make it easier to differentiate" from my comments. Alas I don't know how to do that either.

---

### Post by FakeOutdoorsman on 2013-02-26
> **Langstracht said:**
> If this is STILL unclear please do ask for further clarification.
I understand now. Thanks for the further explanation.

> **Langstracht said:**
> I would be happy to download the archive file, extract, and run the binary.  Unfortunately I don't know how to "run the binary".

At this point I'm unsure if there is a static build available for your system due to the age of your kernel (there are 64-bit builds available for your kernel I think). The output of the following command will tell you your kernel info:
```
uname -a
```

Or you can quickly compile ffmpeg just to test if you're experiencing an already-fixed-bug:
```

sudo apt-get install build-essential wget
cd
wget https://ffmpeg.org/releases/ffmpeg-snapshot.tar.bz2
tar xjvf ffmpeg-snapshot.tar.bz2
cd ffmpeg
./configure --disable-yasm
make -j2
```

When *make* finishes you will end up with a ffmpeg binary. No need to install or anything. Now you can try it:
```
cd ~/ffmpeg
./ffmpeg -ss 00:38:24 -i ~/infile.m4v -t 01:52:36 -acodec copy -vcodec copy ~/out.m4v
```
Note that this command assumes that infile.m4v is in your home directory, and that you would want out.m4v in the home directory as well.

> **Langstracht said:**
> I understand that "Wrapping the console outputs in the ```
 tags will make it easier to differentiate" from my comments. Alas I don't know how to do that either.

There should be a code button above the message box, or you can simply do this:

[noparse][code]commands and console outputs go here
```[/noparse]

---

### Post by Langstracht on 2013-02-27
I actually use two machines (both of which get the same - rather disappointing - result).  The results of uname -a respectively are:

3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

2.6.32-45-generic #104-Ubuntu SMP Tue Feb 19 21:21:41 UTC 2013 i686 GNU/Linux

Hopefully the significance of that will mean something to you.  Alas it means nothing to me.


You wrote (and I can see no "quote" or "code" button) "Or you can quickly compile ffmpeg just to test if you're experiencing an already-fixed-bug;"

Do you think that what's happening is a bug - fixed or not - or could it be that the code is flawed?

And, given the kernels, am I "o.k." to download the "new" version of ffmpeg?

---

### Post by andrew.46 on 2013-02-27
> **Langstracht said:**
> (and I can see no "quote" or "code" button) 

Possibly you don't have the right controls defined in your forum setup, I show the 'Code' button in the attached screenshot...

---

### Post by FakeOutdoorsman on 2013-02-27
> **Langstracht said:**
> 
```
3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
```

```
2.6.32-45-generic #104-Ubuntu SMP Tue Feb 19 21:21:41 UTC 2013 i686 GNU/Linux
```
As far as I know static builds are not available for either machine, but you can still compile by following the instructions from my previous post in this thread.

> **Langstracht said:**
> Hopefully the significance of that will mean something to you.  Alas it means nothing to me.

Static builds from *burek* require kernel 3.2.x+, and both 32 and 64 bit versions are provided. Static builds from *relaxed* require kernel 2.6.26+, and only 64 bit version are supplied.

> **Langstracht said:**
> You wrote (and I can see no "quote" or "code" button)
I don't have a code button either. Actually, I have no buttons, but you can type it manually as shown in my previous post, or refer to the [BB code list](http://ubuntuforums.org/misc.php?do=bbcode) for this forum.

> **Langstracht said:**
> Do you think that what's happening is a bug - fixed or not - or could it be that the code is flawed?
I'm not sure. That's what I'm trying to find out. Your command is probably fine.

> **Langstracht said:**
> And, given the kernels, am I "o.k." to download the "new" version of ffmpeg?
No, apparently the kernels are too old and/or you're on a 32 bit system. Try compiling.

---

