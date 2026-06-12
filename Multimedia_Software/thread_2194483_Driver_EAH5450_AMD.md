---
title: "Driver EAH5450 AMD"
date: 2013-12-18
forum: Multimedia Software
---

### Post by magicman1223 on 2013-12-18
I just started playing minecraft yesterday and noticed i was getting a frame rate of 2 -5 fps, the game stuttered and was just aweful. Looking into it I believe its because I am using my integrated graphics instead of the graphics card. I realize this card is not high end but figured it should be better then what I am getting now. The system has  8GB memory , AMD A10-5800K APU with Radeon(tm) HD Graphics × 4 . The Graphics shows Gallium 0.4 on AMD CEDAR.  I tried to use the proprietary drivers from "software and updates" The first time i used "using video driver fro the amd graphics accelerators from fglrx-updates (proprietary) However doing that led to the system using VESA:CEDAR and i keep getting > the selected configuration for displays could not be applied required virtual size does not fit available size when trying to set up my dual monitors. Then I tried "just the fglrx (not the -updates) and then received error in the lower right hand corner saying unsupported hardware ,  my dual monitor configuration also was not working with that driver as well. I have also disabled integrated graphics in bios so i dont understand how it continues to use it. I am a bit of a noob when it comes to graphics on Linux so if i misspoke please correct me. Below is some info that might help. Any suggestions on whats going on? 

```
~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD CEDAR
OpenGL version string:  3.0 Mesa 9.1.3


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes



```

```
$ sudo lshw -C video
[sudo] password for user2: 
  *-display               
       description: VGA compatible controller
       product: Cedar [Radeon HD 5000/6000/7350 Series]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:54 memory:c0000000-cfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:fea00000-fea1ffff
```

---

