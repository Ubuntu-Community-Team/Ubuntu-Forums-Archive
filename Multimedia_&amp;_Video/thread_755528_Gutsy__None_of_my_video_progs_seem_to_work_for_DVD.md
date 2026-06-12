---
title: "Gutsy:  None of my video progs seem to work for DVD"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by rmaguir on 2008-04-14
I'm a newby...please be gentle.  

I've been using Ubuntu for a couple of months now, but today was the first time I tried to watch a DVD.  I tried using Mplayer, Totem, Miro, and god knows what to watch this DVD.  I read all of the forums could find, and downloaded various programs and libraries and whatnot.  

All to no avail.  

What happens when I put in a DVD is (well, first, nothing) that no matter what program I use to play it, I hear the first millisecond of sound, then the program closes.  Why is this?

I'm using a Dell 1420....

---

### Post by greenstar on 2008-04-14
You might try this to be sure you have all the necessary libraries installed:
```
sudo aptitude install libdvdcss2 libdvdread3
```

HTH,

Greenstar

---

### Post by rmaguir on 2008-04-14
> **greenstar said:**
> You might try this to be sure you have all the necessary libraries installed:
```
sudo aptitude install libdvdcss2 libdvdread3
```

HTH,

Greenstar

No go.  

Do I need to restart?  If not, that didn't do it.

---

### Post by greenstar on 2008-04-15
OK, then try running the player from a terminal. Whatever happens, the player's verbose output will be displayed in the terminal. The video player will open in a separate window. You'll see...

This is what I did to play a file called "Elastic Bands.wmv" that is in the /Videos directory in my /home.
```
mplayer ~/Videos/Elastic\ Band.wmv
```

Try a similar command pointing to one of your video files and post the terminal output.

Greenstar

---

### Post by rmaguir on 2008-04-15
> **greenstar said:**
> OK, then try running the player from a terminal. Whatever happens, the player's verbose output will be displayed in the terminal. The video player will open in a separate window. You'll see...

This is what I did to play a file called "Elastic Bands.wmv" that is in the /Videos directory in my /home.
```
mplayer ~/Videos/Elastic\ Band.wmv
```

Try a similar command pointing to one of your video files and post the terminal output.

Greenstar

When I do that, I get a scrolling X11 error like this:

> X11 error: BadAlloc (insufficient resources for operation) 0.9% 0 0 

The numbers at the end change.  Right now, it's "5 0"

Oddly enough, this time, even though there was no video whatsoever, I could hear the sound, until I closed the terminal.

---

### Post by rmaguir on 2008-04-15
I just say another thread that would leavem me to believe that it's my graphics card.  Just in case it is, I've looked up my card, and I think it's an Intel X3100

---

### Post by warp99 on 2008-04-15
Open a terminal, put the DVD in the tray and issue the following:
```
mplayer -vo x11 dvd://
```

What is the output?

---

### Post by rmaguir on 2008-04-15
> **warp99 said:**
> Open a terminal, put the DVD in the tray and issue the following:
```
mplayer -vo x11 dvd://
```

What is the output?

Hey!  It actually works (kind of).  

Here's the output:

> 
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 2 titles on this DVD.
There are 9 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: unknown aid: 128.
number of audio channels on disk: 1.
number of subtitles on disk: 0
MPEG-PS file format detected.
VIDEO:  MPEG2  352x240  (aspect 2)  29.970 fps  10000.0 kbps (1250.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 240 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 352 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 352x240 => 352x264 Planar YV12 
[swscaler @ 0x8925250]SwScaler: using unscaled yuv420p -> rgb32 special converter
A:  38.2 V:  38.2 A-V: -0.001 ct:  0.070 1146/1146  4%  2%  1.0% 10 0 

MPlayer interrupted by signal 2 in module: sleep_timer
gnome_screensaver_control()robert@Herman-II:~$ mplayer -vo x11 dvd://
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 2 titles on this DVD.
There are 9 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: unknown aid: 128.
number of audio channels on disk: 1.
number of subtitles on disk: 0
MPEG-PS file format detected.
VIDEO:  MPEG2  352x240  (aspect 2)  29.970 fps  10000.0 kbps (1250.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 240 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 352 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 352x240 => 352x264 Planar YV12 
[swscaler @ 0x8925250]SwScaler: using unscaled yuv420p -> rgb32 special converter



However, the video size is very small.  Maybe three inches by three inches, and there are no controls.

---

### Post by warp99 on 2008-04-15
> **rmaguir said:**
> Hey!  It actually works (kind of).  
However, the video size is very small.  Maybe three inches by three inches, and there are no controls.

It's suppose to do that since it was just a test. It appears that you may not be able to use the xv or gl video driver with your video card. This is a known bug with some Intel graphics chips. You need to change the video driver in mplayer, xine, and/or vlc if you use that program from xv or gl to x11/xshm in the settings/preferences dialog of each program.

In Totem there is no method of changing the video driver so you have to edit the file manually like this:

Open the file in gedit:
```
gedit ~/.gnome2/Totem/xine_config
```
scroll down until you find the following line:
```
# video driver to use
# string, default: auto
#video.driver:auto
```
and change that to the following:
```
# video driver to use
# string, default: auto
video.driver:xshm
```
save the file, now totem will use the x11 driver for video.

Edit:
Here's the reason straight from the developers:
> Question: Does the driver support the Xv extensions?

Answer
To better support the Composite extension, the Intel graphics driver supports --for i915 and later-- textured video which uses the 3D hardware to paint the video directly to the frame buffer instead of using an overlay. This means there's no funny 'blue' image caused by the color key, and it means you can capture video frames with normal X tools.

[http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html)


---

### Post by rmaguir on 2008-04-15
warp99, when I open the file in gedit, it's completely blank!  What's wrong?  Does it just mean I have the file somewhere else?

---

### Post by ubuntu-freak on 2008-04-15
Did you un-blacklist your graphics device to enable desktop effects? My understanding was that xv (xvideo) playback works with your chipset, but not with effects enabled. Using x11 will seriously decrease performance, especially in fullscreen mode. Also, I suggest using VLC for DVD playback, have a look at part 4 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) for details and advice.
 
Nathan

---

### Post by rmaguir on 2008-04-15
reassuringlyoffensive, I love VLC, but it doesn't work either.  None of my DVD programs are working.  

I remember, in order to get the desktop effects of compiz fusion to work, I had to un-blacklist my intel card, but that doesn't seem to be helping me here....

---

### Post by ubuntu-freak on 2008-04-15
> **rmaguir said:**
> reassuringlyoffensive, I love VLC, but it doesn't work either.  None of my DVD programs are working.  

I remember, in order to get the desktop effects of compiz fusion to work, I had to un-blacklist my intel card, but that doesn't seem to be helping me here....

 
What's not helping? Have you disabled effects in System>Appearance>Effects? It was blacklisted for a reason, be patient. Try part 4 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) afterwards.
 
Nathan

---

### Post by warp99 on 2008-04-15
> **rmaguir said:**
> warp99, when I open the file in gedit, it's completely blank!  What's wrong?  Does it just mean I have the file somewhere else?

That's the location of the file. Since the file is local you can use nautilus, the file manager, to move to the directory and open the file with gedit, just remember to turn on view hidden files.

---

### Post by rmaguir on 2008-04-16
Warp99, I did have to click the "show hidden files" to find it, but when I open the "Totem" folder there is no xine_config file.  The only file in there is "state.ini"

---

### Post by warp99 on 2008-04-16
> **rmaguir said:**
> Warp99, I did have to click the "show hidden files" to find it, but when I open the "Totem" folder there is no xine_config file.  The only file in there is "state.ini"

You may be using totem-gstreamer instead of totem-xine, then the file xine_config would not exist on your system. I found a post on how to change all of the media programs to x11 video including totem-gstreamer:

[http://ubuntuforums.org/showpost.php?p=3138952&postcount=7](http://ubuntuforums.org/showpost.php?p=3138952&postcount=7)

Lot easier to make a pointer then type another howto. Sorry about the confusion.

---

### Post by ubuntu-freak on 2008-04-16
> **rmaguir said:**
> Warp99, I did have to click the "show hidden files" to find it, but when I open the "Totem" folder there is no xine_config file.  The only file in there is "state.ini"

 
You can easily use x11 in VLC by going into its preferences. However, like I said before, if you want good quality video playback with your chipset - you need to disable desktop effects.
 
Nathan

---

