---
title: "Problen upgrading Nvidia"
date: 2010-07-24
forum: Multimedia Software
---

### Post by unconcrete on 2010-07-24
Hi all,
I've recently installed Lucid Linx and all works well until the os asked me if I'd like to upgrade my Nvidia geforce gtx 260. I've followed the suggestion to make possible to use Compiz Fusion and Emerald themes. 
It was an unleasant choice since at reboot I've run Ubuntu 10.04 lts and I had only a black dead monitor.
What happened? I was forced to reboot by dvd and uninstall the upgrade.
I'd like to know how to upgrade my current video card without risks.
This is the first tim i try to edit Xorg.conf, but in the new ubuntu i can't find it. Once it was in the /x11/ dir but now if i search a file called Xorg/xorg.conf i obtain only some packages mainly in /share/docs/. Where is Xorg? Synaptic reports it is installed but i don't find it. Hav i to create a new Xorg.conf by hand? And if yes, where have i to put it?
Please help. 
At least I'll find useful a guide to install a proper driver for Geforce GTX 260.

thanks in advance,

unconcrete

---

### Post by GeoPirate on 2010-07-31
Sounds like you tried to do everything at once. Try installing the driver and rebooting before you mess with compiz at all.  This way you can see if it's a compiz problem or a driver problem.

---

### Post by unconcrete on 2010-08-01
> **GeoPirate said:**
> Sounds like you tried to do everything at once. Try installing the driver and rebooting before you mess with compiz at all.  This way you can see if it's a compiz problem or a driver problem.
You are right. First of all, the geforce must be installed. Anyway I don't understand why xorg.conf is lost. Maybe lucid lynx can work without it?
If no, how have I do to install a xorg.conf for my Geforce gtx 260?
Anyway I'd like to avoid jockey-gtk since the automatic driver installation have caused a black screen at reboot > grub > ubuntu.
A strange thing is that ubuntu recognizes my video card is a nvidia but 3d games and or graphic effects don't work.
[djangou@ESPERYDES:~$ sudo hwinfo --framebuffer
[sudo] password for djangou: 
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.tvl4Tad3xF8
  Hardware Class: framebuffer
  Model: "NVIDIA GT200 Board - 0651s009"
  Vendor: "NVIDIA Corporation"
  Device: "GT200 Board - 0651s009"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xf9000000-0xf9dfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037b: 1280x720 (+5120), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
]
Thanks a lot
unconcrete

---

