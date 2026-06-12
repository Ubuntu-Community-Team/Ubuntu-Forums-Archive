---
title: "Undefined Video Mode Number 31e"
date: 2010-04-06
forum: Multimedia Software
---

### Post by joebrueske on 2010-04-06
I accidentally turned on Usplash when I was playing around with Xsplash. BIG difference. :P Now I'm getting an "Undefined Video Mode Number 31e" error after grub.

I searched and found that if you added "vga=xxx" to the menu.lst file, it should take care of it. So I put in 317. Nothing. Tried 0x0317, which by the way, here's my framebuffer
```
 sudo hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.jMhVbQzvL57
  Hardware Class: framebuffer
  Model: "ATI C24 "
  Vendor: "ATI Technologies Inc."
  Device: "C24 "
  SubVendor: "ATI MOBILITY RADEON X600   "
  SubDevice: 
  Revision: "01.00"
  Memory Size: 128 MB
  Memory Range: 0xc8000000-0xcfffffff (rw)
  Mode 0x0382: 320x200 (+320), 8 bits
  Mode 0x030d: 320x200 (+640), 15 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+960), 24 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0392: 320x240 (+320), 8 bits
  Mode 0x0393: 320x240 (+640), 15 bits
  Mode 0x0394: 320x240 (+640), 16 bits
  Mode 0x0395: 320x240 (+960), 24 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03a2: 400x300 (+400), 8 bits
  Mode 0x03a3: 400x300 (+800), 15 bits
  Mode 0x03a4: 400x300 (+800), 16 bits
  Mode 0x03a5: 400x300 (+1200), 24 bits
  Mode 0x03a6: 400x300 (+1600), 24 bits
  Mode 0x03b2: 512x384 (+512), 8 bits
  Mode 0x03b3: 512x384 (+1024), 15 bits
  Mode 0x03b4: 512x384 (+1024), 16 bits
  Mode 0x03b5: 512x384 (+1536), 24 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c2: 640x350 (+640), 8 bits
  Mode 0x03c3: 640x350 (+1280), 15 bits
  Mode 0x03c4: 640x350 (+1280), 16 bits
  Mode 0x03c5: 640x350 (+1920), 24 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0383: 640x400 (+1280), 15 bits
  Mode 0x0384: 640x400 (+1280), 16 bits
  Mode 0x0385: 640x400 (+1920), 24 bits
  Mode 0x0386: 640x400 (+2560), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+1920), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+2400), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+3072), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
```
And nothing with 0x0317. One person on a blog suggested "vga=normal." That didn't work.

The system launches fine with me manually entering 317, but you know, it's kind of annoying.

I also have a bunch of mounting code now come up right after it. Normally it just brings up a line or two about mount-all failing and checking so many blocks of data. It still does, but there's two screen of other crap that whiz by too fast to read. I'd rather just have a blank screen before Xsplash.

Any thoughts on what's wrong?

**EDIT**
The video mode WAS set incorrectly in the menu.lst file. But I never noticed that the VGA option was in a different line.
```
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=16d468b3-74ec-488b-a931-6e370fe75d6f ro vga=0x0317 splash 
```
It was set to 798. My guess is that when I installed a usplash theme it changed it. Now it's back to normal.

---

