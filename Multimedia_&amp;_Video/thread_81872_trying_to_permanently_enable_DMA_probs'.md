---
title: "trying to permanently enable DMA probs'"
date: 2005-10-25
forum: Multimedia &amp; Video
---

### Post by blastradius on 2005-10-25
Following the Ubuntu.com/DMA guide (which worked with Hoary) i've hit problems.   I'm configuring a fresh install of Breezy.

My hdparm settings look like this:-

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

The guide seems ok until i follow the troubleshooting bit which tells me to add 'amd74xx' above the line 'ide-cd' in /etc/modules.  Thing is, i don't have an ide-cd line.  MY /etc/modules looks like this:-

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
fglrx

I guess it's a Breezy thing.

Please help if you can

Thanks in advance

Eric

---

