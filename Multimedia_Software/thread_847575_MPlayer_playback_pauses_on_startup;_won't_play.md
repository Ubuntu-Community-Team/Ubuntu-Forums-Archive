---
title: "MPlayer playback pauses on startup; won't play"
date: 2008-07-02
forum: Multimedia Software
---

### Post by loneblender on 2008-07-02
All of the videos I've tried with mplayer pause at startup and won't play; there is also no audio.  I can seek forward in time and the video displays the frames properly, but the movie pauses again but will not play by itself.  The frames mplayer stops at are reproducible (see below).

I run Ubuntu 8.04 on a Dell Inspiron 530 with an nVidia geforce 8600 GT graphics card.

The mplayer version and output, as well as some OS information is below; any help is greatly appreciated.  Thank you :-)

$ mplayer movie.avi
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing movie.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  640x256  24bpp  23.976 fps  844.5 kbps (103.1 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2439/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 256 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.50:1 - prescaling to correct movie aspect.
VO: [xv] 640x256 => 640x256 Planar YV12 

A:   0.0 V:   0.2 A-V: -0.167 ct: -0.013   5/  5 ??% ??% ??,?% 0 0 
(I press the right-arrow key once, mplayer pauses again)
A:  12.6 V:  12.6 A-V: -0.085 ct: -0.005 304/304 ??% ??% ??,?% 0 0 
(I press the right-arrow key once, mplayer pauses again)
A:  25.1 V:  25.1 A-V: -0.010 ct: -0.100 602/602 ??% ??% ??,?% 0 0 
(I press the right-arrow key once, mplayer pauses again)
A:  42.6 V:  42.6 A-V: -0.008 ct: -0.100 1022/1022 ??% ??% ??,?% 0 0 
(I press the space bar)
  =====  PAUSE  =====
(I press the space bar again)
A:  42.6 V:  42.6 A-V: -0.003 ct: -0.100 1022/1022 ??% ??% ??,?% 0 0 
(The movie is still paused)
...

$ uname -a
Linux host 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

Please also let me know if other info would be helpful.

---

### Post by zccpop on 2008-07-30
I have met this problem.But I cannot find ideas to fix.
The mplayer is recover without anything.

---

### Post by mc4man on 2008-07-30
gmplayer - (from apps menu) see what happens if you switch audio output to alsa from pulse. 
Or in cli specify alsa as the ao.

---

### Post by Cresho on 2009-09-30
This is rather old but for example, If I disabled xscreensaver in smplayer, it plays the videos after fine.  It seems as if it tries to disable xscreensaver and fails.  in smplayer, there is an option to disable it in general settings.  I play with this switch and my videos play immediately.

I think its in general, general, video...remove checkmark that tells smplayer to disable xscreensaver and it works fast at startup.

my problem was starting up smplayer to play vide and it would pause for a few seconds..like 5

---

### Post by pfifo on 2009-10-21
I am running a fresh install of 8.04.3 mplayer was driving me nuts with the freezing, my solution may or may not be relevant cause in my journey to get this fixed I built mplayer from scratch via linuxfromscratch's directions, but it was still freezing afterwards.

Anyway, I noticed a message in mplayer's output complaining about the selected video output driver not being valid so i tacked on a '-vo x11' onto the command line and it worked. Then i did 'sudo gedit /etc/mplayer/mplayer.conf' and changed the default vo driver in the configuration. Im now enjoying my wmv files in my favorite video player. Hope this helps out, and yes i registered just to post this fix :)

---

### Post by andrew.46 on 2009-10-21
Hi pfifo,

> **pfifo said:**
> then i did 'sudo gedit /etc/mplayer/mplayer.conf' and changed the default vo driver in the configuration.

You might be better to use a *local* configuration file rather than a file that is more usually used for *system* configuration. The usual way to establish a local file of this type is to copy the system file to $HOME:

```
$ mkdir $HOME/.mplayer
$ cp /etc/mplayer/mplayer.conf $HOME/.mplayer/mplayer.config
```

All the best,

Andrew

---

### Post by GoMad on 2009-10-22
I have this issue, I have to press a key to move the movie on. I have tried -vo xv abd -vo x11 and neither prevent this happending.
 
Any more ideas ?
 
Thanks.

---

### Post by GoMad on 2009-10-28
I don't think the 9.0.4 upgrade worls well, did a complete fresh install after downloading RC1 9.10 and all seems ok now, apart from ubuntu locking up but I am going to change the graphics card and memory to seeit that helps.

---

### Post by shanedk on 2009-11-02
I'm having this same problem (upgraded to 9.10 and the videos pause), and see how weird this is:

If I open a shell, and type precisely the mplayer string from the setup, with the video's file name in place of  "%s" of course, then I still get the video pausing.

But if I close out of the MythTV frontend, then go back to the shell and type the exact same command, mplayer plays the video fine with no problems.

Why would this be? Hopefully it'll give someone a clue as to the problem.

---

### Post by NTolerance on 2009-11-02
> **shanedk said:**
> I'm having this same problem (upgraded to 9.10 and the videos pause), and see how weird this is:

If I open a shell, and type precisely the mplayer string from the setup, with the video's file name in place of  "%s" of course, then I still get the video pausing.

But if I close out of the MythTV frontend, then go back to the shell and type the exact same command, mplayer plays the video fine with no problems.

Why would this be? Hopefully it'll give someone a clue as to the problem.

I'm also getting this after upgrading to 9.10.  The problem only occurs when launching mplayer from the MythTV frontend.  I've tried these mplayer switches with no luck:

-vo xv
-vo x11
-ao pulse

---

### Post by irwand on 2009-11-10
After upgrading, I have the same problem as well. I've narrowed it down to the audio part.
If I do '-ao null' or '-ao oss', then I can play the videos just fine while mythfrontend is running. This problem is so annoying. I don't know why I'm having so much problem with pulse audio since 9.04 release. 

There were supposedly fix to the same kind of problem:
[http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
But obviously it doesn't work for me and a couple of people here..

Anyone else have more ideas?

---

### Post by bgiannes on 2009-11-11
i have the same problem, in other forums people are just switching to the internal mythtv player.

---

### Post by J_Coppens on 2009-11-30
I replied but made a mistake (it was quite late yesterday), it didn't apply to pulseaudio. Sry.

---

### Post by morrow on 2009-12-18
Relating to the original issue, you may wanna add/change the line

```
stop-xscreensaver = "no"
```

either in

```
/etc/mplayer/mplayer.conf
```

or 

```
~/.mplayer/config
```

This will stop mplayer from trying to stop a non-existing XScreenSaver.

Note that this is in essence what Cresho has pointed out before, just configuring it in a difference place.

---

### Post by kudude on 2010-02-01
I just upgraded to 9.10 and am now having this problem.  Even if myth is not running, and I have a file in my home directory with all permissions set, mplayer starts and pauses the video (allowing seek, like described)

If I run "sudo mplayer $filename", then it plays fine.  I don't know what sudo has permission to that my user needs.   Any ideas?

---

### Post by rvm4000 on 2010-02-01
Have you tried to use *pulse* for the audio?

mplayer -ao pulse ....

---

### Post by kudude on 2010-02-02
no go, but I do get pointed to bug ticket #440.  Seems there might be a fix, but I don't know how to deal with it in synaptic.  I'm new to ubuntu (from gentoo)


Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 320.0 kbit/22.68% (ratio: 40000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 191.0 (03:11.0) ??,?%

---

### Post by kudude on 2010-02-02
Ok, It's working now.  I added my user to /etc/group wherever I saw audio or pulse.  I'm not sure, but I think I was using alsa before the upgrade.  I think the switch to pulse was accompanied without giving correct user permissions.

The clue here was that it worked as 'sudo'.  Hope that helps someone.

---

### Post by joachimp on 2010-05-29
I was able to fix this [for myth using mplayer] by changing the audio preferences in mythfrontend Utilities/Setup > Setup > General  
to: 
Audio output device: pulseaudio:default
[also, but not sure if necessary] uncheck internal audio controls  
*nothing else worked for me* I tried everything else suggested on this thread, and many others.. This system was originally 8.10, 9.04, 9.10, 10.04, I think myth stopped working somewhere around 9.04....

---

### Post by pedemoz on 2010-06-20
Same problem after upgrade to Lucid.
Same solution as joachimp - set Myth to use PulseAudio by default (Utilities/Setup, Setup, General - Audio output device: pulseaudio:default).

---

