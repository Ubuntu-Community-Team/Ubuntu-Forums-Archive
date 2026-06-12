---
title: "Desktop video recording problem"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by PaulFXH on 2007-04-22
I',m using a HP Pavilion dv1000 laptop (integrated Intel 915 video card) and I've tried two options to enable recording of my desktop (I have beryl installed).
The options were:
1) recordmy desktop from [here]("http://ubuntuforums.org/showthread.php?t=294605&highlight=recordmydesktop")
2)xvidcap from [here]("http://sourceforge.net/project/downloading.php?group_id=81535&use_mirror=ufpr&filename=xvidcap_1.1.5rc3_i386.deb&63826160")

Both apps seem to install OK and function as expected with, however, the unfortunate fact that neither provides a video I can watch.
For recordmydesktop, I've changed the output file from .ogg to .avi and tried to watch it in both Totem and mplayer. In either case, the screen remains black throughout the length of the video. I've even sent one of these .avi files over to my Wondows box and tried it on WMP10 with the same result.
In the case of xvidcap, after recording for 10-15 seconds, stopping the recording and pressing the Play button, a new window opens up only to close almost immediately without displaying anything of the movie nor providing any error message.

Anybody know what I might be missing here?

---

### Post by charly4711 on 2007-04-23
It would help, if you could start xvidcap from the command line and post the output on crash.

[Edit]
Ack, wrong thread ...
with xvidcap, run mplayer from the command line (like: mplayer test.avi) and see what it says.

---

### Post by PaulFXH on 2007-04-23
Thanks for your reply.
Actually, I had made an error in my post yesterday. While both Totem (in Ubuntu Edgy) and WMP10 (in WinXP) both gave black screens when the .avi file was run, in mplayer an error message was received as follows:
> Error opening/initializing the selected video_out (-vo) device

Perhaps, therefore, a more relevant answer to your request is to provide the terminal output when I run the .avi file in Totem which is as follows:
> ** Message: don't know how to handle video/mpeg, mpegversion=(int)4, framerate=(fraction)15/1, width=(int)1280, height=(int)768
** Message: don't know how to handle video/mpeg, mpegversion=(int)4, framerate=(fraction)15/1, width=(int)1280, height=(int)768
Clearly, two identical messages are received, the first before the .avi file starts running and the second after it has finished.

I believe the problem is solely due to problems with the player (whether Totem, mplayer or WMP10). Therefore the error I am geting when trying to run this file in mplayer is a separate issue and not relevant to my main problem.
Nevertheless, for what it's worth I provide here below the terminal output when I try to run the .avi file in mplayer:
> MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing output1.avi.
AVI file format detected.
VIDEO:  [FMP4]  1280x768  24bpp  15.000 fps  923.7 kbps (112.8 kbyte/s)
Clip info:
 Software: MEncoder 2:0.99+1.0pre8-0ubuntu8
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 181.7 kbit/11.83% (ratio: 22712->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 768 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.67:1 - prescaling to correct movie aspect.
VO: [xv] 1280x768 => 1280x768 Planar YV12 
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
X11 error: BadAlloc (insufficient resources for operation)?,?% 3 0 


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed


---

### Post by charly4711 on 2007-04-24
hmm, can you try recording at a smaller resolution (just to see if it works) and start mplayer with "-vo x11"?

---

### Post by PaulFXH on 2007-04-24
Hi charly4711
Thanks for your suggestion.
Actually, xvidcap now records on my machine but only when I choose a reduced portion of the desktop screen. If I try to get it to record the entire desktop, when I click the Play button, the player opens momentarily and then closes.
So, it appears it doesn`t like to be overloaded.
This improvement resulted after I installed many of the bad and ugly gstreamer codecs (or whatever).
Still struggling with recordMyDesktop, but I believe a breakthrough is not far away.

---

### Post by charly4711 on 2007-04-25
you certainly ARE capturing a rather large area.
However, if you're a version of xvidcap older than 1.1.5rcX you should try the recently released 1.1.5 version to see if the Xdamage support helps you (not that it is turned off by default on beryl or compiz)

---

### Post by PaulFXH on 2007-04-25
Thanks for the reply. 
Actually, the xvidcap version I am using is 1.1.5rc3 which is what's in the Ubuntu repos.
Also, I've now found that running mplayer from a terminal will play the .ogg files from recordMyDesktop as long as they're not too big.
Despite the fact that mplayer runs from a terminal (but not, strangely, from the GUI) it does give a large error message essentially complaining that my HP Pavilion dv1000 laptop (1.46 GHz single-core CPU, 512 MB RAM and integrated Intel 945GM graphics card) is insufficiently resourced to play these videos.
If you are interested in the details I've posted them to post #196 in this [thread]("http://ubuntuforums.org/showthread.php?t=294605&page=20").
Any further comments would be welcome as I've still got an awful lot to learn.
Thanks for your help
Paul

---

### Post by kathe on 2007-04-30
hello friend 

this will help uu

[http://linuxera.com/content/view/207/2/](http://linuxera.com/content/view/207/2/)


kathe :)

---

