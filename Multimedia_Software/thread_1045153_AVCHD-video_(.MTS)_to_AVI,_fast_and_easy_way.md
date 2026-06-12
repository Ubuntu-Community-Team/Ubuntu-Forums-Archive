---
title: "AVCHD-video (.MTS) to AVI, fast and easy way"
date: 2009-01-20
forum: Multimedia Software
---

### Post by uhappo on 2009-01-20
**[COLOR="Red"]EDITED FOR LATEST INFO[/COLOR]**

I just tried this again on a new install, 9.10 64-bit.

1. ```
sudo apt-get install build-essential subversion zlib1g-dev
```

2. ```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
cd mplayer
./configure
make
sudo make install
```

Then, just do it (this command does not downscale the picture)
```
mencoder 00001.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1920:1080
```

There's also another variation, a bit higher quality but about 3 or 4 times larger file size.. There's no point, actually, but anyway (if someone knows how to make video quality ALMOST identical but with smaller file size, let us know...)```
mencoder 00001.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vqscale=2 -fps 50 -vf scale=1920:1080
```

This script just works, just follow the commands above and you should be good with it!

And then converting the whole directory:

```
sudo apt-get install csh
```

Make a file, name it *convert* and place it in /bin -folder. Then open the convert-file and put the stuff in it:
```
#!/bin/csh

# For NTSC change -fps 50 tp -fps 60000/1001 below

foreach f ($*)
   mencoder $f -o ${f:r}.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1920:1080
end
```

Allow the file to execute as a program. Now, just go to your .MTS-folder and write
```
convert *.MTS
```

See all your files converting...

**[COLOR="Red"]ORIGINAL POST[/COLOR]**

[I]You probably don't need the codecs, but here they are anyway. Try first without them
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

Next
```

svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
./configure
make
make install

```

Then
```

mencoder 00001.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1280:720

```

This did change a .MTS-file, made with Sony DCR that outputs 1920x1080p-video, to 1280x720- AVI-video. I appears in your home folder. Nice and easy, and FAST! I had a 3,1gig MTS-video that lasted about 30 minutes. Transform took 60 minutes and resulted video was 1gig.

No more hazzles, this just works.[/I]

---

### Post by TVMA on 2009-01-21
This is something that I have been looking for, thank you. Worked like a champ!

:popcorn:

---

### Post by TVMA on 2009-01-21
uhappo:

I am ahving an issue with the audio / video sync:

I have .mts files I'm converting frm my AVCHD   JVC Everio cam.

Original files are like 1920

Your stuff is working, but the audio sync is just off, the audio is ahead from the video, is there an easy way to tweak that?

---

### Post by jtappin on 2009-01-26
> **TVMA said:**
> 
Your stuff is working, but the audio sync is just off, the audio is ahead from the video, is there an easy way to tweak that?

A guess here: uhappo has -fps 50, since you appear to be in the US, you probably have a NTSC camera with a real frame rate of 29.97 (30000/1001), so you should use -fps 60000/1001. (Omitting the fps altogether is equivalent to specifying 25 or 50).

---

### Post by uhappo on 2009-01-26
Hello!

Sorry for late reply, I was on the road..

So, about your problem. First, I had no idea how to help you, but this came to my mind:

I live in Europa, you in USA. Europa = PAL, USA = NTSC.

So, we have different frame per second-rates, PAL 25 and NTSC 30. Could be possible that PAL is 50 and NTSC 60 fps, I'm not that good with this, but anyway.

So, my bet is just change the script a bit
```

mencoder 00001.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 60 -vf scale=1280:720

```

That should do it!

---

### Post by uhappo on 2009-01-26
> **jtappin said:**
> A guess here: uhappo has -fps 50, since you appear to be in the US, you probably have a NTSC camera with a real frame rate of 29.97 (30000/1001), so you should use -fps 60000/1001. (Omitting the fps altogether is equivalent to specifying 25 or 50).

Haha, you were a bit faster, and a bit more precise.
```

mencoder 00001.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 60000/1001 -vf scale=1280:720

```
Should be the ticket

---

### Post by uhappo on 2009-01-26
By the way, what would be the best way to mod this script so it could convert all .MTS-files in that folder, in the same process? So I could just leave it on and it takes care of the whole package?

---

### Post by jtappin on 2009-01-26
> **uhappo said:**
> By the way, what would be the best way to mod this script so it could convert all .MTS-files in that folder, in the same process? So I could just leave it on and it takes care of the whole package?

How about:
```

#!/bin/csh

# For NTSC change -fps 50 tp -fps 60000/1001 below

foreach f ($*)
   mencoder $f -o ${f:r}.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1280:720
end

```

In bash it would be a little harder as it doesn't have the :r modifier. Then if you've saved it as [FONT="Courier New"]avc_conv[/FONT] you could use:
```

avc_conv *.MTS

```
Or any other appropriate glob.

---

### Post by uhappo on 2009-01-26
Wuhuu!!!

Thanks, jtappin!

---

### Post by citybird on 2009-03-25
gave this a go under 64 bit Ubuntu 8.10:

```
user@mycomputer:~/Videos$ mencoder 00009.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1280:720
MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x12b8800
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
[V] filefmt:29  fourcc:0x10000005  size:0x0  fps: 0.00  ftime:=0.0000
Input fps will be interpreted as 50.00 instead.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale w=1280 h=720]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=32000 sample-1)
[h264 @ 0xe28200]PAFF interlacing is not implemented
[h264 @ 0xe28200]concealing 3060 DC, 3060 AC, 3060 MV errors
VDec: vo config request - 1440 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
SwScaler: reducing / aligning filtersize 6 -> 8
SwScaler: reducing / aligning filtersize 6 -> 8
SwScaler: reducing / aligning filtersize 7 -> 6
SwScaler: reducing / aligning filtersize 7 -> 6
[swscaler @ 0xe20930]SwScaler: BICUBIC scaler, from yuv420p to yuv420p using MMX2
[swscaler @ 0xe20930]SwScaler: using 8-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xe20930]SwScaler: using 8-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xe20930]SwScaler: using n-tap MMX scaler for vertical scaling (YV12 like)
[swscaler @ 0xe20930]SwScaler: 1440x1080 -> 1280x720
videocodec: libavcodec (1280x720 fourcc=34504d46 [FMP4])
Selected font is fixed-width.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
[h264 @ 0xe28200]PAFF interlacing is not implementedb  A-V:0.000 [0:0]
[h264 @ 0xe28200]top block unavailable for requested intra mode at 14 1
[h264 @ 0xe28200]error while decoding MB 14 1, bytestream (29439)
[h264 @ 0xe28200]illegal short term buffer state detected
[h264 @ 0xe28200]concealing 6120 DC, 6120 AC, 6120 MV errors
[h264 @ 0xe28200]PAFF interlacing is not implementedb  A-V:0.002 [0:0]
[h264 @ 0xe28200]concealing 3060 DC, 3060 AC, 3060 MV errors
[h264 @ 0xe28200]PAFF interlacing is not implementedb  A-V:0.004 [0:0]
[h264 @ 0xe28200]concealing 6010 DC, 6010 AC, 6010 MV errors

1 duplicate frame(s)!
[h264 @ 0xe28200]PAFF interlacing is not implementedb  A-V:0.006 [0:0]
Segmentation fault
user@mycomputer:~/Videos$ 

```

Any advice on the seg fault?

---

### Post by uhappo on 2009-04-17
Huh, now that seems tricky one!

---

### Post by pcapazzi on 2009-05-08
Just wanted to say THANK YOU so much for posting this. I was using another program (mts2avi or something like that). I should've been using mencoder all along.

I had the same sync problem and this post solved it.... this is great! 

Also, for bash users you can go through a directory with the following:

> 
#!/bin/bash
for file in *.MTS
do
        outfile=${file%.MTS}.avi
        echo $file " " $outfile
        mencoder $file -o $outfile -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 60000/1001 -vf scale=1280:720
done


You can do more I suppose... make a processed directory and put the MTS files there and an output folder to put the .avi files with something like this after the mencoder command:

> 
         mv $file processed
         mv $outfile avi


Thanks again!

---

### Post by Wizzu on 2009-05-11
I've recently been trying to play with AVCHD video on Linux out of my Sony HDR-SR7 camera.
I also tried that mts2avi script, without much success. Using mencoder directly seems to work much better.

> **citybird said:**
> gave this a go under 64 bit Ubuntu 8.10:

```
user@mycomputer:~/Videos$ mencoder 00009.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1280:720
MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1 (C) 2000-2007 MPlayer Team

[ ... snip snip, extra stuff removed ... ]

[h264 @ 0xe28200]PAFF interlacing is not implementedb  A-V:0.006 [0:0]
Segmentation fault
user@mycomputer:~/Videos$ 

```Any advice on the seg fault?

I ran into the same issue, more or less. I found out I had to manually download and compile mplayer (& mencoder which comes with it), apparently the current mediubuntu-provided version does not work.
The version of mencoder from svn that I've compiled and which works is SVN-r29289-4.3.3.

See the first post of this thread for how to compile mplayer... You will need at least the build-essential and subversion packages installed (maybe others too). Also, it's not absolutely necessary, but probably a good idea to remove the mplayer package before doing the compile.

I also had issues with mencoder giving errors of "Too many video packets in the buffer:" and audio getting out of sync, these were solved by adding "-demuxer lavf" to the mencoder line.

Hope this helps!

---

### Post by akashiii on 2009-07-01
I am facing a different problem - compilation issue. 

When I checkout the latest version of mplayer. ./configure works fine, but when I run make, I get the errors below after about 10 minutes of compilation (I have build-essential installed). 

Can asomeone please tell me what I'm doing wrong here? (Incidentally I'm running a 32 bit version of Ubuntu 9.04)

Error dump:

```
cc -DHAVE_AV_CONFIG_H -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT    -c -o lcldec.o lcldec.c
lcldec.c:50:18: error: zlib.h: No such file or directory
lcldec.c:70: error: expected specifier-qualifier-list before 'z_stream'
lcldec.c: In function 'zlib_decomp':
lcldec.c:131: warning: implicit declaration of function 'inflateReset'
lcldec.c:131: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:132: error: 'Z_OK' undeclared (first use in this function)
lcldec.c:132: error: (Each undeclared identifier is reported only once
lcldec.c:132: error: for each function it appears in.)
lcldec.c:136: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:137: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:138: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:139: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:140: warning: implicit declaration of function 'inflate'
lcldec.c:140: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:140: error: 'Z_FINISH' undeclared (first use in this function)
lcldec.c:141: error: 'Z_STREAM_END' undeclared (first use in this function)
lcldec.c:145: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:147: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:150: error: 'LclDecContext' has no member named 'zstream'
lcldec.c: In function 'decode_init':
lcldec.c:544: error: 'Z_NO_COMPRESSION' undeclared (first use in this function)
lcldec.c:544: error: 'Z_BEST_COMPRESSION' undeclared (first use in this function)
lcldec.c:580: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:580: error: 'Z_NULL' undeclared (first use in this function)
lcldec.c:581: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:582: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:583: warning: implicit declaration of function 'inflateInit'
lcldec.c:583: error: 'LclDecContext' has no member named 'zstream'
lcldec.c:584: error: 'Z_OK' undeclared (first use in this function)
lcldec.c: In function 'decode_end':
lcldec.c:609: warning: implicit declaration of function 'inflateEnd'
lcldec.c:609: error: 'LclDecContext' has no member named 'zstream'
make[1]: *** [lcldec.o] Error 1
make[1]: Leaving directory `/home/akash/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] Error 2
akash@lenovo:~/mplayer$ 
```

---

### Post by Wizzu on 2009-07-01
> **akashiii said:**
> Can asomeone please tell me what I'm doing wrong here? (Incidentally I'm running a 32 bit version of Ubuntu 9.04)

Error dump:

```
cc -DHAVE_AV_CONFIG_H -I.. -I.. -Wundef -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99 -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -O4 -march=native -mtune=native -pipe -ffast-math -fomit-frame-pointer -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -Ilibdvdread4 -I.  -D_REENTRANT    -c -o lcldec.o lcldec.c
lcldec.c:50:18: error: zlib.h: No such file or directory
.....

```

Looks like you're missing zlib headers (at least). Check to see if you have the zlib1g-dev (or zlib1-dev) package installed, as well as zlib1g (or zlib1). You might be missing other -dev packages too that mplayer requires to compile, this being just the first of such error that you run into. If that's the case, check the mplayer documentation for a list of required packages (software) to build. build-essential is not enough in itself for mplayer, it just means you can build software in general.
 
I would imagine configure is meant to handle this stuff and complain if something required is missing, strange that it doesn't.

---

### Post by akashiii on 2009-07-01
Thanks a lot, Wizzu. As configure went smoothly without complaining, I was wondering if I had messed up somewhere. Anyway, including zlib1g-dev did the trick. 

For the benefit of those who might run into this, you will need build-essential, subversion and zlib1g-dev for compilation to succeed (on a clean Ubuntu Jaunty install).

```
sudo apt-get install build-essential subversion zlib1g-dev
```

Cheers!

---

### Post by ziaziu on 2009-07-02
Thank you all for the great solution!  I found using m2ts2avi a bit strange and never got the results I wanted. Basically the sound was gone/deformed and the picture was totally mashed.  With this everything is in sync and well done :D  Thanks!

---

### Post by mashedbear on 2009-07-12
I think I have been trying to solve the same problem using ffmpeg - without much success - you can read about my efforts [here]("http://ubuntuforums.org/showthread.php?t=1180261") 

Have tried the mencoder commands and am getting the same segmentation error. 

```
[h264 @ 0xe271a0]MBAFF + spatial direct mode is not implemented
[h264 @ 0xe271a0]concealing 3060 DC, 3060 AC, 3060 MV errors
Pos:  20.2s   1013f (100%) 14.92fps Trem:   0min  25mb  A-V:0.020 [10002:448]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 10002.628 kbit/s  (1250328 B/s)  size: 25281643 bytes  20.220 secs  1013 frames

Audio stream:  448.000 kbit/s  (56000 B/s)  size: 1134336 bytes  20.256 secs
Segmentation fault
```

I am using MEncoder 2:1.0~rc2-0ubuntu19 on 64bit Ubuntu 9.04 

I have tried to follow uhappo's instructions to install mplayer & mendocer from svn and build from source. But I haven't built software form source before and I can't seem to get this to work.

Could someone jot down an idiots step by step guide to doing this - or point me in the right direction. Do I need to remove the installed mplayer first? Where should I make and install the new version on my system - my home directory? Where do I put the codecs uhappo linked to ([http://www.mplayerhq.hu/design7/dload.html)?](http://www.mplayerhq.hu/design7/dload.html)?) 

Thanks!

---

### Post by Oiolosse on 2009-10-27
I am getting the same errors as mashedbear:

[h264 @ 0xe271a0]MBAFF + spatial direct mode is not implemented
[h264 @ 0xe271a0]concealing 3060 DC, 3060 AC, 3060 MV errors

Any help would be much appreciated!

---

### Post by Jepic Phail on 2009-11-10
Can someone here explain to me these "duplicate frame(s)!" errors? I googled the error messages, but I lack the technical knowledge and I can't understand them.

Thank you.

```
zombie@ubuntu:~/Videos$ mencoder 00001.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1280:720
MEncoder SVN-r29851-4.4.1 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x26adc800
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4352) NO SUBS (yet)!  PROGRAM N. 1
FPS seems to be: 29.970030
[V] filefmt:29  fourcc:0x10000005  size:0x0  fps:29.970  ftime:=0.0334
Input fps will be interpreted as 50.000 instead.
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 0
Opening video filter: [scale w=1280 h=720]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=32000 sample-1)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect..000 [0:0]
[swscaler @ 0xa280310]BICUBIC scaler, from yuv420p to yuv420p using MMX2
videocodec: libavcodec (1280x720 fourcc=34504d46 [FMP4])
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.0s      3f ( 0%)  0.00fps Trem:   4min  77mb  A-V:0.004 [0:0]
1 duplicate frame(s)!
Pos:   0.0s      4f ( 0%)  0.00fps Trem:   4min  77mb  A-V:0.006 [0:0]
1 duplicate frame(s)!
Pos:   0.1s      5f ( 0%)  0.00fps Trem:   4min  77mb  A-V:0.008 [0:0]
1 duplicate frame(s)!
Pos:   0.1s      6f ( 0%)  0.00fps Trem:   4min  77mb  A-V:0.006 [0:0]
1 duplicate frame(s)!
Pos:   0.1s      7f ( 0%)  0.00fps Trem:   5min  77mb  A-V:0.006 [0:0]
1 duplicate frame(s)!
Pos:   0.1s      8f ( 0%)  0.00fps Trem:   5min  77mb  A-V:0.008 [0:0]
1 duplicate frame(s)!
Pos:   0.1s      9f ( 0%)  0.00fps Trem:   6min  77mb  A-V:0.010 [0:0]
1 duplicate frame(s)!
Pos:   0.2s     11f ( 0%)  0.00fps Trem:   7min  91mb  A-V:0.014 [0:0]
1 duplicate frame(s)!
[h264 @ 0xa27f8a0]left block unavailable for requested intra mode at 0 16
[h264 @ 0xa27f8a0]error while decoding MB 0 16, bytestream (24406)

```

---

### Post by uhappo on 2010-01-16
I just tried this again on a new install, 9.10 64-bit.

1. ```
sudo apt-get install build-essential subversion zlib1g-dev
```

2. ```
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
cd mplayer
./configure
make
sudo make install
```

Then, just do it (this command does not downscale the picture)
```
mencoder 00001.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1920:1080
```

There's also another variation, a bit higher quality but about 3 or 4 times larger file size.. There's no point, actually, but anyway (if someone knows how to make video quality ALMOST identical but with smaller file size, let us know...)```
mencoder 00001.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vqscale=2 -fps 50 -vf scale=1920:1080
```

This script just works, just follow the commands above and you should be good with it!

And then converting the whole directory:

```
sudo apt-get install csh
```

Make a file, name it *convert* and place it in /bin -folder. Then open the convert-file and put the stuff in it:
```
#!/bin/csh

# For NTSC change -fps 50 tp -fps 60000/1001 below

foreach f ($*)
   mencoder $f -o ${f:r}.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1920:1080
end
```

Allow the file to execute as a program. Now, just go to your .MTS-folder and write
```
convert *.MTS
```

See all your files converting...

---

### Post by boo12345679 on 2010-01-30
Thank you for some excellent advice, very much appreciated. 

This has worked for me, however when viewing the .avi the picture is not clear at all.  

So the conversion worked and a standard player can see the .avi, but the picture or sound is not clear.  

I get the following errors on the conversion - not sure if this is standard or not ?  Can anyone assist.   (there are pages and pages of it) 

[h264 @ 0x8815750]mb_type 27 in B slice too large at 77 1
[h264 @ 0x8815750]error while decoding MB 77 1
[h264 @ 0x8815750]concealing 6120 DC, 6120 AC, 6120 MV errors
[h264 @ 0x8815750]PAFF interlacing is not implemented  A-V:0.032 [10655:256]
[h264 @ 0x8815750]concealing 3060 DC, 3060 AC, 3060 MV errors
[h264 @ 0x8815750]PAFF interlacing is not implemented  A-V:0.030 [10644:256]
[h264 @ 0x8815750]negative number of zero coeffs at 40 1
[h264 @ 0x8815750]error while decoding MB 40 1
[h264 @ 0x8815750]illegal short term buffer state detected
[h264 @ 0x8815750]concealing 6120 DC, 6120 AC, 6120 MV errors
[h264 @ 0x8815750]PAFF interlacing is not implemented  A-V:0.030 [10652:256]
[h264 @ 0x8815750]concealing 3060 DC, 3060 AC, 3060 MV errors
[h264 @ 0x8815750]PAFF interlacing is not implemented  A-V:0.032 [10651:256]
[h264 @ 0x8815750]mb_type 54 in B slice too large at 86 1
[h264 @ 0x8815750]error while decoding MB 86 1
[h264 @ 0x8815750]concealing 6083 DC, 6083 AC, 6083 MV errors
[h264 @ 0x8815750]PAFF interlacing is not implemented  A-V:0.032 [10650:256]
[h264 @ 0x8815750]concealing 3060 DC, 3060 AC, 3060 MV errors
[h264 @ 0x8815750]PAFF interlacing is not implemented  A-V:0.034 [10648:256]
[h264 @ 0x8815750]cbp too large (65) at 83 2

[h264 @ 0x8815750]PAFF interlacing is not implementedb  A-V:0.032 [10400:255]
[h264 @ 0x8815750]concealing 3060 DC, 3060 AC, 3060 MV errors
Pos:  12.4s    623f (100%) 13.55fps Trem:   0min  15mb  A-V:0.034 [10390:255]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 10390.797 kbit/s  (1298849 B/s)  size: 16105736 bytes  12.400 secs  623 frames

Audio stream:  256.000 kbit/s  (31999 B/s)  size: 398336 bytes  12.448 secs

My player is JVC Everio and I am in the UK.  1920 output is the highest quality I am working with. 

Im on Ubuntu 8.04 32 Bit version

---

### Post by heracles on 2010-02-15
Being the thicko of all time I am having difficulty in following your excellent and well prepared conversion method. Where is the bin folder you refer to and how do I make a file called convert?

---

### Post by uhappo on 2010-02-15
> **heracles said:**
> Being the thicko of all time I am having difficulty in following your excellent and well prepared conversion method. Where is the bin folder you refer to and how do I make a file called convert?

Maybe easiest way could be:
```
gksudo gedit /bin/convert
```

Then place```

#!/bin/csh

# For NTSC change -fps 50 tp -fps 60000/1001 below

foreach f ($*)
   mencoder $f -o ${f:r}.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1920:1080
end
```
inside that file and tada!

---

### Post by Wizzu on 2010-03-20
> **uhappo said:**
> Maybe easiest way could be:
```
gksudo gedit /bin/convert
```

You'll need to also do this: ```
gksudo chmod a+x /bin/convert
```I would also recommend using a different name eg. *convertmts*, since convert is a program coming with imagemagick (image converter). Not that everyone has that installed, but still.

---

### Post by uhappo on 2010-03-22
> **Wizzu said:**
> You'll need to also do this: ```
gksudo chmod a+x /bin/convert
```I would also recommend using a different name eg. *convertmts*, since convert is a program coming with imagemagick (image converter). Not that everyone has that installed, but still.

You're right. You can use whatever you like, convertmts etc.

But the main point is that this method works once it's done!

---

### Post by doriad on 2010-10-08
I tried this:
```

mencoder 00050.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 60000/1001 -vf scale=1280:720

```

but the resulting video is in slow motion. Any ideas?

David

---

### Post by andrew.46 on 2010-10-09
Hi uhappo,

Does adding *vhq:v4mv:trell* add much to the quality of the encoding? That is:

```

-lavcopts vcodec=mpeg4:vhq:v4mv:trell:vqscale=3

```

which in theory should give better quality with equivalent or smaller filesize. Other options are available of course but this might be a simple and effective addition?

Andrew

---

### Post by sirpy on 2012-01-19
I've tried many mencoder settings found in various forums to convert my sony cybershot mts files, but usually it resulted either in slow motion or audio out of sync.

finnaly i found settings that worked in this blog:
[http://publicvideos.posterous.com/how-to-convert-avchd-mts-files-to-diracogg-th]("http://publicvideos.posterous.com/how-to-convert-avchd-mts-files-to-diracogg-th")

mencoder inputfile -fps 50 -oac pcm -demuxer lavf -vf pp=ci,detc,softskip,scale=1440:1080 -ofps 25 -ovc lavc -lavcopts vcodec=mpeg4:format=YV12:vstrict=-1:aspect=16/9:vqscale=1 -o outputfile

---

### Post by uniomni on 2012-09-25
Didn't work for me.
The MTS files come from a Sony CX760 camcorder and I am running Ubuntu 11.04, 32 bit.

Running any of the mencoder commands mentioned, e.g.

[FONT="Courier New"]mencoder 00001.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1920:1080[/FONT]

invariable gives an error about 40 seconds into the conversion:


[FONT="Courier New"]1 duplicate frame(s)!
Pos:  68.1s   1903f ( 6%) 41.14fps Trem:  10min 373mb  A-V:0.019 [2770:448]
Too many video packets in the buffer: (319 in 33583582 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.[/FONT]


The -ni option doesn't affect this issue. Also, mencoder normally works for me on other file formats. Can someone please let me know how to get the MTS files converted (so that I can e.g. edit with OpenShot).

Many thanks
Ole

---

