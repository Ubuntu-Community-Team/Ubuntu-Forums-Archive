---
title: "No VDPAU in Lucid"
date: 2010-06-09
forum: Multimedia Software
---

### Post by padukes on 2010-06-09
Hi All,

I upgraded from Karmic to Lucid today and my VDPAU has disappeared (I use it for mythtv).

vdpauinfo shows this:
```

doug@freshertv:~$ vdpauinfo
display: :0.0   screen: 0
Error creating VDPAU device: 1

```

mplayer shows this:
```
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.

```

Myth shows this:
```
2010-06-09 16:30:33.081 VDPAU Error: Error at mythrender_vdpau.cpp:1478 (#1, Unknown)
2010-06-09 16:30:33.081 VDPAU Error: Failed to create VDPAU device.
2010-06-09 16:30:33.081 VDPAU Error: No VDPAU device
2010-06-09 16:30:33.081 Failed to create VDPAU render device.
2010-06-09 16:30:33.081 VidOutVDPAU Error: Failed to initialise VDPAU
2010-06-09 16:30:33.081 VideoOutput, Error: Not compiled with any useable video output method.
2010-06-09 16:30:33.081 NVP(1), Error: Couldn't create VideoOutput instance. Exiting..
2010-06-09 16:30:33.082 Unable to initialize video.
2010-06-09 16:30:53.092 playCtx, Error: StartPlaying() Failed to start player

```

Any ideas?
Thanks!
P

---

### Post by padukes on 2010-06-10
Hey all,

My problem was that /usr/lib/libvdpau_nvidia.so was pointing to the wrong lib.  I had to point it to /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.

I figured it out by running the following in the shell:

```
export VDPAU_NVIDIA_DEBUG=3
export VDPAU_TRACE=1

vdpauinfo

```

This printed out some extra error messages about /usr/lib/libvdpau_nvidia.so which caused me to check out the link.

Thanks!
P

---

### Post by thatsdaniel on 2010-07-18
You Sir, are awesome! Solved [my problem]("http://ubuntuforums.org/showthread.php?t=1473257") as well!
Thank ye! :D

```
sudo mv /usr/lib/[libvdpau_nvidia.so]("http://libvdpau_nvidia.so/") /usr/lib/libvdpau_nvidia.soOLD
sudo ln -s /usr/lib/nvidia-current/vdpau/[libvdpau_nvidia.so]("http://libvdpau_nvidia.so/") /usr/lib/[libvdpau_nvidia.so]("http://libvdpau_nvidia.so/")
```

---

