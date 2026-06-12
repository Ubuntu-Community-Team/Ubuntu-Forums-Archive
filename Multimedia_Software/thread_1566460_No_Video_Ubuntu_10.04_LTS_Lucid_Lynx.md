---
title: "No Video Ubuntu 10.04 LTS Lucid Lynx"
date: 2010-09-02
forum: Multimedia Software
---

### Post by Blue DaNoob on 2010-09-02
Woke up one morning and my HP Mini no longer plays video. Mplayer and VLC show a black screen with audio only. I was able to play everything, including AVI FLV MPG MP4... everything. Now nothing. 

Flash video plays in my browser. Youtube plays fine. Never had this problem before, usually the other way around. I am running 64 bit. restricted drivers installed long ago. Even the OGG sample videos in the default samples folder don't play any video - just sound. Cheese doesn't work. Camera lights up but no picture (HP Webcam-50 (/dev/video0) is selected and grayed out in Cheese Preferences. bye bye skype.

After battling with flash for #$%##% years, I am surprised that it works fine while Ubuntu has seemed to lose ability to play all video entirely.

Not sure what I did. Would appreciate any suggestions. Thank you.

---

### Post by tripmix on 2010-09-02
Any error messages when playing video inn mplayer from a terminal? What about if you run it as root? Or in a different video mode like gl or fbdev in console? You might need sudo to access fbdev.

---

### Post by Blue DaNoob on 2010-09-02
first attempt: mplayer directory/file...

Mplayer not installed. use sudo apt-get. 

Installed Mplayer. Weird, I never uninstalled...

Second attempt in terminal:

~$ mplayer /usr/share/example-content/Ubuntu_Free_Culture_Showcase/UbuntuIsHumanity.ogv
Creating config file: /home/sefton/.mplayer/config
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /usr/share/example-content/Ubuntu_Free_Culture_Showcase/UbuntuIsHumanity.ogv.
[Ogg] stream 0: video (Theora v3.2.1), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  320x240  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 Artist: Andrew Higginson
 Name: Ubuntu Is Humanity
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x7ff498bf39a0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 320x240 => 320x240 Planar YV12 
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->176400)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:  27.9 V:  27.9 A-V:  0.000 ct: -0.010 836/836  5%  1%  0.9% 0 0 
Exiting... (Quit)

Still no video, Black Screen.

Thanks for your help!

---

### Post by tripmix on 2010-09-02
Looks too me like there is something wrong with your codec
```
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x7ff498bf39a0]Missing extradata!
Could not open codec.
VDecoder init failed
``` That would explain why flash works as it has it's own codec but so do vlc so that should not fail even if your codecs have gotten corrupted somehow. Strange, what do vlc say when you run that in a terminal? You might also want to try to force a different codec in mplayer like so "mplayer -vc codecname" you can get a list of all codecs on your system with "mplayer -vc help"

What output do you get from this command?```
mplayer -fps 15 tv:// -tv driver=v4l2:device=/dev/video0

```
Both player failing like that suggests it has problems accessing the overlay layer but nothing in mplayers output suggests that. What happens if you go to console by ctrl+alt+f1 and run "sudo mplayer -vo directfb videofile"? directfb can be a little tricky sometimes but if you can get a picture with that at least you'd know it's not the codecs which would suggest its some kind of permission issue.

---

### Post by Blue DaNoob on 2010-09-02
Thanks for your help. Here is the VLC in Terminal Output:

:~$ vlc /usr/share/example-content/Ubuntu_Free_Culture_Showcase/UbuntuIsHumanity.ogv
VLC media player 1.0.6 Goldeneye
[0x11934b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x7fb290002da8] main input error: ES_OUT_RESET_PCR called
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x2439718] pulse audio output: No. of Audio Channels: 2

Here is the output from the MPlayer Terminal Command:

:~$ mplayer -fps 15 tv:// -tv driver=v4l2:device=/dev/video0
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: HP Webcam-50
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Packed YUY2)
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
FPS forced to be 15.000  (ftime: 0.067).
Starting playback...
v4l2: select timeout ??% ??,?% 0 0 
v4l2: ioctl set mute failed: Invalid argument
v4l2: 214 frames successfully processed, 24919809 frames dropped.

Exiting... (Quit)

and that Last Command:

~$ sudo mplayer -vo directfb /usr/share/example-content/Ubuntu_Free_Culture_Showcase/UbuntuIsHumanity.ogv
[sudo] password for ******: 
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /usr/share/example-content/Ubuntu_Free_Culture_Showcase/UbuntuIsHumanity.ogv.
[Ogg] stream 0: video (Theora v3.2.1), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  320x240  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 Artist: Andrew Higginson
 Name: Ubuntu Is Humanity
commandline read: mplayer
commandline read: -vo
commandline read: directfb
commandline read: /usr/share/example-content/Ubuntu_Free_Culture_Showcase/UbuntuIsHumanity.ogv

   ~~~~~~~~~~~~~~~~~~~~~~~~~~| DirectFB 1.2.8 |~~~~~~~~~~~~~~~~~~~~~~~~~~
        (c) 2001-2008  The world wide DirectFB Open Source Community
        (c) 2000-2004  Convergence (integrated media) GmbH
      ----------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2010-04-09 12:41) 
(*) Direct/Memcpy: Using libc memcpy()
(*) Direct/Thread: Started 'VT Switcher' (-1) [CRITICAL OTHER/OTHER 0/0] <8388608>...
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: Power Button (1) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: Lid Switch (2) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: Power Button (3) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: Macintosh mouse button emulatio (4) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: AT Translated Set 2 keyboard (5) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: Logitech USB Receiver (6) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: HP Webcam-50 (7) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: SynPS/2 Synaptics TouchPad (8) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: Video Bus (9) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: HDA Digital PCBeep (10) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: HDA Intel Mic at Ext Front Jack (11) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Linux Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: HDA Intel HP Out at Ext Front J (12) 0.1 (directfb.org)
(*) Direct/Thread: Started 'Keyboard Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: Keyboard 0.9 (directfb.org)
(*) Direct/Thread: Started 'PS/2 Input' (-1) [INPUT OTHER/OTHER 0/0] <8388608>...
(*) DirectFB/Input: IMPS/2 Mouse 1.0 (directfb.org)
(*) DirectFB/Genefx: MMX detected and enabled
(*) DirectFB/Graphics: MMX Software Rasterizer 0.6 (directfb.org)
(*) DirectFB/Core/WM: Default 0.3 (directfb.org)
(*) FBDev/Surface: Allocated 1024x600 32 bit RGB32 buffer (index 0) at offset 0 and pitch 5120.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x7faedce409a0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x7faedc1d9660]using unscaled yuv420p -> rgb32 special converter
VO: [directfb] 320x240 => 320x240 BGRA 
 (!!!)  *** WARNING [letting unprivileged IDirectFBDisplayLayer::GetSurface() call pass until cooperative level handling is finished] *** [../../../src/display/idirectfbdisplaylayer.c:174 in IDirectFBDisplayLayer_GetSurface()]
(*) FBDev/Mode: Setting 1024x600 RGB32
(*) FBDev/Mode: Switched to 1024x600 (virtual 1024x600) at 32 bit (RGB32), pitch 5120
(*) FBDev/Surface: Allocated 1024x600 32 bit RGB32 buffer (index 0) at offset 0 and pitch 5120.
(*) FBDev/Surface: Allocated 1024x600 32 bit RGB32 buffer (index 0) at offset 0 and pitch 5120.
(*) FBDev/Mode: Setting 1024x600 RGB32
(*) FBDev/Mode: Switched to 1024x600 (virtual 1024x1200) at 32 bit (RGB32), pitch 5120
 (!!!)  *** WARNING [unable to adjust heap offset] *** [../../../systems/fbdev/surfacemanager.c:167 in dfb_surfacemanager_adjust_heap_offset()]
(*) FBDev/Surface: Allocated 1024x600 32 bit RGB32 buffer (index 1) at offset 3072000 and pitch 5120.
(!) [ 2823:    0.000] --> Caught signal 11 (at 0x7faed33b4000, invalid permissions) <--
 (!!!)  *** WARNING [still objects in 'Layer Region Pool'] *** [../../../lib/fusion/object.c:241 in fusion_object_pool_destroy()]
 (!!!)  *** WARNING [still objects in 'Layer Context Pool'] *** [../../../lib/fusion/object.c:241 in fusion_object_pool_destroy()]
 (!!!)  *** WARNING [still objects in 'Surface Pool'] *** [../../../lib/fusion/object.c:241 in fusion_object_pool_destroy()]


MPlayer interrupted by signal 6 in module: init_video_codec
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]

---

### Post by Blue DaNoob on 2010-09-02
This is interesting.... I have an external monitor attached, but when I shut down, unplug the monitor, reboot, then play video, there is no problems.... everything works again. Shut computer, plug in monitor, reboot, no video!!! 

I was able to play movies on a big screen tv connected to VGA no problem... This is a small monitor, 1280X1024. I was able to play video on it before...

The only thing I think I've done recently, besides updates, is let google install the video plugin for chrome... I can't imagine that did it, but can't think of anything else.

The netbook drives both monitors (spanning) no problems.... weird that it just won't play video anymore.

---

### Post by andrew.46 on 2010-09-02
Hi Blue,

Perhaps try the following:

```

mplayer **[COLOR="Red"]-vo x11[/COLOR]** /usr/share/example-content/Ubuntu_Free_Culture_Showcase/UbuntuIsHumanity.ogv

```

Andrew

---

### Post by shimu on 2010-09-07
If both of the dual monitors are on, flv does not play (dark window). If only one is on, it plays. Been hoping it would be taken care of for quite some time. Using Lucid Lynx 64bit. I should probably try more things, but just saw this, wanted to let anybody who is interested, know, as quick info.

---

### Post by taz35 on 2010-09-12
Thanks,
I have nvidia geforce ge9300 ge with two monitors and video is blank unless I run > mplayer -vo x11 myvideoname

---

### Post by PhillipKent on 2010-10-17
I get the same behaviour in Ubuntu 10.04 running on a Macbook (generation 2,1).

A similar workaround to the already mentioned is to edit the preferences in VLC under Video, Display, item output, change from 'Default' to 'X11 video output'.

---

### Post by treunanen on 2010-12-12
I have similar behavior on my HP 2133 MiniNote. I can get the video to be displayed on external monitor with vlc and mplayer, but few things are bothering me.

With VLC the video is cracking and becomes delayed when I change the Video output to X11 instead of default.

mplayer works ok.

---

### Post by Tijok on 2011-01-12
Hey everyone,

Just wanted to say that this thread was a huge help to me, as I was having the exact problem the OP cited, where both Totem and VLC would play audio, but only a black screen of video whenever I tried to play video files.

The solution that worked for me was to switch the Output mode in VLC's video preferences (Tools - Preferences - Video - Output) over to "X11 Video Output". 

This solved a problem that I had been trying to fix for a full day now, and was quite vexing. FWIW, the system set up is:
Intel E5200
Gigabyte G41 Mobo
Nvidia Geforce 210

A big thanks to everyone!

---

### Post by BicyclerBoy on 2011-01-12
What's the DirectFB layer doing for you ?
Because it seems to be causing the errors.

Do you have the intel atom 845 chipset (850 family) ?
Do you use the intel driver ?

---

