---
title: "Problem with EasyCap device in Natty"
date: 2011-05-09
forum: Multimedia Software
---

### Post by deb8torGG on 2011-05-09
Hi,

Just wondering if anyone could offer some advice to the issue I'm having with the install of the easycap driver on my laptop.

I have followed the instructions in the readme to compile and install the driver and have come unstuck at one point.  

The readme says at step 4
"If either /dev/video# or /proc/asound/EasyALSA# is missing then something
is wrong and it will be necessary to do some trouble-shooting."

I have the easycap1 device
ls -s /dev/easycap*
/dev/easycap1

But not the /proc/asound/EasyALSA#.  The readme saysI need to do some troubleshooting but further down the readme there is no help with this particular issue.

Can anyone shed any light on this at all ??

Here is the output from the driver re-install I did incase something went wrong the first time.

kernel directory is /lib/modules/2.6.38-8-generic/build
snd_card_new() will not be used
snd_card_create() will be used
<media/v4l2-device.h> will be included
struct v4l2_file_operations OK
unlocked_ioctl required
v4l2_file_operations.unlocked_ioctl will be used
not overwriting top level Makefile
not overwriting src/Makefile
not overwriting tools/Makefile
make clean OK
make OK
depmod OK
copied OK
depmod OK
unchanged /etc/modprobe.d/easycap.conf
modprobe OK
unchanged /etc/udev/rules.d/57-easycap.rules
unchanged /lib/udev/rules.d/57-easycap.rules


Cheers and many thanks

---

### Post by rmt1947 on 2011-05-09
Hi,

I used the driver a few days ago on Natty without difficulty, so I'm not sure what is causing the audio problem you are encountering.  Your installation is successful, so something is going wrong at the stage where the EasyCAP is plugged in.  Are there other video or audio capture devices on your computer in addition to the EasyCAP?  Are there messages tagged "easycap" in file /var/log/kern.log mentioning "ERROR" or "MISTAKE"?

You might prefer to post your reply on the principal thread at

[http://ubuntuforums.org/showthread.php?p=10564101&posted=1](http://ubuntuforums.org/showthread.php?p=10564101&posted=1)

Mike

---

### Post by deb8torGG on 2011-05-09
hey mate thanks for the reply.

I have managed to get a picture now but only for a short period of time then I just get grey lines.  I'm not sure if the audio is working as there doesn't seem to be any sound.  I really I have no idea of how to record this input to see if the audio and video comes up in the saved capture.  

Does mplayer capture the audio at all ??

I have saved a image of what I see and also the is the ouput of the mplayer command I used.  

Once again thanks for the help Cheers...

mplayer -tv driver=v4l2:device=/dev/easycap1:input=1:width=640:height=480:outfmt=yuy2: alsa:adevice=copy:buffersize=1024:fps=25:amode=2:audiorate=8000:forceaudio:immediatemode=0:norm=PAL -vfm skiploopfilter=all tv://
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing alsa:adevice=copy:buffersize=1024:fps=25:amode=2:audiorate=8000:forceaudio:immediatemode=0:norm=PAL.
File not found: 'alsa:adevice=copy:buffersize=1024:fps=25:amode=2:audiorate=8000:forceaudio:immediatemode=0:norm=PAL'
Failed to open alsa:adevice=copy:buffersize=1024:fps=25:amode=2:audiorate=8000:forceaudio:immediatemode=0:norm=PAL.


Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: EasyCAP DC60
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = PAL_BGHIN; 1 = NTSC_N_443; 2 = PAL_Nc; 3 = NTSC_N; 4 = SECAM; 5 = NTSC_M; 6 = NTSC_M_JP; 7 = PAL_60; 8 = NTSC_443; 9 = PAL_M; 10 = PAL_BGHIN_SLOW; 11 = NTSC_N_443_SLOW; 12 = PAL_Nc_SLOW; 13 = NTSC_N_SLOW; 14 = SECAM_SLOW; 15 = NTSC_M_SLOW; 16 = NTSC_M_JP_SLOW; 17 = PAL_60_SLOW; 18 = NTSC_443_SLOW; 19 = PAL_M_SLOW;
 inputs: 0 = CVBS0; 1 = CVBS1; 2 = CVBS2; 3 = CVBS3; 4 = CVBS4; 5 = S-VIDEO;
 Current input: 0
 Current format: YUYV
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
==========================================================================
Audio: no sound
Starting playback...
V:   0.0 123/123 ??% ??% ??,?% 0 0

---

### Post by rmt1947 on 2011-05-09
Hi,

The grey-bar image (testcard) means that the front-end video chip has lost lock on the analogue input video signal.  This is puzzling, since you do get a picture initially.  Hmm.

If you are not seeing any /proc/asound/EasyALSA# the driver has not obtained control of your audio source, and in these circumstances it is essential ***not*** to even ***ask*** mplayer for audio output (otherwise mplayer gets confused and the ***video*** stream becomes disrupted).  I suggest trying an mplayer command such as:

```
mplayer tv:// -tv driver=v4l2:norm=PAL_BGHIN:width=640:height=480:outfmt=uyvy:device=/dev/easycap1:input=1:fps=25:noaudio -hardframedrop -vo xv

```
This should give sustained silent video.

Mike

---

### Post by deb8torGG on 2011-05-10
Hey Mike,
 
Yeah I used the command as you have put in the thread but still no go.  There is the initial bit of video that is shown then grey bars.  It really isn't the best capture device so maybe it just doesn't work that well with linux or something.  I have used it in XP and it has worked there.  
 
I do run linux off a USB key so this might be part of the problem.  I guess I should have put that in the original post.  My apologies for that.
 
Many thanks for your assistance

---

### Post by maestrodrex on 2011-06-14
Heya guys, I'm also using Natty and my easycap002 can't be detected. I'm using it in Windows 7 and XP and it works fine. Can anyone probably tell me the step by step again in installing the drivers and testing my device. Oh and is easycap002 same as easycap DC60 or whatever it is? Thanks a bunch.

---

### Post by Jared Oberhaus on 2011-11-22
The key is to pass the param "bars=0" to the easycap kernel module; this seems to work for me:

[FONT="Courier New"]modprobe easycap 'bars=0'[/FONT]

See my [blog post]("http://jared-oberhaus-tech-notes.blogspot.com/2011/11/easycap-dc60-and-ubuntu-1110.html").

> **rmt1947 said:**
> Hi,

The grey-bar image (testcard) means that the front-end video chip has lost lock on the analogue input video signal.  This is puzzling, since you do get a picture initially.  Hmm.

If you are not seeing any /proc/asound/EasyALSA# the driver has not obtained control of your audio source, and in these circumstances it is essential ***not*** to even ***ask*** mplayer for audio output (otherwise mplayer gets confused and the ***video*** stream becomes disrupted).  I suggest trying an mplayer command such as:

```
mplayer tv:// -tv driver=v4l2:norm=PAL_BGHIN:width=640:height=480:outfmt=uyvy:device=/dev/easycap1:input=1:fps=25:noaudio -hardframedrop -vo xv

```
This should give sustained silent video.

Mike

---

