---
title: "MP4 Video stutters in all applications on 22.04"
date: 2023-06-04
forum: Multimedia Software
---

### Post by Bhakti108 on 2023-06-04
Just did a complete fresh install of 22.04. I want to use Shotcut for video editing of GoPro and Drone footage. I have done this without issue in previous iterations of Ubuntu. However all Applications, Totem, VLC, and Shotcut are unable to play the MP4.s correctly. There is no error messages. The videos load but jump and wont play smoothly. 

I have checked my NVidia drivers and am using the correct one for my card, I have removed System Monitor as suggested in a thread, I have set Shotcut to proxy, yet nothing seems to work. 

Please can anyone suggest further options as I prefer to edit using this laptop. My other laptop has a smaller screen and runs windows which I dont like, but it does successfully run these same videos for editing purposes. 

TIA

---

### Post by Autodave on 2023-06-04
What nVidia card do you have and what driver are you using?  Where did you get the driver from?

---

### Post by Bhakti108 on 2023-06-04
I did the following 

ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001056sv00001028sd00001494bc03sc00i00
vendor   : NVIDIA Corporation
model    : GF119M [NVS 4200M]
driver   : nvidia-driver-390 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

The correct driver is being used apparantly. I just found out that this problem is also occuring for all MOV files as well as MP4

---

### Post by TheFu on 2023-06-05
CPU, GPU, RAM, DRAM, video codec and resolution all matter for what is possible.
the GF119M is old by video card standards.  Fermi was last used in 2016. It originated in 2010.  GPUs have come a long way sense then. With only 1GB of DRAM, it is underpowered for video editing today.

nVidia dropped support for my 7200 GS in 2018.  The days are numbered for support of my nvidia GT 430, I'm certain.

If you'll please run **inxi -bGz** and post the output, we can see other system information.  For playback, **mpv** seems to be the best option.  If you need a GUI for mpv, check out **smplayer**.  For simple editing, I use **LosslessCut** as an appimage. No idea how well it will work on a system from 2016. Sorry.

---

### Post by qyot27 on 2023-06-05
Either you haven't turned on hardware decoding (which would explain it if the same camera's/drone's footage used to work but doesn't now), or you're using a newer camera/drone that's shooting in HEVC, which the GF119 cannot decode in hardware (it only supports [VDPAU Feature Set D](https://en.wikipedia.org/wiki/Nvidia_PureVideo#Nvidia_VDPAU_Feature_Sets), while HEVC only started to show up in Feature Set E and was only fully accelerated with Set F). That leaves it up to the CPU to do it, and HEVC decoding would be a major workout for a 10-or-so-year-old laptop to do in software, unless it was at smaller resolutions - probably 720p or less; 1080p might be okay, but 4K would be out of the question.

You can use MediaInfo to check the particulars of the video files.

---

### Post by Bhakti108 on 2023-06-06
ran that but got "command 'inxi' not found, but can be installed with:

don't know how to install it.

---

### Post by Bhakti108 on 2023-06-06
How do I turn on Hardware decoding? is it program specific or system wide? There seems to be a lot of information that doesn't appear to be very clear to me, online.

I think your second point might be the issue, that the Go Pro in particular is shooting in HEVC which of course I want for better output of the end product, even if it just for my own enjoyment. I might be forced into finding a decent second hand laptop with better hardware. On age pension I can't afford a new one. 

Thanks for the help all.

---

### Post by TheFu on 2023-06-06
Install it like any other program. It is in the repos.  When running a program from any terminal, if it isn't installed, but it is in a repo, usually the exact command to install it is provided.  Nothing fancy.  Standard Linux for APT-based variants here.  Someone using Ubuntu since 2012, would know how to install programs.

---

### Post by TheFu on 2023-06-06
> **Bhakti108 said:**
> How do I turn on Hardware decoding? is it program specific or system wide? There seems to be a lot of information that doesn't appear to be very clear to me, online.

I think your second point might be the issue, that the Go Pro in particular is shooting in HEVC which of course I want for better output of the end product, even if it just for my own enjoyment. I might be forced into finding a decent second hand laptop with better hardware. On age pension I can't afford a new one. 

Thanks for the help all.

HEVC is h.265 and decoding that in hardware isn't possible for low-end or old GPUs.  I have an nVidia from 1030 and I think it can decode h.265, but it cannot encode it.

h.265 makes sense for 1080p resolutions an higher, if everyone playing it back will have sufficient hardware.
I use h.264 encoding which all my devices support decoding, including raspberry pi v2/v3 and later.
h.264 is good for 720-1080p resolutions.
mpeg2 is good for 480p and lower resolutions.  For these xvid/divx are also good.

See how different codecs are designed for different resolutions?  Pick the right video codec based on the player devices expected and the newest video codec they support in hardware for the resolution used.

These days, h.264 is the safest bet for hardware decoding.  Every Android device supports it.

---

