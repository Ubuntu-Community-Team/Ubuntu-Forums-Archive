---
title: "How to install avconv/libvo-aacenc on ubuntu 10.04"
date: 2011-10-20
forum: Multimedia Software
---

### Post by shekarkcb on 2011-10-20
I got below command to do 2 pass encoding movie file and overlay image on the movie
```


avconv -i $1 -pass 1 \
-vf 'movie=logo.png,setpts=PTS-STARTPTS [logo]; [in][logo] overlay=W-w-20:H-h-22 [out]' \
-vcodec libx264 -preset veryslow -b 1300k -maxrate 1600k -bufsize 900k -threads 0 -refs 6 -f h264 -y /dev/null &> pass1.log "$@"

sleep 10

### Pass 2

avconv -f yuv4mpegpipe -i - -pass 2 \
-vf 'movie=logo.png,setpts=PTS-STARTPTS [logo]; [in][logo] overlay=W-w-20:H-h-22 [out]' \
-vcodec libx264 -preset veryslow -b 1300k -maxrate 1600k -bufsize 900k -threads 0 -refs 6 -y video.h264 &>pass2.log "$@"

avconv -i "$@" -vn -acodec libvo_aacenc -ac 2 -ab 96k -y audio.aac 2>&1 | tee audio.log
 
avconv -f h264 -i video.h264 -i audio.aac -metadata title="sample video" -vcodec copy -acodec copy -absf aac_adtstoasc -y temp.mp4 2>&1 | tee mux.log

```Hence using avconv to do 2 pass encoding for movie file and overlaying logo on the movie.
I downloaded libav-0.7.2 tar file, while configuring it says
```

shekar@x264Encoder:~/Desktop/shekar/libav-0.7.2$ ./configure --enable-libx264 --enable-gpl --enable-version3 --enable-libvo-aacenc

ERROR: libvo_aacenc not found

If you think configure made a mistake, make sure you are using the latest
version from Git.  If the latest version fails, report the problem to the
libav-user@libav.org mailing list or IRC #libav on irc.freenode.net.
Include the log file "config.log" produced by configure as this will help
solving the problem.
shekar@x264Encoder:~/Desktop/shekar/libav-0.7.2$

```I couldn't find package 'libvo-aacenc for unbunto 10.04. Can anybody point me where i am doing wrong?

Thanks

---

### Post by BicyclerBoy on 2011-10-20
If you run:
./configure --help

you should get a list of possible options..
I imagine you need a good 3 lines of options not just a couple as you have...

In the old ffmpeg --enable-libfaac was needed for good AAC encoder.

Isn't libvo-aacenc an internal ffmpeg/libav library ?

---

### Post by shekarkcb on 2011-10-20
Thanks for the reply.

I don't think other options are required. In the command which uses avconv , it used only those 2.

No, i have installed ffmpeg, but i couldn't find libvo-aacenc under ffmpeg/libav library.

Any pointer are greatly helpful.

Thanks.

---

### Post by ron999 on 2011-10-20
> **shekarkcb said:**
> I couldn't find package 'libvo-aacenc for unbunto 10.04. Can anybody point me where i am doing wrong?
Thanks

Hi
To install libvo-aacenc you need to compile it yourself.

This is the method I use:-

Install the dependencies:-
```
sudo apt-get install build-essential checkinstall
```

Then paste this single command:-

```
cd ~/ && \
wget http://sourceforge.net/projects/opencore-amr/files/vo-aacenc/vo-aacenc-0.1.1.tar.gz && \
tar -xf vo-aacenc-0.1.1.tar.gz && \
cd vo-aacenc-0.1.1 && \
./configure
```

If everything looks OK then:-
```
make
```

And then:-

```
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname vo-aacenc --pkgversion 0.1.1 \
--backup=no --default && sudo ldconfig

```

---

### Post by shekarkcb on 2011-10-20
Thanks for the reply.

I am able to install libav-0.7, but it seems installed 'ffmpeg', when i run avconv command i get this.
```

shekar@x264Encoder:~/Desktop/shekar/libav-0.7.2$ avconv
avconv version 0.7, Copyright (c) 2000-2011 the Libav developers
  built on Sep 13 2011 19:59:21 with gcc 4.4.3
  configuration: 
  libavutil    51. 10. 0 / 51. 10. 0
  libavcodec   53. 10. 0 / 53. 10. 0
  libavformat  53.  7. 0 / 53.  7. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  6. 0 /  2.  6. 0
  libswscale    2.  1. 0 /  2.  1. 0
Hyper fast Audio and Video encoder
usage: avconv [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man avconv'
shekar@x264Encoder:~/Desktop/shekar/libav-0.7.2$ find . -iname "avconv"
shekar@x264Encoder:~/Desktop/shekar/libav-0.7.2$ 

```and when i run the command for avconv (which i posted on the first post, it says this

```

avconv version 0.7, Copyright (c) 2000-2011 the Libav developers
  built on Sep 13 2011 19:59:21 with gcc 4.4.3
  configuration: 
  libavutil    51. 10. 0 / 51. 10. 0
  libavcodec   53. 10. 0 / 53. 10. 0
  libavformat  53.  7. 0 / 53.  7. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  6. 0 /  2.  6. 0
  libswscale    2.  1. 0 /  2.  1. 0
Input #0, mpeg, from '5min.mpg':
  Duration: 00:14:59.97, start: 1.000000, bitrate: 8253 kb/s
    Stream #0.0[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 224 kb/s
    Stream #0.1[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x576 [PAR 16:15 DAR 4:3], 11432 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
Unrecognized option 'preset'
Failed to set value 'veryslow' for option 'preset'
576TO480.sh: 17: 5min.mpg: not found
avconv version 0.7, Copyright (c) 2000-2011 the Libav developers
  built on Sep 13 2011 19:59:21 with gcc 4.4.3
  configuration: 
  libavutil    51. 10. 0 / 51. 10. 0
  libavcodec   53. 10. 0 / 53. 10. 0
  libavformat  53.  7. 0 / 53.  7. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  6. 0 /  2.  6. 0
  libswscale    2.  1. 0 /  2.  1. 0
pipe:: Operation not permitted
avconv version 0.7, Copyright (c) 2000-2011 the Libav developers
  built on Sep 13 2011 19:59:21 with gcc 4.4.3
  configuration: 
  libavutil    51. 10. 0 / 51. 10. 0
  libavcodec   53. 10. 0 / 53. 10. 0
  libavformat  53.  7. 0 / 53.  7. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  6. 0 /  2.  6. 0
  libswscale    2.  1. 0 /  2.  1. 0
Input #0, mpeg, from '5min.mpg':
  Duration: 00:14:59.97, start: 1.000000, bitrate: 8253 kb/s
    Stream #0.0[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 224 kb/s
    Stream #0.1[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x576 [PAR 16:15 DAR 4:3], 11432 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
Unknown encoder 'libvo_aacenc'
avconv version 0.7, Copyright (c) 2000-2011 the Libav developers
  built on Sep 13 2011 19:59:21 with gcc 4.4.3
  configuration: 
  libavutil    51. 10. 0 / 51. 10. 0
  libavcodec   53. 10. 0 / 53. 10. 0
  libavformat  53.  7. 0 / 53.  7. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  6. 0 /  2.  6. 0
  libswscale    2.  1. 0 /  2.  1. 0
video.h264: No such file or directory
shekar@x264Encoder:~/Subtitle Encoding scripts/test/test$ 

```where 576TO480.sh is the file name where i have put avconv commands. 

Any pointer are greatly helpful.

Thanks.

---

### Post by ron999 on 2011-10-20
> **shekarkcb said:**
> Thanks for the reply.

I am able to install libav-0.7, but it seems installed 'ffmpeg', when i run avconv command i get this.
[CODE]
shekar@x264Encoder:~/Desktop/shekar/libav-0.7.2$ avconv
avconv version 0.7, Copyright (c) 2000-2011 the Libav developers
  [COLOR="Red"]built on Sep 13 2011 19:59:21[/COLOR] with gcc 4.4.3
  configuration: 
  libavutil    51. 10. 0 / 51. 10. 0
  libavcodec   53. 10. 0 / 53. 10. 0
  libavformat  53.  7. 0 / 53.  7. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  6. 0 /  2.  6. 0
  libswscale    2.  1. 0 /  2.  1. 0
Hyper fast Audio and Video encoder
usage: avconv [options] [[infile options] -i infile]... {[outfile options] outfile}...

Any pointer are greatly helpful.

Thanks.

Built on _Sep 13 2011 19:59:21_?

---

### Post by shekarkcb on 2011-10-21
Thanks for the reply. Now i have re-built the avconv. Downloaded new libav-HEAD-0.7 from get libav site, and updated the script.
```

#!/bin/bash

#Now doing for PASS 1
avconv -i ./cheeni_5min.mpg  -pass 1 -vf 'movie=logo.png,setpts=PTS-STARTPTS [logo]; [in][logo] overlay=W-w-20:H-h-22 [out]' -vcodec libx264 -b 1300k -maxrate 1600k -bufsize 900k -threads 0 -refs 6 -f h264 -y /dev/null > 480p.ffmpeg.pass1.log;

sleep 10;
echo -e "\n\n\n===========================n PASS 1 DONE ==========================\n\n\n";
echo;
# Now doing for PASS 2

avconv -f yuv4mpegpipe -i - -pass 2 -vf 'movie=logo.png,setpts=PTS-STARTPTS [logo]; [in][logo] overlay=W-w-20:H-h-22 [out]' -vcodec libx264 -b 1300k -maxrate 1600k -bufsize 900k -threads 0 -refs 6 -y video.h264 &>480p.ffmpeg.pass2.log "$@"


```Below is the script o/p.

```

shekar@x264Encoder:~/Subtitle Encoding scripts/test/test$ time sh encode.sh 
avconv version 0.7, Copyright (c) 2000-2011 the Libav developers
  built on Oct 20 2011 20:04:53 with gcc 4.4.3
  configuration: --enable-libx264 --enable-libfaac --enable-gpl --enable-nonfree --enable-libvo-aacenc --enable-version3
  libavutil    51. 10. 0 / 51. 10. 0
  libavcodec   53. 10. 0 / 53. 10. 0
  libavformat  53.  7. 0 / 53.  7. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  6. 0 /  2.  6. 0
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  52.  0. 0 / 52.  0. 0
Input #0, mpeg, from './cheeni_5min.mpg':
  Duration: 00:14:59.97, start: 1.000000, bitrate: 8253 kb/s
    Stream #0.0[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 224 kb/s
    Stream #0.1[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x576 [PAR 16:15 DAR 4:3], 11432 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
[buffer @ 0x90bef00] w:720 h:576 pixfmt:yuv420p
[movie @ 0x90bd760] seek_point:0 format_name:(null) file_name:logo.png stream_index:0
[overlay @ 0x90c20e0] auto-inserting filter 'auto-inserted scaler 0' between the filter 'Parsed filter 1 setpts' and the filter 'Parsed filter 2 overlay'
[movie @ 0x90bd760] TB:0.040000
[scale @ 0x90c2dc0] w:68 h:16 fmt:bgra -> w:68 h:16 fmt:yuva420p flags:0x4
[overlay @ 0x90c20e0] main w:720 h:576 fmt:yuv420p overlay x:632 y:538 w:68 h:16 fmt:yuva420p
[overlay @ 0x90c20e0] main_tb:1/1000000 overlay_tb:1/25 -> tb:1/1000000 exact:1
[libx264 @ 0x90be960] using SAR=16/15
[libx264 @ 0x90be960] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x90be960] profile Main, level 3.0
Output #0, h264, to '/dev/null':
  Metadata:
    encoder         : Lavf53.7.0
    Stream #0.0: Video: libx264, yuv420p, 720x576 [PAR 16:15 DAR 4:3], q=-1--1, pass 1, 1300 kb/s, 90k tbn, 25 tbc
Stream mapping:
  Stream #0.1 -> #0.0 (mpeg2video -> libx264)
Press ctrl-c to stop encoding
frame=22500 fps=179 q=-1.0 Lsize=       0kB time=899.96 bitrate=   0.0kbits/s dup=12 drop=0    
video:141070kB audio:0kB global headers:0kB muxing overhead -100.000000%
frame I:254   Avg QP:13.57  size: 42310
[libx264 @ 0x90be960] frame P:7683  Avg QP:17.00  size: 11852
[libx264 @ 0x90be960] frame B:14563 Avg QP:19.18  size:  2929
[libx264 @ 0x90be960] consecutive B-frames:  5.7% 20.2% 11.5% 62.6%
[libx264 @ 0x90be960] mb I  I16..4: 27.8%  0.0% 72.2%
[libx264 @ 0x90be960] mb P  I16..4: 22.0%  0.0%  0.0%  P16..4: 71.4%  0.0%  0.0%  0.0%  0.0%    skip: 6.6%
[libx264 @ 0x90be960] mb B  I16..4:  3.6%  0.0%  0.0%  B16..8: 31.6%  0.0%  0.0%  direct:21.0%  skip:43.8%  L0:34.9% L1:46.2% BI:18.9%
[libx264 @ 0x90be960] coded y,uvDC,uvAC intra: 47.0% 71.0% 33.5% inter: 18.5% 31.0% 1.6%
[libx264 @ 0x90be960] i16 v,h,dc,p: 44% 23% 24%  9%
[libx264 @ 0x90be960] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 29% 21% 17%  3%  7%  6%  5%  6%  6%
[libx264 @ 0x90be960] i8c dc,h,v,p: 46% 19% 29%  5%
[libx264 @ 0x90be960] Weighted P-Frames: Y:2.1% UV:0.4%
[libx264 @ 0x90be960] kb/s:1284.05
-e 

===============================n PASS 1 DONE ==============================

real    2m16.083s
user    6m41.477s
sys    0m12.105s
shekar@x264Encoder:~/Subtitle Encoding scripts/test/test$ avconv version 0.7, Copyright (c) 2000-2011 the Libav developers
  built on Oct 20 2011 20:04:53 with gcc 4.4.3
  configuration: --enable-libx264 --enable-libfaac --enable-gpl --enable-nonfree --enable-libvo-aacenc --enable-version3
  libavutil    51. 10. 0 / 51. 10. 0
  libavcodec   53. 10. 0 / 53. 10. 0
  libavformat  53.  7. 0 / 53.  7. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  6. 0 /  2.  6. 0
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  52.  0. 0 / 52.  0. 0
pipe:: Operation not permitted


```Please share your thoughts... Any pointers are greatly helpful.

Thanks.

---

### Post by ron999 on 2011-10-21
> **shekarkcb said:**
> ... Any pointers are greatly helpful.


Well, you've compiled and installed avconv with libvo-aacenc OK.:)

Looks like there's a problem with the script.:(
See if somebody smart comes along now to help.:)

---

### Post by FakeOutdoorsman on 2011-10-21
As a side note in Ubuntu Oneiric 11.10 *libvo-aacenc* can be enabled in avconv/ffmpeg from the repository by installing *libavcodec-extra-53*. For more details see:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

> **shekarkcb said:**
> Please share your thoughts... Any pointers are greatly helpful
Make sure your avconv commands work first, and then once they work try the same commands in the script to rule out any issues introduced by the script itself.

Why is your second pass using a pipe as in input instead of *cheeni_5min.mpg* as your first pass does? Your script does not show where the piped input is coming from.

---

### Post by andrew.46 on 2011-10-21
Any thoughts on the sound quality of libvo-aacenc? I have used it and found it quite reasonable although on my setup neroAacEnc sounds better...

---

### Post by FakeOutdoorsman on 2011-10-21
I haven't tried libvo-aacenc much myself, but I did find a somewhat dated comparison [vo-aacenc&#12398;&#38899;&#36074;&#35413;&#20385;](http://d.hatena.ne.jp/kamedo2/20110430/1304181738) which rated: iTunes(qtaacenc) >= neroAacEnc > libfaac > vo-aacenc 0.1.0 > ffmpeg (the native FFmpeg aac encoder: -vcodec aac -strict experimental). I can't read Japanese however and I am not sure of the actual commands used.

---

### Post by andrew.46 on 2011-10-22
Well, my Japanese is pretty non-existent as well :). With apologies to the OP (I realise we are moving a long way from the question!) here is my own rather primitive script for converting *anything* to aac using neroAacEnc:

```

#!/bin/sh
# ----------------------------------------------- #
# Convert most audio files to aac using FFmpeg,   # 
# neroAacEnc and neroAacTag.                      #
# ----------------------------------------------- #      

# Select an input and output filename:

echo -n "Chose an input filename: "
read -e INPUT

echo -n "Chose an output filename: "
read -e OUTPUT

# Create some metatag variables from the input file:

TITLE=$(ffprobe $INPUT 2>&1 | grep -i 'TITLE' | sed 's/.\{24\}//')
ARTIST=$(ffprobe $INPUT 2>&1 | grep -i 'ARTIST' | sed 's/.\{24\}//')
ALBUM=$(ffprobe $INPUT 2>&1 | grep -i 'ALBUM' | sed 's/.\{24\}//')

# Convert the file to aac:

ffmpeg -i $INPUT -f wav - | \
          neroAacEnc -ignorelength -q 0.5 -if - -of $OUTPUT

# Add in the tags:

neroAacTag $OUTPUT \
           -meta:title="$TITLE" \
           -meta:artist="$ARTIST" \
           -meta:album="$ALBUM"

# Enjoy the music!!

```

Missing any sanity checks and only deals with the metatags that I use myself but can easily be adapted to anybody's needs. Sorry again to the OP for diverting the thread :(.

---

### Post by shekarkcb on 2011-11-04
Thanks all for the reply.

I have just copied script from some source... not sure from where i did that.

But i need to get this working. Any suggestions/pointers are greatly helpful

--
Shekar

---

### Post by U2XS on 2012-12-14
> **ron999 said:**
> Hi
To install libvo-aacenc you need to compile it yourself.

This is the method I use:-

Install the dependencies:-
```
sudo apt-get install build-essential checkinstall
```

Then paste this single command:-

```
cd ~/ && \
wget http://sourceforge.net/projects/opencore-amr/files/vo-aacenc/vo-aacenc-0.1.1.tar.gz && \
tar -xf vo-aacenc-0.1.1.tar.gz && \
cd vo-aacenc-0.1.1 && \
./configure
```

If everything looks OK then:-
```
make
```

And then:-

```
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname vo-aacenc --pkgversion 0.1.1 \
--backup=no --default && sudo ldconfig

```

Thanks!  I read & refer to this often so I figured I'd bump the thread.  I'm glad you posted this info.

---

