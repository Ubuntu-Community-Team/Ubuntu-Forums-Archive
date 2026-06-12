---
title: "kernel update causes nvidia display to break"
date: 2012-09-25
forum: Multimedia Software
---

### Post by Docaltmed on 2012-09-25
kernel 3.2.0-31-generic came down the pipeline the other day (12.04 LTS), and I upgraded it as part of the normal process. After that, the wheels came off.

I could no longer get either a login screen, a grub menu, or anything except the stupid "Out of range" error message, a problem I had dealt with ages ago by updating grub with the right resolution.

Booting off a live USB proved to be a bozo no-no as well. As soon as I clicked on "try Ubuntu" the screen disintegrated into a morass of confused pixels, making a totally unreadable, unusable mess.

I finally figured out how to get into Ubuntu from the Live USB (ProTip: nomodeset), and reconfigured grub about 6 times with no change in results. Finally, I had the grub repair utility completely purge grub and reinstall it.

What I got from there was at least a grub menu, where I could pick my kernel. When I tried the latest kernel, however, I got booted directly to the console. From there, I added x-swat ppa, and installed Nvidia driver 295.49. After that, I could boot successfully into Ubuntu using the older kernel, 3.2.0-30-generic, and my display works just fine, at least in Ubuntu 2D. However, when I try kernel 3.2.0-31, I get spewed into the console.

BTW, my graphics card is the GeForce 7025/nForce 630a.

Does anybody have a *clue* as to what's going on here? I sure don't.

---

### Post by BicyclerBoy on 2012-09-25
The nVidia driver does not load if you use "nomodeset".
You would end up with VESA or nouveau
Check the /var/log/Xorg.0.log file..

You have a PCI express x16 slot on the mobo ? Why not get an upgrade to a cheap VDPAU GPU like 240/440/630 ?

The nForce 730 & ION were the 1st mobo graphics of merit..

Reboot into the problem kernel:
The kernel log or cmd "dmesg" could help debug the kernel problem.

---

### Post by Docaltmed on 2012-09-27
I think I may have to get a graphics card to plug in. I'm not sure I want to stick with Nvidia, though.

I'm beginning to suspect there is something hinky in the way the graphics is implemented on the motherboard. This is not the first kind of odd problem that I'm having that it would seem that nobody else in the universe is having. And I'm using a no-name mobo from Tiger Direct.

---

### Post by BicyclerBoy on 2012-09-27
When you start have to replace bits of a PC, sometimes better just to start fresh, a new PSU is always a good start.

nVidia h/w & driver is the only out-of-the-box solution that works as well as on windows.
And the open source nouveau is functional.

The intel driver (sandy/ivy) is shaping up to be a good option & is open source.
The intel h/w is undeniably king of performance (CPU) & power efficiency.

---

