---
title: "Help with XvMC woes"
date: 2009-08-28
forum: Mythbuntu
---

### Post by schwinn on 2009-08-28
I've been trying to troubleshoot this for a while now, and have not been having any success, so hopefully someone can point out my dumb mistake here.

Relevant specs:
Mythbuntu 8.04 (have run a few updates through update manager along the way, as everything SD works fine.)
Athlon XP 3000+
Via KT400 (maybe KT800?) chipset
NVidia 7800GS AGP card (173.14.12 driver installed by EnvyNG)

Short answer is that I can't get XvMC to work on this machine, though videos play fine otherwise. I never cared before, since the CPU could handle the SD streams, but I just installed a pcHDTV 5500 card, so HD is coming out choppy, hence I want to get XvMC working.

I can't even get mplayer xvmc to work, so that's where I'm concentrating my efforts for now. In both myth and mplayer (and xine) they sit at 100% CPU usage, and the machine freezes - I have to kill the process to recover the system.

Mplayer provides the following output when running the video file:
mplayer -vo xvmc -vc ffmpeg12mc 5686_20090825000000.mpg
```
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) XP 3000+ (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.

Playing 5686_20090825000000.mpg.
TS file format detected.
VIDEO MPEG2(pid=2048) AUDIO A52(pid=2049) NO SUBS (yet)!  PROGRAM N. 1
VIDEO:  MPEG2  1920x1080  (aspect 3)  29.970 fps  19392.8 kbps (2424.1 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
vo_xvmc: X-Video extension 2.2
vo_xvmc: X-Video MotionCompensation Extension version 1.1
==========================================================================
Forced video codec: ffmpeg12mc
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] XVMC accelerated codec.
Selected video codec: [ffmpeg12mc] vfm: ffmpeg (FFmpeg MPEG-1/2 (XvMC))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
AUDIO: 48000 Hz, 2 ch, s16le, 384.0 kbit/25.00% (ratio: 48000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
[VD_FFMPEG] Trying pixfmt=0.
VDec: vo config request - 1920 x 1080 (preferred colorspace: MPEG1/2 Motion Compensation and IDCT)
VDec: using MPEG1/2 Motion Compensation and IDCT as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xvmc] 1920x1080 => 1920x1080 MPEG1/2 Motion Compensation and IDCT 
vo_xvmc: Port 275 grabed
vo_xvmc: Found matching surface with id=54434449 on 275 port at 0 adapter
vo_xvmc: Allocated Direct Context
vo_xvmc: data_blocks allocated
vo_xvmc: mv_blocks allocated
vo_xvmc: Motion Compensation context allocated - 8 surfaces
vo_xvmc: idct=1 unsigned_intra=0
vo_xvmc: looking for OSD support
    Subpicture id 0x34344149
vo_xvmc: OSD support by additional frontend rendering

```

I should note, my xorg.conf includes the following:
```

Section "Device"
	Identifier	"Configured Video Device"
	# Option		"UseFBDev"	"true"
	Driver		"nvidia"
	Option		"UseEvents"	"True"
	Option		"XvmcUsesTextures"	"False" # necessary for color Chromakey OSD)
	# Option		"NVAGP"		"1"
	Option		"NoLogo"	"True"
	Option		"RenderAccel"	"True"
	Option		"DPMS"		"False"
EndSection

Section "Extensions"
	Option		"Composite"	"Disabled"
EndSection

```
Note that NVAGP = 1 is commented out - when enabled, /proc/drivers/nvidia/agp/status states that AGP is disabled, which I figured was "wrong" or "bad", so I didn't test it that way (maybe I should have?). I suppose I could try NVAGP=2, but even without that, the status file says AGPGART is enabled, so I figured it wasn't necessary.

Any ideas? I can get more logs if needed... there's much more troubleshooting I have already done, but everything I check says XvMC is installed and enabled in the logs (ie, "Motion Compensation" is showing loaded in their respective logs)... yet I get this lockup when trying to use it.

It should be noted that this particular video file plays fine without XvMC in myth, mplayer, and xine.

The only thing I haven't tried yet is regarding AGP and Nvidia drivers >100.x.x... I have seen a few posts saying there may be some sort of bug on AGP systems with the newer drivers, but nothing definitive. I plan to try some v96 flavor driver that EnvyNG can provide... haven't gotten around to that yet.

---

### Post by xinix on 2009-08-28
Did you follow the directions on this page?  [http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC)

---

### Post by schwinn on 2009-08-28
Yes, I believe I followed everything there:
- drivers installed with EnvyNG (which means I don't need to follow the "Compiling/Installing the driver" section, I assume)
- xorg.conf updated (except for NVAGP=1, which I mentioned in the OP)
- chipset library enabled
- Xorg.0.log "Motion" check passed
- Xorg.0.log "XvmcUsesTextures" showing up (as "False" since that's what's in my conf... most recent user-posts say it should be false, though the wiki says "True"? Which is it supposed to be?)
- didn't try the compiled-program check yet...
- mythfrontend version check passed
- mplayer check fails (as mentioned above, and why I'm here)

And that's where I sit now. Did I miss something? I figure I have to use the 173-driver since the top of the document says that my 7-series card requires this driver to support XvMC... which is why I haven't tried an older driver yet.

I'll try the NVAGP=1 again tonight, and actually run mplayer, but am I supposed to see the cat-status show up as "disabled" when it's working "properly"?

---

### Post by xinix on 2009-08-28
> **schwinn said:**
> Yes, I believe I followed everything there:
- drivers installed with EnvyNG (which means I don't need to follow the "Compiling/Installing the driver" section, I assume)
The EnvyNG driver should be fine, I don't use it myself though.

> **schwinn said:**
> - xorg.conf updated (except for NVAGP=1, which I mentioned in the OP)
Here's what the [[COLOR="Red"]_Nvidia readme_[/COLOR]]("http://us.download.nvidia.com/XFree86/Linux-x86/171.06.01/README/chapter-12.html") says about this setting:
> There are several choices for configuring the NVIDIA kernel module's use of AGP on Linux. You can choose to either use the NVIDIA builtin AGP driver (NvAGP), or the AGP driver that comes with the Linux kernel (AGPGART). This is controlled through the "NvAGP" option in your X config file:

    Option "NvAGP" "0"  ... disables AGP support
    Option "NvAGP" "1"  ... use NvAGP, if possible
    Option "NvAGP" "2"  ... use AGPGART, if possible
    Option "NvAGP" "3"  ... try AGPGART; if that fails, try NvAGP

The default is 3 (the default was 1 until after 1.0-1251).

> **schwinn said:**
> - chipset library enabled
- Xorg.0.log "Motion" check passed
if ```
cat /var/log/Xorg.0.log | grep Motion
``` gave you ```
(II) Loading extension XVideo-MotionCompensation
```
Then XvMC loaded and should be working.

> **schwinn said:**
> - Xorg.0.log "XvmcUsesTextures" showing up (as "False" since that's what's in my conf... most recent user-posts say it should be false, though the wiki says "True"? Which is it supposed to be?)
XvMC works for me with this setting set to "true" or "flase". I'm not exactly sure why the instructions say to set it to flase.  The output of the command will reflect whatever you have in your xorg.conf.  If it is set to true it will report true and same for false.

Have you tried a playback profile in MythTV that uses XvMC?  I created a basic test profile that uses "Standard XvMC" as the decoder.  If you get a grey OSD then XvMC is kicking in.

---

### Post by mitchell2345 on 2009-08-28
heres a better idea.  move to the VDPAU repo or wait a couple of months and use VDPAU.  WAY better than XvMC.

Mitchell

---

### Post by xinix on 2009-08-28
I agree vdpau would be a better solution.  I stayed away from that recommendation because [[COLOR="Red"]_they state_[/COLOR]]("http://www.mythtv.org/wiki/VDPAU#Supported_Cards") that cards lower than the 8xxx series are not supported (the GeForce Go 7700 is the only seires 7xxx card listed).

On the other hand, I have a 6200 card and the 180.xx.x drivers do work, even though the wiki makes it sound like they won't.  I don't get VDPAU though.  I remember that I had trouble switching away from the EnvyNG drivers.  So, I'd do a little research to see if the 7800GS AGP supports VDPAU.  If it does, then the trouble would be worth it.

---

### Post by schwinn on 2009-08-28
Can't do VDPAU on the 7-series, in general - certainly not the 7800GS: [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

I shouldn't have to upgrade the hardware on this system - it used to do XvMC on an older video card (under MythDora)... I just want to get it working here. I don't see any reason why this cannot be done?

---

### Post by schwinn on 2009-08-29
> **xinix said:**
> Have you tried a playback profile in MythTV that uses XvMC?  I created a basic test profile that uses "Standard XvMC" as the decoder.  If you get a grey OSD then XvMC is kicking in.

I wasn't going to bother testing myth yet, since I wanted to make sure the OS is configured properly first - which is why I'm trying to get mplayer or xine to work first.

I'm going to try nvagp=1 (even though the status says disabled) and see if that helps...

---

### Post by schwinn on 2009-08-29
Ok, looks like that did it... NVAGP = 1 gets it to work, even though I get this:
```
cat /proc/driver/nvidia/agp/status 
Status: 	 Disabled

AGP initialization failed, please check the ouput  
of the 'dmesg' command and/or your system log file 
for additional information on this problem.
```

CPU usage is down to 25% now because of xvmc on the video, so it appears that it's all working, even though the status says it's not. Pretty annoying that the XVMC docs don't tell you this, but hey, whatever...

Thanks for the help... I'll try to see if I can help improve documentation to include this issue, so that others can be helped that way, too. Or, maybe it was only me having this problem, haha!

---

### Post by schwinn on 2009-08-29
Incidentally, XvmcUsesTextures = True allows for OSD elements to stop flickering. At one point, I thought it would also restore color on the OSD, but it does not (not while XvMC is running, anyway). So, the "better" setting is to have it = True.

I still get some stuttering when the OSD is up (on HD streams) but that's an issue for another day, I suppose... I'm just happy the XvMC is working now!

---

