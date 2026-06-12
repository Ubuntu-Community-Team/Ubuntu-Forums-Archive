---
title: "Totem flips video vertically"
date: 2011-11-22
forum: Multimedia Software
---

### Post by vancouverite on 2011-11-22
Hi all,
Strange problem: Playing videos in totem results in an upside down image!  I have some avi videos that are 24-bit RGB and totem plays them upside down.

The attached image shows a screen shot: on the left is totem, on the right VLC.  Notice the numbers in the color bar are upside down.

VLC plays them correctly, but cannot play all of the videos.  They are at a variety of resolutions and the ones at the highest resolution will not play in VLC (otherwise I would just use VLC).  VLC gives the error

[INDENT]Your video output acceleration driver does not support the required resolution: 1897x1225 pixels. The maximum supported resolution is 1898x1225.
Video output acceleration will be disabled. However, rendering videos with overly large resolution may cause severe performance degration.[/INDENT]

Has anybody seen this before?  What could be going on?

Cheers.

Ubuntu 11.10 - Linux 3.0.0-13-generic x86_64 GNU/Linux
Totem 3.0.1
VLC 1.1.12
x64codecs
gstreamer 0.10
libavcodec-extra-53 4:0.7.2
ubuntu-restricted-extras 56
nvidia-current 280.13

$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: G92 [GeForce GTS 240]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ec00(size=128) memory:fbee0000-fbefffff

---

