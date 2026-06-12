---
title: "xvinfo: no adaptors present"
date: 2015-06-17
forum: Multimedia Software
---

### Post by Ogashi on 2015-06-17
Hi all
I'm using Ubuntu 15.04 in a HP laptop with an AMD Radeon HD 8650G using fgrlx. The other day I was going to play a PS1 game (which I own) using pcsxr (the XVideo Driver 1.1.17) , when I found that loading the ISO exits immediately. When I run the emulator via console, I get the following message before exiting: "RGB or YUV not available for this adapter. See xvinfo. Quitting." So I run xvinfo in the console and I get X-Video Extension version 2.2, screen #0, no adaptors present. The thing is that I was able to play before in 14.10, and I'm still capable of playing if I select the OpenGL Driver 1.1.78, but the usage of CPU is too high. Any help would be much appreciated. Here's some info:

lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8650G]

lshw -numeric -class video
*-display               
       description: VGA compatible controller
       product: Richland [Radeon HD 8650G] [1002:990B]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI] [1002]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:39 memory:e0000000-efffffff ioport:3000(size=256) memory:f0400000-f043ffff

---

### Post by Yellow Pasque on 2015-06-18
It's an old thread, but you may find some relevant info here: [http://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/amd-linux/4822-opengloverlay-vs-xvideo-which-one-is-better](http://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/amd-linux/4822-opengloverlay-vs-xvideo-which-one-is-better)

You can try this:
```
sudo amdconfig --overlay-type=Xv
```

If it doesn't work, delete the xorg.conf and generate a new one.
```
sudo rm /etc/X11/xorg.conf
sudo amdconfig --initial -f
```

---

### Post by Ogashi on 2015-06-19
Hi Temujin, thanks for your reply. I've tried your suggestions with no luck. I have also noticed that in aticonfig --help, under screen related options, for overlay only gives the option "opengl" or "disable". Any ideas?
EDIT: I'm finding some concerning things in Xorg.0.log:
[    36.444] (II) Module amdxmm: vendor="X.Org Foundation"
[    36.444]     compiled for 1.4.99.906, module version = 2.0.0
[    36.445] (EE) fglrx(0): XMM failed to initialize
[    36.445] (WW) fglrx(0): No XV video playback available

[    37.720] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    37.720] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[    37.720] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]

---

### Post by Yellow Pasque on 2015-06-19
```
I have also noticed that in aticonfig --help, under screen related options, for overlay only gives the option "opengl" or "disable". Any ideas?
```
Maybe AMD stopped supporting xv?

---

### Post by Ogashi on 2015-06-21
Ok, so now I've tried to switch to the open source drivers. I can boot, but the performance is terribly low, my graphics info shows Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits). I know that is some kind of low graphics mode because something is going wrong, I have installed Fedora in a different partition and the open source drivers work fine. Any ideas?
EDIT: After checking the Xorg.log I found it was still trying to load the frglx driver instead the open source ones. I run sudo apt-get autoremove to remove the frglx driver and now loads the open source drivers and I can use my psx emulator. Hope it helps someone.

---

### Post by jtniehof on 2015-08-04
I'm having the same problem, no Xv support after upgrade to vivid, Radeon 7750 (R7 250E, Cape Verde). I did try installing xvba-va-driver, since I saw VLC was looking for fglrx_drv_video.so, but that didn't help the Xv situation. It would seem odd if ATI stopped supporting Xv in total (since xvba-va-driver only works with fglrx), but I have found the fglrx driver tends to drop full support for older cards rather aggressively.

---

