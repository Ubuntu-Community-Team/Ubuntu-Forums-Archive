---
title: "Video scrambled when using mplayer/Xine/VLC"
date: 2007-11-22
forum: Mythbuntu
---

### Post by ubnewbie2 on 2007-11-22
I have been copying some recorded TV from my old myth box, onto my new one, via NFS.  (Just copying the mpg files to a spare directory, not trying to integrate them into the recorded programs on the box.)

I copied a few, and played them using vlc on the new box. I deleted some and kept some to watch later.  I then set it to copy all the rest of them (300GB or more) and went to bed.

This morning I tried to play some of the new ones, and vlc (and mplayer and xine) just display scrambled video as they play.  I even tried one of the one's from last night that played previously - same result.

Worse still, I went back into mythfrontend and it showed scrambled video on live TV, and showed a pink screen playing a recorded show - and it locked up.

I rebooted the box, and mythfrontend was back to working properly.  However, trying to play the copied mpg files in mplayer/vlc/xine again shows scrambled video, and his stuffs mythfrontend again.  I have repeated this a few times.  I even rebooted, test myth was ok, then tried to play one of the file from last night that was good, first.  No result - still scrambled video.

This has me really worried. Has anyone ANY ideas what is going on?

---

### Post by ubnewbie2 on 2007-11-22
Just wanted to add, running mplayer from the command line, there was one error before it displayed the scrambled video

"selected video_out device is incompatible with this codec"

maybe that's a clue?

---

### Post by superm1 on 2007-11-22
Do you have proprietary drivers installed?  If not, please do install them (assuming they are available).

If you do have them installed, I suspect that you don't have the video overlay enabled.

---

### Post by ubnewbie2 on 2007-11-22
> **superm1 said:**
> Do you have proprietary drivers installed?  If not, please do install them (assuming they are available).

If you do have them installed, I suspect that you don't have the video overlay enabled.


Thanks for the response, as I said, this is worrying me a bit.

Yes, I'm using the proprietary drivers (nvidia).   So, somehow this video overlay has become disabled?  

How can I check and/or turn it back on?  The only things I think I have changed since mplayer/vlc worked last might be a screen res change and I think I changed the deinterlacing in myth playback (to linear blend).

---

### Post by hanzomon4 on 2007-11-22
Do you have the win32codecs installed?

---

### Post by ubnewbie2 on 2007-11-22
> **hanzomon4 said:**
> Do you have the win32codecs installed?

Yes I do, and I did wonder if they might have become corrupted, at least at first, but these video mpgs that won't play are direct recorded from DVB-T cards (streamed from the TV station).  They don't use w32 codecs do they?

---

### Post by ubnewbie2 on 2007-11-23
I have captured the full output from mplayer.  This is still happening even after disabling and reenabling the restricted driver (with consequent reboots). The driver certainly becomes unstable after trying this, eventually locking mythbuntu up.  Is it possible my cheap Geforce 7200 is flaky, or that the current driver version is flaky?

```
$ mplayer wire.mpg
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 
107, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote 
control.

Playing wire.mpg.
TS file format detected.
VIDEO MPEG2(pid=512) AUDIO MPA(pid=650) NO SUBS (yet)!  PROGRAM N. 1
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  15000.0 kbps (1875.0 
kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder 
libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
gnome_screensaver_control().009 ct: -0.168 100/100  7%  1%  2.6% 0 0 
```

---

### Post by axelsvag on 2007-11-23
Do you mean by scrambled that it just shows a lot of colours?

---

### Post by ubnewbie2 on 2007-11-23
> **axelsvag said:**
> Do you mean by scrambled that it just shows a lot of colours?

Yes.  Sort of like what we used to call "snow" on the TV when it was off station, but in colour - lot's of colours, but a lot of green, all in small semi random pixels, or groups of pixels.

---

### Post by axelsvag on 2007-11-24
I have the same problem. I have tried to sort the problem out but have not succeded. Many seems to have the same illness in the system. Some people mean that it is caused but bad nvidia software. And it does not seems to be solved the the new beta nvidia. I have seen that some believe that the problem get solved if you downgrade the nvidia driver and yet some don´t think it will work. I use a different but awkvard method.  I have to shut down the frontend and log out and  log in from the desktop. Then the mythtv interface is back. After that you have to shut the frontend down without starting any mythtv application. After that at least I can play files from the desktop interface without any scrambling. But.... when you start the frontend again the picture in mythtv will have the same scrambling so you have to log off and log on the desktop again to be able to make the mythtv to work. I hope somebody soon will find the bug that causing this problem.

---

### Post by ubnewbie2 on 2007-11-24
> **axelsvag said:**
> I have the same problem. I have tried to sort the problem out but have not succeded. Many seems to have the same illness in the system. Some people mean that it is caused but bad nvidia software. And it does not seems to be solved the the new beta nvidia. I have seen that some believe that the problem get solved if you downgrade the nvidia driver and yet some don´t think it will work. I use a different but awkvard method.  I have to shut down the frontend and log out and  log in from the desktop. Then the mythtv interface is back. After that you have to shut the frontend down without starting any mythtv application. After that at least I can play files from the desktop interface without any scrambling. But.... when you start the frontend again the picture in mythtv will have the same scrambling so you have to log off and log on the desktop again to be able to make the mythtv to work. I hope somebody soon will find the bug that causing this problem.


I hope so too.

One thing, it is interesting that myth itself uses mplayer to play it's video's - and that works.  I notice it explicitly calls xv as the output (-vo xv) and I haven't tried that from the desktop yet.  It's a big election night here, so I might wait until tomorrow before I play around with myth :)

---

### Post by J0ris on 2007-11-24
I have the same problem as well. I can generalise it even further: if you play any kind of video in myth frontend whether television or other, then exit myth frontend and try play any video with mplayer, vlc or xine, this will not work and you get a green or pink scrambled screen. If you then open up myth frontend again and try to play any video, this will not work any more either.
If you play any video right after boot-up with mplayer, vlc or xine, this will work perfectly. When you then open up myth frontend no video will work. When you then close myth frontend again and try playing any video using mplayer, vlc or xine this will not work either any more. 
It would appear that myth frontend video or tv and video or tv throught the other three players are mutually exclusive no matter what the format of the video is.

I'm not sure how relevant this is but I mention it anyway for reasons of completeness, I also run a dvb-t card.

So, this may be some malfunctioning nvidia proprietry driver? Is there anybody who can be more definite about this? Or give me a clue as to how to remedy this or what kind of information is required?

cheers,
J0ris

Edit: I suppose there is some shared resource that myth frontend doesn't like sharing?

---

### Post by williammanda on 2007-11-24
> **J0ris said:**
> I have the same problem as well. I can generalise it even further: if you play any kind of video in myth frontend whether television or other, then exit myth frontend and try play any video with mplayer, vlc or xine, this will not work and you get a green or pink scrambled screen. If you then open up myth frontend again and try to play any video, this will not work any more either.
If you play any video right after boot-up with mplayer, vlc or xine, this will work perfectly. When you then open up myth frontend no video will work. When you then close myth frontend again and try playing any video using mplayer, vlc or xine this will not work either any more. 
It would appear that myth frontend video or tv and video or tv throught the other three players are mutually exclusive no matter what the format of the video is.

I'm not sure how relevant this is but I mention it anyway for reasons of completeness, I also run a dvb-t card.

So, this may be some malfunctioning nvidia proprietry driver? Is there anybody who can be more definite about this? Or give me a clue as to how to remedy this or what kind of information is required?

cheers,
J0ris

Edit: I suppose there is some shared resource that myth frontend doesn't like sharing?

**Several other threads have been started concerning this same problem as well as the solution also solves another lockup problem. See the following threads:**

[http://ubuntuforums.org/showthread.php?t=572057](http://ubuntuforums.org/showthread.php?t=572057)

[http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)
[B]
I had the same problem JOris and upgraded the Nvidia driver to ver 169.04. Download it here:[/B]
i386: [http://www.nvidia.com/object/linux_d...32_169.04.html](http://www.nvidia.com/object/linux_d...32_169.04.html)
x64 : [http://www.nvidia.com/object/linux_d...64_169.04.html](http://www.nvidia.com/object/linux_d...64_169.04.html)

**I then followed these instructions:**

Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

* development tools like make and gcc are installed
* the linux-headers package matching the installed Linux kernel is installed
* the pkg-config and xserver-xorg-dev packages are installed
* the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

/lib/linux-restricted-modules/.nvidia_new_installed

**Then I did these steps:**

Ctrl-Alt-F1
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run
sudo /etc/init.d/gdm start

SInce updating the driver I haven't had any video issues or lockups.
Thanks

---

### Post by ubnewbie2 on 2007-11-24
Thanks very much for that info.

I noted also, from one of those  threads,  that nVidia have acknowledged the bug and intend to fix it.  I hope it's in the next release.

---

### Post by axelsvag on 2007-11-25
> **williammanda said:**
> **Several other threads have been started concerning this same problem as well as the solution also solves another lockup problem. See the following threads:**

[http://ubuntuforums.org/showthread.php?t=572057](http://ubuntuforums.org/showthread.php?t=572057)

[http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)
[B]
I had the same problem JOris and upgraded the Nvidia driver to ver 169.04. Download it here:[/B]
i386: [http://www.nvidia.com/object/linux_d...32_169.04.html](http://www.nvidia.com/object/linux_d...32_169.04.html)
x64 : [http://www.nvidia.com/object/linux_d...64_169.04.html](http://www.nvidia.com/object/linux_d...64_169.04.html)

**I then followed these instructions:**

Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

* development tools like make and gcc are installed
* the linux-headers package matching the installed Linux kernel is installed
* the pkg-config and xserver-xorg-dev packages are installed
* the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

/lib/linux-restricted-modules/.nvidia_new_installed

**Then I did these steps:**

Ctrl-Alt-F1
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run
sudo /etc/init.d/gdm start

SInce updating the driver I haven't had any video issues or lockups.
Thanks


Sounds like you have found the solution. Before I start to follow your instructions I would like to ask you a few newbie questions first
1. About the linux headers which package should be installed to check that it meets the kernel?
2. What does the purge command mean? Or is it impossible to use synaptic to uninstall?

---

### Post by tuckie on 2007-11-26
I had the same problem, and was able to get it working after uninstalling the nvidia driver, rebooting, reinstalling it, and rebooting once more.

---

### Post by apauna on 2007-12-14
I had simular problems and found that enableing the -V xxmc for NVIDIA fixed me.

```
xine -pfhq -D -V xxmc --no-splash dvd:/%s
```

may want to check out my findings on forum link:
[http://ubuntuforums.org/showthread.php?t=639186]("http://ubuntuforums.org/showthread.php?t=639186")

Hope this helps!

---

