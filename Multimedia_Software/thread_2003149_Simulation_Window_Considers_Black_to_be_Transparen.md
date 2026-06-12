---
title: "Simulation Window Considers Black to be Transparent"
date: 2012-06-13
forum: Multimedia Software
---

### Post by zeratul22 on 2012-06-13
I have been using a simulation software called AtomEye ([http://li.mit.edu/Archive/Graphics/A/](http://li.mit.edu/Archive/Graphics/A/)) to visualize some atomic configurations. I have been using it on an old laptop running Ubuntu 10.04 and it has worked fine from the beginning. I installed Ubuntu 12.04 on a newer desktop computer, and it has had transparency issues (see attached images). White is ok, but anything not white is taken as transparent.

Atoms can be colored according to relative RGB values, ie 111 = white, 000=black (should be). It turns out, 111 does show up white, but 000 shows up completely transparent and 100 shows up as a transparent red, etc.

I thought it might be an issue with Ubuntu 12, so I installed 10.04 on my desktop as well, with the same issue. I therefore conclude it must be a hardware issue, but I have no idea how to fix it.

It could be a video card issue. On the working computer, I have a GeForce Go 6600:

[COLOR="DarkOrange"]sudo lshw -c video

  *-display               
       description: VGA compatible controller
       product: NV43 [GeForce Go 6600]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:c0000000-cfffffff(prefetchable) memory:fc000000-fcffffff memory:fe9e0000-fe9fffff(prefetchable)[/COLOR]

But on the non-working desktop, I have Intel integrated chipset:

[COLOR="DarkOrange"]sudo lshw -c video

[sudo] password for mike: 
  *-display               
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:fe400000-fe7fffff memory:d0000000-dfffffff ioport:ec00(size=8 )[/COLOR]


One of the techies I know suggested it could be a problem with openGL. Here are the results of a relevant (I think) command that I found online:

For the working computer:

[COLOR="DarkOrange"]glxinfo | grep -i opengl

OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:[/COLOR]

For the non-working desktop:

[COLOR="DarkOrange"]glxinfo | grep -i opengl

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) G41 x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 8.1-devel
OpenGL shading language version string: 1.20
OpenGL extensions:[/COLOR]

Any ideas???
Thanks in advance!

---

### Post by ssds2004 on 2012-07-16
export XLIB_SKIP_ARGB_VISUALS=1 in the ~/.bashrc may fix the probem. Good Luck!

---

### Post by zenmasterfu on 2013-01-15
> **ssds2004 said:**
> export XLIB_SKIP_ARGB_VISUALS=1 in the ~/.bashrc may fix the probem. Good Luck!

Perfect solution. I'll email this message to Ju Li and hopefully it can be added in the atomeye readme or whatever.

---

