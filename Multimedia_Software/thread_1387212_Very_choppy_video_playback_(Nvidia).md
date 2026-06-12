---
title: "Very choppy video playback (Nvidia)"
date: 2010-01-21
forum: Multimedia Software
---

### Post by JG234 on 2010-01-21
Currently using **NVIDIA accelerated graphics driver (version 185)** and a Nvidia 8800GT. CPU is an Intel C2D E6600, so it's quite a fast PC.

Video playback is extremely choppy to the point of being unwatchable. It affects all applications that I have tried, such as VLC, Movie Player and flash videos in Mozilla Firefox. Videos on Youtube seem slow but playable, but when I try to watch them in full screen there's a drop to about 5FPS. CPU usage reaches 100%. 

Scrolling is also slow on large web pages. 

Disabling Compiz makes no visible difference. Before I installed Nvidia's driver, videos played perfectly...

Videos play fine in Windows XP.

It seems as if Nvidia's driver is using the CPU to 'process' videos, instead of the graphics card. Other than that, Ubuntu 9.10 is lightning fast... so what's going on here? I would really appreciate some help here! Is there some kind of codec pack I need? Thanks guys.

_______________________

Edit: I have resolved _one_ issue, that is flash player's performance in Firefox. Followed instructions [[here]](http://www.reddit.com/r/linux/comments/8f8l3/flash_problems_in_ubuntu_904/c093vw2) and Youtube is now smooth in full screen.

Other videos, however, are still stuttering and spiking CPU usage. This must be a widespread issue, but the lack of information on the web shows otherwise. There must be a fix out there somewhere...

---

### Post by JG234 on 2010-02-01
Sorted it out.

Copied this from NvNews forums:

> 
The 8800GT was running with a 1x PCI-E link width, it should have been @ 16x. And it was all down to my motherboard. All I had to do was update the motherboard's BIOS and now it's flying. Previous BIOS was from early 2006, 1.5 years before the 8800GT was released, explaining the incompatibility.


Quote:
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 GT (G92) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.92.16.00.04
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU  

And the Nvidia drivers seem to be working great, no annoying hacks or tweaks needed. I can't fault them. 

Hope this will help someone else another time. It's best to update your motherboard's BIOS regularly, then you won't run into problems like I have.

---

