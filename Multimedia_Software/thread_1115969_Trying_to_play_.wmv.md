---
title: "Trying to play .wmv"
date: 2009-04-04
forum: Multimedia Software
---

### Post by Trekky0623 on 2009-04-04
I'm trying to get Ubuntu to play .wmv files.  Neither Totem nor VLC would play the audio by default, only the video, so I installed mplayer a well as the w32 codecs.  However, now mplayers plays audio but no video.  Does anyone have any suggestions?

---

### Post by coffeecat on 2009-04-04
Try installing ubuntu-restricted-extras. WMV files are playing fine in VLC, mplayer and Totem in my Jaunty, so they should play OK.

---

### Post by Trekky0623 on 2009-04-04
That didn't fix mplayer, but it did add sound to Totem, which has solved my problem.  Thanks!

---

### Post by kyott81 on 2009-04-04
Hi, I am experiencing the same problems and I have already installed the ubuntu-restricted-extras packet from console...

Can anybody help us? 

Thanks & regards!

---

### Post by wolfen69 on 2009-04-04
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```
then
```
sudo apt-get install w32codecs
```

---

### Post by kyott81 on 2009-04-05
Hi Wolfen! First of all thanks! But I'm still in troubles. I have installed w64codecs &  w32codecs, only w64, and only w32... And no way! :(.

This is the error message that I get on VLC player, thought it runs forward without sound and video:

"No suitable decoder module:
VLC does not support the audio or video format "MSS2". Unfortunately there is no way for you to fix this."

And that's the message from Totem:

"The playback of this movie requires a video/x-asf-unknown decoder plugin which is not installed."

Any Idea???

Thanks and regards!

---

### Post by bonfire89 on 2009-04-24
I'm having this issue too.

---

### Post by lindsay7 on 2009-04-25
Same problem for me too.

---

### Post by wolfen69 on 2009-04-25
```
sudo apt-get-install non-free-codecs
```
this is for jaunty only.

---

### Post by lindsay7 on 2009-04-25
You need to take out the - (dash) between apt-get install.

---

### Post by gjoellee on 2009-04-25
.wmv is the Windows Media Player format, and does under my experience not run in Linux at all.

---

### Post by cotcot on 2009-04-25
Look [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=356656").

---

### Post by ninjapirate89 on 2009-04-25
If you have the original cd's I would recommend re-ripping them into .ogg or at least into .mp3. Although that could potentially take a long time, it is worth it to get rid of Windows' audio format (I know, I did it). 

Edit -> Sorry I'm tired I thought we were discussing .wma not .wmv, but I still say convert to something else if at all possible.

---

### Post by mc4man on 2009-04-25
In a 32 bit install all wmv and wma are playable one way or the other.

Mplayer will play all wmv and wma versions
Amarok will play all wma versions
Other Xine based players should play all wma versions but may have trouble with some wmv3 video codecs

Vlc and gstreamer apps are more hit or miss, most can't handle wmal (lossless), wma3(pro) is again hit or miss with these apps.(more miss than hit, most can play wma2 and wmv3 with wma2 audio

In a *default* 64 bit install due to the lack of anything useful in w64codecs your limited to the built-in capabilities of any individual app and or ffmpeg. 
A wmapro patched mplayer can extend mplayer to wmv3 with wma3(pro) audio
wma lossless isn't possible atm.

---

### Post by bonfire89 on 2009-04-25
> **mc4man said:**
> In a 32 bit install all wmv and wma are playable one way or the other.

Mplayer will play all wmv and wma versions
Amarok will play all wma versions
Other Xine based players should play all wma versions but may have trouble with some wmv3 video codecs


I have a 32 bit installation of jaunty that disagrees. =/


Just prior to the jaunty install I got the same video files to play in mplayer after following some advice... un fortunately I didn't save the link since I had read that the wmv issues were supposed to be fixed in jaunty.

---

### Post by xc3RnbFO8P on 2009-04-25
> I had read that the wmv issues were supposed to be fixed in jaunty.
No problem here.

---

### Post by mc4man on 2009-04-25
> have a 32 bit installation of jaunty that disagrees. =

If your having any issues with wmv and or wma in jaunty then you'd need to post some info about the file
run mplayer from from the command line or otherwise get some codec info

mediainfo is very handy, just open and drop your file onto. (view -> hmtl provides extended info, view -> text can be copied and pasted easier.

For jaunty there is a mediainfo ppa in launchpad

[https://edge.launchpad.net/~mediainfo/+archive/ppa](https://edge.launchpad.net/~mediainfo/+archive/ppa)

((and do make sure you have w32codes installed or the codecs from mplayerhq (see below link "install the codecs" section

suggested reading
[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)

---

### Post by bonfire89 on 2009-04-26
eek

[http://ubuntuforums.org/showthread.php?t=1081070](http://ubuntuforums.org/showthread.php?t=1081070)
looks like I'm just going to dirty up a nice fresh install.

Note, it is only _some_ wmv files that wont play.

I always forget about running from the terminal to get the errors. 

here is some output.

```
me@meezcomp:~/Downloads/$ mplayer censored.wmv 
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM) Duo CPU      L2400  @ 1.66GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing censored.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [MSS1]  800x600  24bpp  1000.000 fps   77.0 kbps ( 9.4 kbyte/s)
Clip info:
 name: censored
 author: censored
 copyright: censored 
 comments: censored
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmsdmod.dll, /usr/lib/win32/wmsdmod.dll, /usr/local/lib/win32/wmsdmod.dll
IMediaObject ERROR: 0x88e67c9  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmsdmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Opening video decoder: [dshow] DirectShow video codecs
Win32 LoadLibrary failed to load: msscds32.ax, /usr/lib/win32/msscds32.ax, /usr/local/lib/win32/msscds32.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=msscds32.ax, r=0xa7a1238)
Failed to create DirectShow filter
ERROR: Could not open required DirectShow codec msscds32.ax.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x3153534D.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [dshow] Win32/DirectShow decoders
Win32 LoadLibrary failed to load: acelpdec.ax, /usr/lib/win32/acelpdec.ax, /usr/local/lib/win32/acelpdec.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=acelpdec.ax, r=0xa7a0ada)
ERROR: Could not open required DirectShow codec acelpdec.ax.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x130.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Exiting... (End of file)

```



thanks for the reminder. I had come into this thread casually not expecting anything, but just saying that there were other people experiencing the issue.

---

### Post by mc4man on 2009-04-26
@ bonfire89

> Win32 LoadLibrary failed to load: wmsdmod.dll, /usr/lib/win32/wmsdmod.dll, /usr/local/lib/win32/wmsdmod.dll
IMediaObject ERROR: 0x88e67c9  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmsdmod.dll.

If you do have a 32 bit install then either w32codecs or mplayer codecs pack isn't installed or mplayer can't find them.

Look in /usr/lib or /usr/local/lib for a codecs folder 

I believe w32codecs will also install a folder link in /usr/lib named win32 that should link to the codecs folder or in some cases a folder named win32 that contains individual links inside.


You should have around 132 files in your codecs folder


The how to you linked to shows how to install the codecs from mplayerhq

---

### Post by Nuked on 2009-05-10
man do I appreciate all of your input around here... I've been able to get my wmv/wma/avi files all working greatly with everyones help :)

---

### Post by Another Monkey on 2009-05-15
I am also having problems with WMV play back.  Totem, VLC and MPlayer all close immediately when I try to play such files.  I tried MPlayer form the command line and got this:
```
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  320x240  24bpp  1000.000 fps  324.0 kbps (39.6 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:230400  align:1
StreamCount r=0x0  1  1
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 320 x 240 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12 
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8005->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 
(This message just keeps appearing)

```

Interestingly, this did play although only with sound.
I am not sure what the X11 message is about - the machine has 3Gb of RAM.  It does use Intel graphics though, could that be the issue?  I can't use Compiz etc for that reason.

---

