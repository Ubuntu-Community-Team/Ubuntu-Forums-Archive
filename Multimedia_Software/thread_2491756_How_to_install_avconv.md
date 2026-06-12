---
title: "How to install avconv"
date: 2023-10-19
forum: Multimedia Software
---

### Post by satimis on 2023-10-19
Hi all,

**[COLOR="#FF0000"]Ubuntu 22.04 desktop[/COLOR]**

How to install avconv

I need using it to convert .mp4 to mpeg-2 file

ffmpeg is already running but I couldn't find libav-tools on repo

$ apt policy libav-tools```

libav-tools:
  Installed: (none)
  Candidate: (none)
  Version table:

```

Please help.  Thanks in advance.

OR

Any other package can do the job?  Thanks

Regards

---

### Post by #&amp;thj^% on 2023-10-19
For me it is:
```
sudo ln -s /usr/bin/ffmpeg /usr/bin/avconv

```
Now check with:
```
avconv
ffmpeg version n6.0 Copyright (c) 2000-2023 the FFmpeg developers
  built with gcc 13.2.1 (GCC) 20230801
  configuration: --prefix=/usr --disable-debug --disable-static --disable-stripping --enable-amf --enable-avisynth --enable-cuda-llvm --enable-lto --enable-fontconfig --enable-gmp --enable-gnutls --enable-gpl --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libdav1d --enable-libdrm --enable-libfreetype --enable-libfribidi --enable-libgsm --enable-libiec61883 --enable-libjack --enable-libjxl --enable-libmodplug --enable-libmp3lame --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librav1e --enable-librsvg --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libsvtav1 --enable-libtheora --enable-libv4l2 --enable-libvidstab --enable-libvmaf --enable-libvorbis --enable-libvpl --enable-libvpx --enable-libwebp --enable-libx264 --enable-libx265 --enable-libxcb --enable-libxml2 --enable-libxvid --enable-libzimg --enable-nvdec --enable-nvenc --enable-opencl --enable-opengl --enable-shared --enable-version3 --enable-vulkan
  libavutil      58.  2.100 / 58.  2.100
  libavcodec     60.  3.100 / 60.  3.100
  libavformat    60.  3.100 / 60.  3.100
  libavdevice    60.  1.100 / 60.  1.100
  libavfilter     9.  3.100 /  9.  3.100
  libswscale      7.  1.100 /  7.  1.100
  libswresample   4. 10.100 /  4. 10.100
  libpostproc    57.  1.100 / 57.  1.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'

```
Do check the man page.

---

### Post by satimis on 2023-10-19
> **1fallen said:**
> For me it is:
```
sudo ln -s /usr/bin/ffmpeg /usr/bin/avconv

```
Now check with:
```
avconv
ffmpeg version n6.0 Copyright (c) 2000-2023 the FFmpeg developers
  built with gcc 13.2.1 (GCC) 20230801
  configuration: --prefix=/usr --disable-debug --disable-static --disable-stripping --enable-amf --enable-avisynth --enable-cuda-llvm --enable-lto --enable-fontconfig --enable-gmp --enable-gnutls --enable-gpl --enable-ladspa --enable-libaom --enable-libass --enable-libbluray --enable-libbs2b --enable-libdav1d --enable-libdrm --enable-libfreetype --enable-libfribidi --enable-libgsm --enable-libiec61883 --enable-libjack --enable-libjxl --enable-libmodplug --enable-libmp3lame --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librav1e --enable-librsvg --enable-libsoxr --enable-libspeex --enable-libsrt --enable-libssh --enable-libsvtav1 --enable-libtheora --enable-libv4l2 --enable-libvidstab --enable-libvmaf --enable-libvorbis --enable-libvpl --enable-libvpx --enable-libwebp --enable-libx264 --enable-libx265 --enable-libxcb --enable-libxml2 --enable-libxvid --enable-libzimg --enable-nvdec --enable-nvenc --enable-opencl --enable-opengl --enable-shared --enable-version3 --enable-vulkan
  libavutil      58.  2.100 / 58.  2.100
  libavcodec     60.  3.100 / 60.  3.100
  libavformat    60.  3.100 / 60.  3.100
  libavdevice    60.  1.100 / 60.  1.100
  libavfilter     9.  3.100 /  9.  3.100
  libswscale      7.  1.100 /  7.  1.100
  libswresample   4. 10.100 /  4. 10.100
  libpostproc    57.  1.100 / 57.  1.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'

```
Do check the man page.
Hi,

Thanks for your advice.

It is a symbolic link, still ffmpeg command

---

### Post by TheFu on 2023-10-19
Why not just use ffmpeg?

$ more 2mpg-HQ.sh 
```
#!/bin/bash

for filename in "$@"; do
   NEW=${filename/%???/mpg}
   nice ffmpeg -i $filename -c:v mpeg2video -qscale:v 1   $NEW
done
```
This will create a high quality mpeg2 file - it will be big.  If you intend to put it onto a DVD, some other options are needed to ensure a compatible video file for DVD is created.

---

### Post by satimis on 2023-10-19
> **TheFu said:**
> Why not just use ffmpeg?

$ more 2mpg-HQ.sh 
```
#!/bin/bash

for filename in "$@"; do
   NEW=${filename/%???/mpg}
   nice ffmpeg -i $filename -c:v mpeg2video -qscale:v 1   $NEW
done
```
This will create a high quality mpeg2 file - it will be big.  If you intend to put it onto a DVD, some other options are needed to ensure a compatible video file for DVD is created.
I'm trying to convert .mp4 to mpeg-2 file.

According to following link

How to convert a video from mp4/flv to mpeg/mpg
[https://askubuntu.com/questions/265176/how-to-convert-a-video-from-mp4-flv-to-mpeg-mpg](https://askubuntu.com/questions/265176/how-to-convert-a-video-from-mp4-flv-to-mpeg-mpg)

$ avconv -i video.mp4 -c:v mpeg2video video.mpg

It need to run avconv

Regards

---

### Post by TheFu on 2023-10-20
My script works to convert from **any** video file type supported by ffmpeg to mpeg2.  That's basically any file type that isn't using the very, very, very latest video codecs like h.266 or AV3.

BTW, mp4 is a container, not a video codec.

But you seem to like doing things different from me, which is fine. I provided a working method.

---

### Post by Yellow Pasque on 2023-10-20
avconv is obsolete and the libav-tools package is not found in any modern/supported version of Ubuntu. Use ffmpeg.
(You should look at the date on guides you try to follow. The page you linked to is 10 years old..)

---

### Post by satimis on 2023-10-21
> **TheFu said:**
> My script works to convert from **any** video file type supported by ffmpeg to mpeg2.  That's basically any file type that isn't using the very, very, very latest video codecs like h.266 or AV3.

BTW, mp4 is a container, not a video codec.

But you seem to like doing things different from me, which is fine. I provided a working method.
Hi,

Please advise.
1) Steps to create your script file ?
2) Where to store your script file ?
3) How to run your script file ?

Thanks

Regard

---

### Post by satimis on 2023-10-21
> **Yellow Pasque said:**
> avconv is obsolete and the libav-tools package is not found in any modern/supported version of Ubuntu. Use ffmpeg.
(You should look at the date on guides you try to follow. The page you linked to is 10 years old..)
Hi,

Thanks for your advice.

Regards

---

### Post by TheFu on 2023-10-21
> **satimis said:**
> Hi,

Please advise.
1) Steps to create your script file ?
2) Where to store your script file ?
3) How to run your script file ?

Thanks

Regard

Seriously?  You've been here long enough to know these things. It isn't like you don't ask and get help with scripts ever month or so.  Nothing special. Standard script.
Google found this: [https://www.cyberciti.biz/faq/howto-run-a-script-in-linux/](https://www.cyberciti.biz/faq/howto-run-a-script-in-linux/)

---

### Post by satimis on 2023-10-22
Hi all,

I have old video captured on Sony V8 tapes, years ago, with Sony Camcorder, CCD-F380E.  I suppose this camcorder is the 1st Generation model of Sony Camcorders.  Later I, myself, ripped them on VHS tapes, playing the tapes on VHS player connected to Cathode-ray tube TV.  The video were quite clear.

Unfortunately my VHS player and Sony camcorder were broken down, leaving me no device playing the tapes.  One year ago I sent a VHS tape to a professional shop here, ripping it on DVD. Unfortunately some video are not clear, unsharp.

I have download the video to desktop computer as .VOC format, converting them to .mov/mp4 etc.  2 weeks before I ran following ffmpeg commands to restore/sharpen them;
```

ffmpeg -i inpute.mov -vf unsharp=3:3:1.5 output.mov 
ffmpeg -i inpute.mov -vf unsharp=5:5:2 output.mov  
ffmpeg -i inpute.mov -vf unsharp=3:3:5 output.mov
ffmpeg -i inpute.mov -vf unsharp=13:13:2.5 output.mov
ffmpeg -i inpute.mov -vf unsharp=13:13:5 output.mov

```

Not much better result obtained.  (I also tried their .mp4 files)

Just tried TheFu version, still not much result obtained.```

a 34.6MB .mov file increased to 46.1MB mpg file
a 582.3MB .mp4 file increased to 1.5GB mpg file

```
3 days before I sent a V8 tape to another professional shop here, ripping the video on USB stick as .mp4. I'm still waiting for its delivery.

If this professional shop can provide a better result, ripping the V8 tapes, I won't shop a second-hand Sony V8 and Hi8 camcorder to do the job myself.

I have succeeded retoring old yellowish photos, running GIMP and AI Photo editor, but fail to restore the video on my old V8 tapes.

**[COLOR="#FF0000"]EDIT[/COLOR]**
The second professional shop can also rip V8 tape to USB stick as mpeg-2.  Which of them is better .mp4 or mpeg-2 ?

---

### Post by #&amp;thj^% on 2023-10-22
> **satimis said:**
>  Which of them is better .mp4 or mpeg-2 ?
This is not a cut and dried answer, TheFu has tried to explain that, and the general terminology is badly worded by most of us.

Ubuntu switched during the transitional period when libav supplied both their version of ffmpeg and their renamed tool avconv. When users attempted to use libav's ffmpeg they got the following message:
> 
This program is not developed anymore and is only provided for compatibility.  
Use avconv instead (see Changelog for the list of incompatible changes).


The Moving Pictures Experts Group is the developer who created MPEG. to be more exact, they use MPEG-1 or MPEG-2 as a method to compress video files, resulting in MPEG or .mpg and .mpeg. There are different kinds of MPEG files, namely MPEG-1, MPEG-2, MPEG-4, MPEG-7, MPEG-2, and many more depending on the usage.

 MPEG is renowned for its high quality. The quality also makes it a better choice when it comes to backing up videos, especially if the user wants to maintain the original video's quality.

The video's flexibility, MP4 can be played on almost all devices, including mobile devices. This perk of MP4 makes it one of many people's favorites now.(That doesn't make it yours though)

For me The FFmpeg community is larger than libav, and the most dedicated developer (michael niedermayer) stuck with FFmpeg (From VLC)

---

### Post by Yellow Pasque on 2023-10-23
> **1fallen said:**
> The FFmpeg community is larger than LibAV

It's not hard to be > 0. The last commit to the LibAV repo was almost 5 years ago. Their website is gone. Their devs either went back to FFmpeg or moved on to something else. "It's dead, Jim."

EDIT: I also hated that message about ffmpeg not being developed further. That was just a lie. It's funny how it ended up the other way around.

---

