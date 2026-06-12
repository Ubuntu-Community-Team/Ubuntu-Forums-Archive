---
title: "does ubuntu has screenshot creator ?"
date: 2009-09-16
forum: Multimedia Software
---

### Post by dumblebee100 on 2009-09-16
Hey folks I have been using ubuntu for a long time and I could not find some decent program for creating screenshots of the videos

I have to create them because I have to post them in forums 

my requirement is something like this 
if I point out to a movie I want to get the screenshot of the movie just like in the image 

[http://i39.tinypic.com/678t3q.jpg](http://i39.tinypic.com/678t3q.jpg)

please respond as fast as possible ..I need it urgently

for more information just look at this site
[http://www.movieshare.org/non-windows/mac-screen-grabber-v2-0-2-movie-screenshot-maker/301912/]("http://www.movieshare.org/non-windows/mac-screen-grabber-v2-0-2-movie-screenshot-maker/301912/")

---

### Post by Whiffle on 2009-09-16
gxine does, as I'm sure others do.  File > Snapshot

---

### Post by jeannacav on 2009-09-16
It has 2 kinds, afaik.
You would pause your movie, then use the button that says prtsc which on this keyboard is just to the right of f12.
If you hold down 'alt' and press that button you get a screenshot of whatever window the cursor happens to be in at the moment, so 'alt'+'prtsc'. 
I am pretty sure it does NOT take a pic of the cursor, so do not plan on using it as a pointer.

jeanna

(I want a marqueed screenshot, and cannot seem to find it.)

---

### Post by dumblebee100 on 2009-09-16
videocut seems to do the work but its not working for me 

its saying floating point error for avi files and for some wmv files it got screenshots but all are having greenlines and I cannot see anything particular from those screens ..

is there any other program for taking screenshots of a movie in a consolidated way

---

### Post by ajgreeny on 2009-09-16
In totem use the Edit - Take screenshot.

The printscreen key will just give you a black space for videos, I'm afraid.  Most of the video player software applications have a similar utility, but I think you will need to paste them together to get the multiple picture like you showed.

---

### Post by freackout on 2009-09-16
> **dumblebee100 said:**
> Hey folks I have been using ubuntu for a long time and I could not find some decent program for creating screenshots of the videos

I have to create them because I have to post them in forums 

my requirement is something like this 
if I point out to a movie I want to get the screenshot of the movie just like in the image 

[http://i39.tinypic.com/678t3q.jpg](http://i39.tinypic.com/678t3q.jpg)

please respond as fast as possible ..I need it urgently


for more information just look at this site
[http://www.movieshare.org/non-windows/mac-screen-grabber-v2-0-2-movie-screenshot-maker/301912/]("http://www.movieshare.org/non-windows/mac-screen-grabber-v2-0-2-movie-screenshot-maker/301912/")

try istanbul or xvidcap though there are plenty of others it is in synaptics ubuntu distro's ok

---

### Post by ubongo2008 on 2009-09-16
i just press "print"-key

---

### Post by freackout on 2009-09-16
> **dumblebee100 said:**
> Hey folks I have been using ubuntu for a long time and I could not find some decent program for creating screenshots of the videos

I have to create them because I have to post them in forums 

my requirement is something like this 
if I point out to a movie I want to get the screenshot of the movie just like in the image 

[http://i39.tinypic.com/678t3q.jpg](http://i39.tinypic.com/678t3q.jpg)

please respond as fast as possible ..I need it urgently

for more information just look at this site
[http://www.movieshare.org/non-windows/mac-screen-grabber-v2-0-2-movie-screenshot-maker/301912/]("http://www.movieshare.org/non-windows/mac-screen-grabber-v2-0-2-movie-screenshot-maker/301912/")

xscreensaver

---

### Post by dumblebee100 on 2009-09-17
None of these solutions will work for me 


at last videocut is the only software which is perfect for my requirement and now its not crashing so I will use it 

so I mark this thread as solved

---

### Post by kostkon on 2009-09-17
Then you need to check [*GFrameCatcher*]("http://developer.berlios.de/projects/gframecatcher/"). You can download a deb from its site or from *[getdeb.net]("http://www.getdeb.net/app/GFrameCatcher")*.

---

### Post by JuanC on 2009-09-19
I also like [GFrameCatcher]("http://gnomefiles.org/app.php/GFrameCatcher"), it looks integrated in my GNOME desktop and works perfectly for my video files.

This package is not include in *Add/Remove Applications* or *Synaptic*, so you have to download from [getdeb.net]("http://www.getdeb.net")

I made a bug report about this, to include GFrameCatcher in Ubuntu repositories, you can click in *This bug affects me too*, if you want this package would be include in Ubuntu repositories: 
[https://bugs.launchpad.net/ubuntu/+bug/400212](https://bugs.launchpad.net/ubuntu/+bug/400212)

---

### Post by andrew.46 on 2009-09-19
Hi dumblebee,

> **dumblebee100 said:**
> Hey folks I have been using ubuntu for a long time and I could not find some decent program for creating screenshots of the videos

If you are happy to use the commandline MPlayer has what you need. Simply run MPlayer thus:

```
mplayer -vf screenshot ***[COLOR="Red"]mymovie.avi[/COLOR]***
```

and each time you press the 's' key a screenshot in png format will be taken and deposited in your working directory. A working example below:

```

andrew@skamandros~/samples$ **[COLOR="Red"]mplayer -vf screenshot Rammstein_Mutter.mp4[/COLOR]** 
MPlayer SVN-r29687-4.3.3 (C) 2000-2009 MPlayer Team

Playing Rammstein_Mutter.mp4.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
[lavf] Video stream found, -vid 1
VIDEO:  [H264]  352x264  24bpp  24.991 fps    0.0 kbps ( 0.0 kbyte/s)
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 352 x 264 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x8a54300]No accelerated colorspace conversion found.
[swscaler @ 0x8a54300]using unscaled yuv420p -> rgb24 special converter
VO: [xv] 352x264 => 352x264 Planar YV12 
sending VFCTRL_SCREENSHOT!000 ct:  0.023   0/  0  6%  1%  1.3% 1 0 
**[COLOR="Red"]*** screenshot 'shot0001.png' ***[/COLOR]**
sending VFCTRL_SCREENSHOT!001 ct:  0.023   0/  0  5%  1%  1.3% 1 0 
**[COLOR="Red"]*** screenshot 'shot0002.png' ***[/COLOR]**
sending VFCTRL_SCREENSHOT!000 ct:  0.023   0/  0  5%  1%  1.3% 1 0 
**[COLOR="Red"]*** screenshot 'shot0003.png' ***[/COLOR]**
sending VFCTRL_SCREENSHOT!001 ct:  0.024   0/  0  5%  1%  1.3% 1 0 
**[COLOR="Red"]*** screenshot 'shot0004.png' ***[/COLOR]**
A:  15.0 V:  15.0 A-V:  0.002 ct:  0.024   0/  0  5%  1%  1.3% 1 0 
Exiting... (Quit)

```

and I attach the handful of screenshots this command took, pretty easy to do and the results are fine...

Andrew

---

### Post by pricinosus on 2009-10-01
GFrameCatcher is not preserving aspect ratio of the movie !!!!
If a movie is 16:9 GFrameCatcher display 4:3 thumbnails.
The correct way is adding black bars to 16:9 image.

So ... thumb down for GFrameCatcher


@andrew.46 
dumblebee100 want one matrix/table file with snaps not a folder with separte file.... or is there a way with mplayer to generate automatically such a file ?

---

### Post by monraaf on 2009-10-04
The new Totem in Karmic has exactly that feature. Here's one I made with it, it's very easy and fast.

[IMG]http://img15.imageshack.us/img15/2714/lebowski.jpg[/IMG]

---

### Post by dumblebee100 on 2009-10-06
Thanks for the replies ..

the Totem is perfect match for my problem ..

it does exactly what I want .

and it comes out of the box .no need to install other softwares

---

### Post by COKEDUDE on 2011-02-02
I have searched various sites and found these 4 programs for creating thumbnails. 

totem, gframecatcher, videocut, smplayer

gframecatcher- Untested
[http://developer.berlios.de/projects/gframecatcher/](http://developer.berlios.de/projects/gframecatcher/)

videocut- This has problems mp4's and mov's. The only type of video I have been able to make thumnails of is avi's and wmv's. 
File, open file, export

totem- I have had no problems with any type of video I have tried. I tried avi, wmv, mp4, and mov. 
Edit, Create screenshot gallery, save

smplayer- smplayer has the most features so if you like features I recommend using smplayer. I have had no problems with any type of video I have tried. I tried avi, wmv, mp4, and mov. 
Video, Preview, ok, save

---

