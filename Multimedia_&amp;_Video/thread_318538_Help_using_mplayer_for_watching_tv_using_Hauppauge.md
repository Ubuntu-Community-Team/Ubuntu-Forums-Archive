---
title: "Help using mplayer for watching tv using Hauppauge WinTV PVR-150 card"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by leefw on 2006-12-14
Hi

A few months ago I installed a Hauppauge WinTV PVR-150 card (cx23416 based) on my 64-bit Athlon Kubuntu Edgy installation. I initially didn't get it to 'work' and left it a bit, but came back to it recently. I'm using ivtv version 0.7.0 and I register no problems using 'dmesg'. I followed the updated instructions (2006-12-06) at [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy) to set up ivtv.

I changed to the "correct" tv-channel using 'ivtv-tune -teurope-west -cE2 -d/dev/video' and then tested the signal using 'cat /dev/video0 > /tmp/test_capture.mpg'. That seems to work, however audio seems to be missing for some channels? Need to experiment more here...

Anyway, I'd now like to use mplayer to play the tv signal, but running 'mplayer tv://' gives me the output that follows. Can anyone see what is wrong? I'm relatively new to mplayer and have just starting to use it. Let me add that I can watch movie clips and dvd using mplayer from the command line, however I still to look into navigating dvd chapters. The point is that mplayer works, but not for tv. Any ideas? 


MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
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

Playing tv://.
Selected driver: dummy
 name: NULL-TV
 author: alex
Selected input hasn't got a tuner!
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 200 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x200 => 320x200 Planar YV12
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Audio: no sound
Starting playback...

---

### Post by leefw on 2006-12-15
Me again. I think I've come a little further...

I tried the following command:

**  mplayer -tv driver=v4l2:channel=E7 tv://**

which gives a lot of the same output as before, but adds the following (see below). Seems there is a problem with an invalid argument being sent to a ioctl request buffer. I'm not sure what that means... Anyone?

Playing tv://.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Hauppauge WinTV PVR-150
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: STEREO
 Capabilites:  video capture  VBI capture device  tuner  audio  read/write
 supported norms: 0 = PAL-BGH; 1 = PAL-DK; 2 = PAL-I; 3 = PAL-M; 4 = PAL-N; 5 = PAL-Nc; 6 = SECAM-BGH; 7 = SECAM-DK; 8 = SECAM-L; 9 = SECAM-L'; 10 = NTSC-M; 11 = NTSC-J; 12 = NTSC-K;
 inputs: 0 = Tuner 1; 1 = S-Video 1; 2 = Composite 1; 3 = S-Video 2; 4 = Composite 2;
 Current input: 0
 Current format: unknown (0x4745504d)
v4l2: current audio mode is : STEREO
Selected channel: E7 (freq: 189.250)
[B]v4l2: ioctl request buffers failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.[/B]

---

### Post by superm1 on 2006-12-17
Sorry to provide some bad news, but it looks like I identified your troubles:
According to one of the ivtv pages, particularly:
[http://ivtvdriver.org/index.php/Howto#Module_options](http://ivtvdriver.org/index.php/Howto#Module_options)

**What client software is supported besides MythTV?**
[infirit]("http://ivtvdriver.org/index.php?title=User:Infirit&action=edit") 14:56, 16 December 2006 (CET) Anything that can read mpeg files can open the device directly. If you want to do more fancy stuff it will have to support the encoder api. 
At the moment the only software that is capable of using the new encoder api is mplayer 1.0 rc1 and mythtv 0.20.



So this will explain why you're having troubles with mplayer since your not on 1.0RC1.  1.0RC1 was released just right before or just after edgy and didn't make it into Edgy for that reason.

---

### Post by leefw on 2006-12-17
Ok, first off - thanks for taking the time to locate an answer! Appreciate it.

However, I'm not 100% sure I understand your answer. Are we talking about the ivtv driver in general or just this particular version of it that isn't compatible with my version of mplayer? I thought the driver had to be compatible with the kernel version and that was that. In other words not something you can just 'choose'. (As you may have guessed I new to Linux and the kernel is not something I've focused on)

I'm pretty sure this version of the ivtv driver was downloaded recently and I have added 'http://dl.ivtvdriver.org/ubuntu' to Adept as a repository. Maybe that was a bad idea? Maybe I should do the same for mplayer?

So this means that no software client (exept MythTv) can be used for my particular version of the ivtv driver? I am unfamiliar with MythTv, but can that be used as a normal desktop tv-client? I get the impression it's more than that and similar to being it's own Linux distribution. Maybe I'm wrong?

---

### Post by superm1 on 2006-12-17
> **leefw said:**
> Ok, first off - thanks for taking the time to locate an answer! Appreciate it.

However, I'm not 100% sure I understand your answer. Are we talking about the ivtv driver in general or just this particular version of it that isn't compatible with my version of mplayer? I thought the driver had to be compatible with the kernel version and that was that. In other words not something you can just 'choose'. (As you may have guessed I new to Linux and the kernel is not something I've focused on)

I'm pretty sure this version of the ivtv driver was downloaded recently and I have added 'http://dl.ivtvdriver.org/ubuntu' to Adept as a repository. Maybe that was a bad idea? Maybe I should do the same for mplayer?

So this means that no software client (exept MythTv) can be used for my particular version of the ivtv driver? I am unfamiliar with MythTv, but can that be used as a normal desktop tv-client? I get the impression it's more than that and similar to being it's own Linux distribution. Maybe I'm wrong?

Well there is nothing wrong with that repository.  I maintain it and put newer version of ivtv in there.  Bascially this post on the ivtv website is indicating that the old standard for channel control of ivtv is no long valid.  There was a new standard introduced in the last few versions of ivtv.  The only known projects that work with this new standard are mythtv 0.20 or the release candidate for mplayer.  

I think there is a repository hosting the newer mplayer, but I couldn't tell you where it was since I don't know.  You may have luck rolling back to an older ivtv version prior to the control change, but if you go there you're on your own ;).

As for mythtv 0.20, you can set it up on a box already being used as a desktop.  I've got a wiki page written explaining how to do this exact thing.  The page indicates from the ground up how to do it, but you can pick up from a point that you have your box right now.
[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

edit:
One note.  The page indicates to use a seperate partition for recordings.  This isn't necessary, but i'd highly recommend it since the partition will tend to fill up continuously as you schedule things.

---

