---
title: "kino does not import in 7.10"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by mhills on 2007-11-11
Kino worked fine with 7.04 but will not import videos (.wmv or .avi) in 7.10. IKino states it is importing, and it may take a long while, but it never stops.

---

### Post by Unterseeboot_234 on 2007-11-11
That feature IS working on my Gutsy. You have a codec problem. With the Linux version of Kino you have libraries. And, for me, the library names are criptic about which libs do what codecs. One lib will take care of several codecs. Make sure you have the libs listed in the following link:

**[video libraries]("http://www.kinodv.org/article/view/155/1/13/")**

One observation -- libquicktime. With the Gutsy release the Debian/Ubuntu build of libquicktime is libquicktime1 and that library has problems. It is impossible to make libquicktime from source files with Ubuntu which is a shame. Cinerella only has one useful export for me and that is quicktime movies, but, because we have libquicktime1, Cinerella is incapable. libquicktime would also be the necessary file you need to export quality video clips to use in Cinerella. Maybe Debian will fix the library one day.

---

### Post by mhills on 2007-11-11
Thanks for responding.

I loaded all the libraries in the link, but Kino still fails to import. 

One consequence of loading the libraries was that I was able to compile and install kino-1.1.1, which previously refused to configure, but the latest kino still fails to import.

---

### Post by Unterseeboot_234 on 2007-11-11
I just ran a test on my Kino, and my Kino is the default install from AFTER I got Gutsy. I can drag clips icon of .avi and .dv (the raw DV, or the captures) into the edit monitor of Kino. I cannot drag theo, nor quicktime, nor a couple of other formats. My .avi and my .dv are Linux born. I am not trying to drag into the Kino anything that another computer did. Also, if it makes any difference, I'm using a 64-bit Ubuntu. That shouldn't matter except for sound/audio issues.

Well, I know that I could play a "store-bought" DVD in Dapper and in Fiesty after I loaded codecs from Automatix2. In Gutsy I had to change from the default Gutsy's Movie Player to the (I think) Xine, that is, there are two versions of Movie Player using two libs and we have to pick one or the other.

I have installed Kino, Cinelerra, Avidmux, KdenLive. All of those added dependencies, however Kino was installed first and working before I wanted the extra features that possibly the other software would let me have. My recent experience is only Kino and KdenLive are going to do anything for me.

I wished I had a direct, expert answer for you. I've been mumbling in this post what all I fooled around with and it worked for me. The last suggestion I can think of, is a beta opensource called **getlibs** after you sudo apt-get install getlibs, then locate the binary of Kino, note the location -- probably /usr/bin/kino -- and then you type getlibs /user/bin/kino. If there are any dependecies missing for Kino, it will tell you and offer to go fetch.

I want to emphasize any and all of these video programs are front ends for the libs such as ffmpeg and thus my gut feeling why your Kino doesn't work. I crave the preservation of quality that Cinelerra will offer, but I can not have that program working in Gutsy because of libquicktime1.

---

### Post by mhills on 2007-11-11
Thanks for all your efforts. I tried getlibs (a nice application) but was told that kino had no unfulfilled dependencies. So I am at a bit of a loss. Would posting the output from my attempts to import files help?

---

### Post by Unterseeboot_234 on 2007-11-11
Sure, any output says something. I'm changing hardware locations, where this keyboard I'm typing is, we will be going to backup. I'll take a couple more look-sees at this with you on my Monday. Peace.

---

### Post by mhills on 2007-11-11
Sorry there is so much - I have no idea what is important and what is not.

>> Starting Editor
>> Creating undo/redo buffer
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --disable-ffserver --disable-ffplay --disable-v4l --disable-v4l2 --disable-dv1394 --disable-network --disable-zlib --disable-vhook --build-suffix=-kino --enable-gpl --enable-swscaler --prefix=/usr/local
  libavutil version: 49.3.0
  libavcodec version: 51.38.0
  libavformat version: 51.10.0
  built on Nov 11 2007 15:33:16, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
MEncoder 1.0rc1-4.0.3 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 9)
MEncoder 1.0rc1-4.0.3 (C) 2000-2006 MPlayer Team
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2



success: format: 0  data: 0x0 - 0xe1000
success: format: 0  data: 0x0 - 0xe1000
AVI file format detected.
AVI file format detected.
AVI_NI: No audio stream found -> no sound.
VIDEO:  [WMV3]  352x288  24bpp  25.000 fps  1346.4 kbps (164.4 kbyte/s)
[V] filefmt:3  fourcc:0x33564D57  size:352x288  fps:25.00  ftime:=0.0400
VIDEO:  [WMV3]  352x288  24bpp  25.000 fps  1346.4 kbps (164.4 kbyte/s)
[V] filefmt:3  fourcc:0x33564D57  size:352x288  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 11025 Hz, 2 ch, s16le, 24.0 kbit/6.80% (ratio: 3000->44100)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Ignoring video stream!
videocodec: framecopy (352x288 24bpp fourcc=33564d57)
Input #0, s16le, from '/home/mhills/temp/test.avi.pcm':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Input #1, rawvideo, from '/home/mhills/temp/test.avi.i420':
  Duration: N/A, bitrate: N/A
  Stream #1.0: Video: rawvideo, yuv420p, 640x480, 29.97 fps(r)
Output #0, dv, to '/home/mhills/temp/test.avi.dv':
  Stream #0.0: Video: dvvideo, yuv411p, 720x480, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [format fmt=I420]
Opening video filter: [expand w=640 h=480]
Expand: 640 x 480, -1 ; -1, osd: 0, aspect: 0.000000, round: 1
Opening video filter: [scale]
Opening video filter: [dsize=640:480:0]
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:304128  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 352 x 288 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
Press [q] to stop encoding
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4
SwScaler: reducing / aligning filtersize 5 -> 4

SwScaler: BICUBIC scaler, from yuv420p to yuv420p using MMX2
SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
SwScaler: using n-tap MMX scaler for vertical scaling (YV12 like)
SwScaler: 352x288 -> 588x480
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
>>> Received playlist to store at position 0min   0mb  A-V:0.000 [0:0]
>>>> Adding to end
>> Leaving Editor
>> Left Editor
>> Starting Editor
>> Kino Common newFile
>>> Received playlist to store at position 0
>>>> Adding to end
Exiting Kino

---

### Post by Unterseeboot_234 on 2007-11-12
OK, starting Kino from a command line (instead of the menu) I get a different stream of information. When I drag a "clip001006.dv" into the editor window of Kino, I then get:

```
>>> Received playlist to store at position 1
>>>> Adding to end
>> Trying XVideo at 720x480
>>> XvQueryAdaptors count: 2
>>> Xv: NV17 Video Texture: ports 355 - 386
>>> formats supported: 4
>>>     0x32595559 (YUY2) packed
>>>     0x32315659 (YV12) planar
>>>     0x59565955 (UYVY) packed
>>>     0x30323449 (I420) planar
>>> 0: XV_IMAGE, 2046x2046 rate = 1/1
```

that is, the run-through of available libs matched the one for XVideo and decided on the canvas size to work with.

My version of Kino is 1.10. I installed it straight from Synaptic. If I want to capture with this Kino I must do so as root ... but that's another problem, another discussion. I usually capture with the buttons on my camera or use the command-line dvgrab. The ONE THING I am missing is the ability to export a Kino edit to a Quicktime movie. Fiesty can do that, Gutsy cannot. the connecting libs you see in the link we discussed above are a discussion about Edgy-build.

If you built your Kino, that can twist the Symbolic links to the libs unless you know where to put the various parts of built software. I mention this, you might try **sudo kino** from the command line. If that works, it means something.

The only other lib I have that you might not have is one called ImageMagick, which is a useful lib to manipulate a whole folder of art graphics and/or photos.

The other thing we can try is install Kdenlive -- a video software. If that works to import video clips, then we know we should uninstall your current Kino, and go back to Synaptic's version for a clean install.

If none of this works, we need to move this disussion onto a Kino mail list. The Kino How-to has that list of libs??? it also has a mailto link to the person that wrote that list.

Good luck. I will be watching this thread. If we are successful, we need to advertise that fact so the folks that follow us can do video editing. Preservere, I find video with Linux is much more heavy-duty than M$ answers (never tried OSX). With Kino on 64-bit I capture in real time with NO dropped frames or clipped audio.

[edit] One final thought. If you like, I could post to on an online storage site a very short video clip of mine. If my video imports into your Kino, then that tells us something.

---

### Post by mhills on 2007-11-12
Thanks for this. I have returned to a straight synaptic installation of kino 1.1.0 but still no improvement.

Can I take you up on the offer to place a short video online which I could download?

---

### Post by Unterseeboot_234 on 2007-11-12
No problem, Herr mHill. Uploaded a tested-in-Kino "shortSample.dv" -- 3.9 seconds at 13.5 meg. Follow the link below:

**[videoClip]("http://www.divshare.com/download/2726490-204")**

Let me know if THIS works and we'll take it from there. I want everyone that uses *buntu that wants video to be capable and that way the entire community keeps getting better.

---

### Post by mhills on 2007-11-12
Yes, it worked perfectly, thanks.

So the problem seems to lie with importing .avi or .wmv files.

---

### Post by Unterseeboot_234 on 2007-11-12
Well, if we look inside Kino --> Export tab, there is an option to export OpenDL avi. I have NO idea which zoo animal that flavor of avi is. I do recall having compatibillity issues, now that we discuss this, with Adobe Premiere .avi and Kino. Which brings up the point, whatever vid project I get started, I will slam short clips of various formats between the software(s) I will be using. For a moment, it looks like Quicktime .mov would fix many, many things but as I have mentioned too many times, in Gutsy we don't have the correct libquicktime. To make the correct libquicktime will take Fedora or some other distro to build that library with all the handles for Cinelerra-to-Kino to Kdenlive.

I'm impressed with Kdenlive as of late. Kdenlive is really a GUI for ffmpeg. If we study up real hard on ffmpeg, there are command-lines that will translate one format into another format, but the commands are very long and very involved. I'm in the middle of animation. Kdenlive is the ONLY answer I've found to make a folder full of images into a film clip. Kdenlive does list .avi but I don't know if that is the MS idea of .avi. Indeed, .avi is plagued with too many compression codecs to choose from and yet the resulting film clips are all called .avi.

Good luck. Post again. I'll watch this thread.

---

### Post by mhills on 2007-11-12
Its not perfect, but I did find I could convert my .wmv file to .dv with

ffmpeg -i test.wmv -target pal-dv test.dv

and then it goes into kino without trouble.

I guess this will have to do for now - many thanks for your help, I would never have got this far without it.

---

### Post by khartojo on 2008-01-01
Had the same problem importing AVI until I installed ffmpeg pkg through Synaptic. Just the gstreamer0.10-ffmpeg pkg was not enough.

> **mhills said:**
> Yes, it worked perfectly, thanks.

So the problem seems to lie with importing .avi or .wmv files.

---

### Post by faintscrawl on 2008-02-05
I'm also having trouble importing the 'raw' clips from my video camera, a hitachi with a hdd.

I've installed kino (and open movie editor after kino didn't work). But I can't get the video from the camera hard drive onto the computer. In Windows, as soon as I plugged the cord in the usb and turned on the camera, i would be asked if I wanted to import video. That doesn't happen in ubuntu. I can see the files (see screen shot). Also if I use vlc media player I can watch a vro file (found in dvd_rtav) , but it is one long clip, not broken into separate shots. Anyway kino and movie editor won't accept the vro file. If anyone has mastered this obstacle and can offer some insight I'd appreciate it.

---

### Post by faintscrawl on 2008-02-05
Just been reading up on .vro files.  They work with a .inf file that contains the information about time and where the separate shots are located.  Clearly to edit, the program (kino, let's say) will need both files to know how to break up the vro file into all the original clips.  A huge vro file by itself will be VERY unwieldy to work with.

---

