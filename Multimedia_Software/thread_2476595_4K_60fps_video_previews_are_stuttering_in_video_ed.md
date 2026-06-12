---
title: "4K 60fps video previews are stuttering in video editing softwares"
date: 2022-06-30
forum: Multimedia Software
---

### Post by jeffbond on 2022-06-30
Hi,

I have created mp4 files with a drone. I set the quality output to 4K 60 frames per second.

I can playback any of my videos using mpv video player and my hardware is adequate :

- Graphics:  Mesa Intel® Xe Graphics (TGL GT2) / Mesa Intel® Xe Graphics (TGL GT2)
- CPU: 11th Gen Intel® Core™ i7-1165G7 @ 2.80GHz × 8
- RAM: 32 GiB
- OS : Ubuntu 22.04

The problem is that after I import my videos in a video editor such as KDenlive, OpenShot, ..., the preview in the editor is  stuttering to the extreme.

What software would you recommend? Do I experience this prb because the editors I have picked don't support 60fps or h265 encoding?

Thank you

---

### Post by TheFu on 2022-06-30
Get a GPU that has native support for 8k encoding?  I've found that onboard iGPUs from Intel are find for decoding video, but not for editing video.  It is amazing how much better even an AMD iGPU built into a Ryzen 5600G is compared to the iGPU in a Core i5.  Expect to spend $300+ on the GPU.

Look at AMD's new RDNA 3-based GPUs to get 
> AMD's VCN 4.0 engine appears to support H.264/MPEG 4 AVC, H.265, VP9, AV1, and JPEG decoding, as well as AV1, H.264, and H.265 encoding. For now, VCN does not appear to support H.266/VVC (versatile video coding) decoding/encoding.
[https://www.tomshardware.com/news/next-amd-video-engine-may-lack-av1](https://www.tomshardware.com/news/next-amd-video-engine-may-lack-av1)
Of course, it will be months before the AMD GPU drivers are available in the kernel and you'll need the HWE kernel of 22.04 AFTER that becomes available.

Perhaps there are older GPUs that will work too?  I have a low-end nVidia GPU GT 1030 and it doesn't support encoding in hardware.  After using both nvidia and AMD for many years, I have to say at the mid-tier, I much prefer the AMD drivers for Linux over whatever mess nVidia does.  Had a graphics driver lock up earlier today on the 1030 system. I was able to recover from a locked screen using another system to selectively kill processes, but I suspect most users would have assumed the entire box was locked up and use the BRS reboot method.  After killing a file manager, the GUI started working again.  A file manager!

---

### Post by jeffbond on 2022-07-02
Thanks. Do you think an RTX 3060 external GPU would be well supported in 22.04?

---

### Post by Autodave on 2022-07-02
The RTX 3060 is well supported.  However, if you could spend a few more dollars, the RTX 3070 would be a much better choice.  Actually, the older RTX 2070 would be a better option than the RTX 3060.

---

### Post by TheFu on 2022-07-02
If it were me, I'd avoid nVidia.  I say this after using recent nvidia and amd GPU drivers.  With AMD, the drivers just work.

I suppose if you need 3090-class performance, then nvidia is the current leader and only choice, but in the mid-range, AMD drivers are just so much easier once they are part of a supported kernel.

Part of our duty is to support companies who provide the best support for Linux. That isn't nVidia.

---

### Post by jeffbond on 2022-07-02
> **Autodave said:**
> The RTX 3060 is well supported.  However, if you could spend a few more dollars, the RTX 3070 would be a much better choice.  Actually, the older RTX 2070 would be a better option than the RTX 3060.

So these are supported in Ubuntu 22.04, great!  And more specifically,  are they supported as en external GPU (connected via thunderbolt) and in  Davinci Resolve video editor?

> **TheFu said:**
> 
If it were me, I'd avoid nVidia.  I say this after using recent nvidia and amd GPU drivers.  With AMD, the drivers just work.


mid range would work I suppose. Do you know of an AMD GPU that is  already in the kernel and would be supported as an external GPU in  Davinci Resolve?

Thanks guys

---

### Post by TheFu on 2022-07-02
> **jeffbond said:**
>  mid range would work I suppose. Do you know of an AMD GPU that is  already in the kernel and would be supported as an external GPU in  Davinci Resolve?

If it were me, I'd ask Davinci Resolve gurus, being clear on your price range for the GPU.  I've heard of it, but never used it. Because it is proprietary, it is unlikely I'll ever use it.

Which kernel?  You've never said which OS version you are running and while you can use almost any kernel that you like, based on the question, I suspect you aren't one to go outside the defaults much.  Using myself as an example, I'm still using 18.04 with the HWE 5.4.x kernels. That limits the supported GPUs. In my AMD Ryzen 5600G system, a 5.10+ kernel was needed to get beyond basic video support, so I'm running a kernel newer than that even with 18.04 as the OS.

A few systems here will be moved from 18.04 to 20.04 this year, but I'm not really contemplating moving to 22.04 anything in 2022.  Stability is more important than "new" to me and I don't think all the major issues in 22.04 that impact me will be solved this year.

---

### Post by jeffbond on 2022-07-03
I am running 5.15.0-40-generic, GNOME 42.2, Wayland

I bought a new laptop a few months ago, it was running Windows 10. I wanted a Linux distribution and went for Ubuntu 20.04 LTS for stability. Unfortunately my WiFi adapter wasn't supported. Installing 21.10 fixed that problem. I just updated to 22.04 to get the latest LTS after all the nagging popups.

I have asked DaVinci Resolve's team about the card support but I am also obviously considering Ubuntu support and how easy (or not) it is to set up an eGPU.

---

### Post by TheFu on 2022-07-03
Please realize that nobody here works for Canonical, not even the moderators.

Wayland doesn't play nice with nVidia. The 22.04 release backed out using Wayland if an nvidia GPU is seen.  Be certain to read the release notes for the release.  If an eGPU is an external GPU, I don't think those work well enough to be considered at this point, for the goal you have.

---

