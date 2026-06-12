---
title: "Lag on 1080p Videos"
date: 2011-06-08
forum: Multimedia Software
---

### Post by zbanghy0ne on 2011-06-08
Hey guys. I'm kinda new to linux/ubuntu, and I got a problem.
When I try to watch 1080p videos on Youtube and more, it lags like hell. The video drivers are installed and my resolution is 1600x1200 pixels (the lag is the same on any res.)

My specifications: (old *** pc)
CPU: Intel P4 631 3.0GHZ
nVidia GeForce 8500GT
2 GB of RAM (DDRII)

Also, Ubuntu is kinda laggy when I try to move the windows.


I have to state that when running 1080p videos (online or not) on this pc with Widows XP/7 installed, it works great. No lag :)


Please help me solve this problem

---

### Post by Joe of loath on 2011-06-08
Your problem is your CPU; the Windows version of flash player supports offloading the processing to the GPU, but the Linux version does not (Although I believe it will soon). There fore your CPU has to do the decoding work, and it's really not up to the job.

---

### Post by lovinglinux on 2011-06-08
> **Joe of loath said:**
> Your problem is your CPU; the Windows version of flash player supports offloading the processing to the GPU, but the Linux version does not (Although I believe it will soon). There fore your CPU has to do the decoding work, and it's really not up to the job.

Although the CPU is indeed a problem (I had similar issues with P4 CPU), nVidia GForce 8 series can use vdpau to offload the video processing to the GPU, even with Flash.

To enable vdpau in flash, first install vdpau;

```
sudo apt-get install libvdpau1
```

Then install [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") and run the extension Wizard. It will detect vdpau and apply the necessary tweak to make it work. Additionally, it will also apply other tweaks, remove conflicting plugins and install the best plugin according to your system architecture and version.

> Note: this only works for 32bit users. 64bit users need to install the 32bit flash from the repositories with the 64bit wrapper, in other to use vdpau. This can be achieved from the Flash-Aid installation options.

You might also try my [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/") add-on, that allows to watch flash videos on some sites using a different plugin, like gecko-mediaplayer, which uses a lot less CPU.

---

