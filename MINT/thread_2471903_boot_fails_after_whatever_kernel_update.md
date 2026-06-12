---
title: "boot fails after whatever kernel update"
date: 2022-02-12
forum: MINT
---

### Post by priam92 on 2022-02-12
Hello,
I'm new on linux and don't hight capabilities!:)

I use Linux Mint 20.3 Cinnamon
AMD Ryzen 5 PRO 4650G with Radeon Graphics × 6
Advanced Micro Devices, Inc. [AMD/ATI] Renoir
5.4.0-99-generic

With this configuration, I have no hardware acceleration.
inxi -G
Graphics:
  Device-1: AMD Renoir driver: N/A 
  Display: x11 server: X.Org 1.20.13 driver: ati,fbdev 
  unloaded: modesetting,radeon,vesa resolution: 1920x1080~77Hz 
  OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6

So I decided to upgrade to a newer kernel (I have already successfully to it in the past with the same hardware).

During the kernel installation I have see some messages you could see in the screenshot (foto!):
  [IMG]https://ubuntuforums.org/attachment.php?attachmentid=290012&stc=1[/IMG]

When I reboot the PC with the new kernel, I have a black screen after grub menu.
So I don't know how to investigate further more to find out where is my problem.
Your help will be appreciated.
Regards

---

