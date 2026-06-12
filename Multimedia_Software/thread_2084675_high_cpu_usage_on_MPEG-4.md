---
title: "high cpu usage on MPEG-4"
date: 2012-11-16
forum: Multimedia Software
---

### Post by KisteBecks on 2012-11-16
hi,

on my 12.04.1 ubuntu playing a .avi file in totem which contains XVID MPEG-4 uses between 50% and 70% for the process.
both cores show 50-70% cpu usage, somehow.
using mplayer cpu usage drops to 30% for the process below:

```

/usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none

```

since this is a amd x2 cpu isnt that too much? or does mpeg-4 need this kind of processing power?
i just installed the ati/amd driver for the gfx card via the ubuntu drivers dialog.

snippet from Xorg.0.log, looks like its running:
```

[    26.377] (II) fglrx(0): [uki] DRM interface version 1.0
[    26.377] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    26.378] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    26.378] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0xb6066000
[    26.378] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    26.378] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    26.378] (II) fglrx(0): swlDriScreenInit done
[    26.378] (II) fglrx(0): Kernel Module Version Information:
[    26.378] (II) fglrx(0):     Name: fglrx
[    26.378] (II) fglrx(0):     Version: 8.96.4
[    26.378] (II) fglrx(0):     Date: Mar 12 2012
[    26.378] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    26.378] (II) fglrx(0): Kernel Module version matches driver.
[    26.378] (II) fglrx(0): Kernel Module Build Time Information:
[    26.378] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-32-generic-pae
[    26.378] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[    26.378] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    26.378] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    26.378] (II) fglrx(0): [uki] register handle = 0x00004000
[    26.438] (II) fglrx(0): DRI initialization successfull

```

but no difference in cpu usage :(



video information from mplayer:

```

mplayer data/schlaptop/Fringe\ S04\ DVDRip\ XviD\ REWARD/fringe.s04e01.dvdrip.xvid-reward.avi 
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing data/schlaptop/Fringe S04 DVDRip XviD REWARD/fringe.s04e01.dvdrip.xvid-reward.avi.
libavformat version 53.21.0 (external)
Mismatching header version 53.19.0
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x352  12bpp  23.976 fps  982.3 kbps (119.9 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
Load subtitles in data/schlaptop/Fringe S04 DVDRip XviD REWARD/
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Could not grab port 143.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[mp3float @ 0xb639cea0]Header missing
AUDIO: 48000 Hz, 2 ch, floatle, 130.5 kbit/4.25% (ratio: 16314->384000)
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)

```

---

### Post by BicyclerBoy on 2012-11-16
The only way you will get CPU usage down is via h/w accelerated decode & overlay.

Some models of AMD GPU are support through the VA-API.
The proprietary catalyst driver is probably best.
VA-API is not as full featured as VDPAU.
And AMD XvBA on linux is about 5 years behind VDPAU on nVidia.

Your mplayer stdout shows it trying (& failing) to use VDPAU.
VDPAU is an nVidia API but is partially supported by nouveau (nVidia h/w) & Radeon driver (AMD h/w).

sudo apt-get install xvba-va-driver vainfo

Then run:
vainfo

Then setup mplayer to use va-api

I could not see your video card model..you could post the entire Xorg.0.log file..

---

### Post by KisteBecks on 2012-11-18
thx for the answer, i will switch the card for a nvidia one.

---

### Post by Yellow Pasque on 2012-11-18
I would try xbmc first:
```
sudo apt-add-repository ppa:wsnipex/xbmc-xvba
sudo apt-get update
sudo apt-get install xbmc
sudo amdconfig --set-pcs-u32=MCIL,HWUVD_H264Level51Support,1
```

---

### Post by KisteBecks on 2012-12-22
that could work, but im just not in the mood todo any more testing in this area.
got enough todo already, thx anyway.

---

