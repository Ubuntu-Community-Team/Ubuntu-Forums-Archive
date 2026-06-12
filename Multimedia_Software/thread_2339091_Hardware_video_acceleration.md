---
title: "Hardware video acceleration"
date: 2016-10-04
forum: Multimedia Software
---

### Post by declan.marks on 2016-10-04
I have just installed Ubuntu 16.04 and I am trying to play video in vlc. The playback is very choppy and I have found out that hardware acceleration is not working. Mainly because other players are working.

My graphics card is AMD R7 240 and is there a way to setup hardware acceleration. Also does this card support the new AMDGPU driver.

---

### Post by monkeybrain20122 on 2016-10-05
If you use the open source driver you need to install the package mesa-vdpau-drivers and set vlc to use vdpau (Tools > Preferences > Input codecs and choose vdpau for hardware acceleration decoding) 

```
sudo apt-get install mesa-vdpau-drivers vdpauinfo
```

You need to reboot. Afterwards, open the terminal and type vdpauinfo to check if vdpau is enabled.

---

### Post by King Crimson on 2016-10-08
I also had extremely choppy playback after installing VLC on Xubuntu 16.04.1 LTS (Xenial Xerus) with the default open source driver (my card: Radeon HD6850), especially with mp4 files, the solution suggested by **monkeybrain20122** did not help at all, however. But I found another one. Should the VDPAU drivers not solve your issue, either, try this:

```
sudo apt-get install gstreamer1.0-vaapi
```

Then, in VLC, go to Tools -> Preferences -> Input/Codecs and select "VA-API video decoder via X11" for Hardware-accelerated decoding. For me, this made playback butter-smooth, and CPU load went down from 20% to 7-9%. :D

Regards,
Marek

---

### Post by Yellow Pasque on 2016-10-08
VLC is not a gstreamer program, so installing that package for VLC doesn't really make sense. It may have pulled in a dependency. Check to see what vaapi driver you're using with vainfo:
```
sudo apt-get install vainfo
vainfo
```

---

### Post by King Crimson on 2016-10-09
That's the output I get:

king@msi:~$ vainfo
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/r600_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

---

### Post by monkeybrain20122 on 2016-10-09
I don't know what the properietary AMD driver uses for hardware acceleration (still VAAPI?), but the open driver uses VDPAU. I think only Intel uses VAAPI now.

---

### Post by King Crimson on 2016-10-10
As I've written above, I don't use the proprietary AMD driver, but the standard open-source driver built into Xubuntu 16.04.1, and VDPAU doesn't solve the problem at all, the playback is as choppy as without it. In my case, only VAAPI solves the problem.

---

### Post by Yellow Pasque on 2016-10-10
> **King Crimson said:**
> In my case, only VAAPI solves the problem.

Which is odd because your vainfo output shows that you have no working VAAPI. I suspect VLC is falling back on something else. Maybe run it from the terminal and take a look at the log. If you want VAAPI to actually work with open source radeon driver, you need the mesa-va-drivers package.

> I think only Intel uses VAAPI now.

The open source radeon and nvidia ("nouveau") also support it if mesa-va-drivers package is installed. To make things more confusing, you can even use VAAPI with a VDPAU backend (vdpau-va-driver package).

---

### Post by monkeybrain20122 on 2016-10-10
> **Temüjin said:**
> 
The open source radeon and nvidia ("nouveau") also support it if mesa-va-drivers package is installed. To make things more confusing, you can even use VAAPI with a VDPAU backend (vdpau-va-driver package).

Yes, I used vdpau-va-driver for mplayer on an intel machine back in the 14.04 days. It is actually a vdpau wrapper for vaapi (by the same guy who created the freshplayer plugin). Now I use mpv instead of mplayer which can use vaapi directly so I don't need it anymore. I think mesa-va-driver is a vaapi wrapper for vdpau, but I  don't really see the use of it since all players as far as I know that support vaapi would support vdpau anyway (maybe vlc in the old days, there was a time when it worked only with vaapi but not vdpau a few years ago)

---

### Post by monkeybrain20122 on 2016-10-10
> **King Crimson said:**
> As I've written above, I don't use the proprietary AMD driver, but the standard open-source driver built into Xubuntu 16.04.1, and VDPAU doesn't solve the problem at all, the playback is as choppy as without it. In my case, only VAAPI solves the problem.

It makes no sense since you have no vaapi driver according to your vainfo output. Maybe vlc is using software decoding (check how much cpu you are using with the top command) It is possible that your machine is capable enough that you don't need hardware acceleration for smooth playback, but because of some graphic driver issue (or vlc issue) attempt to use hd acceleration via vdpau actually results in poorer performance.

---

### Post by Yellow Pasque on 2016-10-10
> **monkeybrain20122 said:**
> It is actually a vdpau wrapper for vaapi (by the same guy who created the freshplayer plugin).

What you are thinking of is this backend to libvdpau, which is found in the libvdpau-va-gl1 package (and is written by the main freshplayer dev):
[https://github.com/i-rinat/libvdpau-va-gl](https://github.com/i-rinat/libvdpau-va-gl)

Gwenolé Beauchesne wrote the VDPAU backend for libva when he worked for Splitted Desktop Systems (before he moved to Intel to work on libva itself) and was focused on video accel support for the binary drivers. That is what is found in the vdpau-va-driver package:
[http://www.phoronix.com/scan.php?page=article&item=xorg_vdpau_vaapi&num=1](http://www.phoronix.com/scan.php?page=article&item=xorg_vdpau_vaapi&num=1)


> I think mesa-va-driver is a vaapi wrapper for vdpau

No, it's a separate state tracker in galliumd3D:
[https://cgit.freedesktop.org/mesa/mesa/tree/src/gallium/state_trackers/va](https://cgit.freedesktop.org/mesa/mesa/tree/src/gallium/state_trackers/va)
[https://cgit.freedesktop.org/mesa/mesa/tree/src/gallium/state_trackers/vdpau](https://cgit.freedesktop.org/mesa/mesa/tree/src/gallium/state_trackers/vdpau)

---

### Post by King Crimson on 2016-10-10
> **Temüjin said:**
> Which is odd because your vainfo output shows that you have no working VAAPI. I suspect VLC is falling back on something else. Maybe run it from the terminal and take a look at the log. If you want VAAPI to actually work with open source radeon driver, you need the mesa-va-drivers package.

Ok, let's see. After starting VLC from the terminal, I get the following:

1. Right after installing VLC on a freshly installed Xubuntu (I had to do a reinstall anyway), without changing its default config or adding any additional codecs:
avcodec decoder: **Using G3DVL VDPAU Driver Shared Library version 1.0 for hardware decoding.**
=> MP4 video playback is extremely choppy, like a slide show (audio is ok), high CPU load (~20%)

2. After installing mesa-va-drivers and choosing "VA-API video decoder via X11" in Input & Codecs Settings > Hardware-accelerated decoding:
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/r600_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
avcodec decoder: **Using mesa gallium vaapi for hardware decoding.**
=> No video at all (black window), audio is ok.

3. After removing mesa-va-drivers and installing gstreamer1.0-vaapi (apt-get then also automatically installs libva-wayland1 as an additional package):
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/r600_drv_video.so
libva info: va_openDriver() returns -1
[00007f70400021f8] **vaapi_x11 generic error: Failed to initialize the VAAPI device**
=> Perfect, smooth video & audio (which was not the case before installing gstreamer1.0-vaapi), CPU load 3-9%. But ONLY if "VA-API video decoder via X11" remains selected in Input & Codecs Settings > Hardware-accelerated decoding, when I switch to "Automatic" or "VDPAU video decoder", stuttering and high CPU load are right back.

Ain't that funny? Well, I guess as long as it works, I'm not gonna complain because of some error messages...

---

