---
title: "Sound Card issues"
date: 2012-12-05
forum: Multimedia Software
---

### Post by ManAbradesStars on 2012-12-05
Hey, I'm a bit of a novice with linux in personal computing contexts, Most of my experience is with web servers, and I hardly have messed with hardware even in that area. I recently started setting up Mythbuntu to act as a DVR/Media Server in my home. I am not able to get sound to work on the box at all.

I have been following the steps here:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

From the output of lspci -v , here is my sound card:

```
07:04.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs X-Fi XtremeMusic
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at bce0 [size=32]
	Memory at cee00000 (64-bit, non-prefetchable) [size=2M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: snd_ctxfi
	Kernel modules: snd-ctxfi


```

the site that thread provides to locate the proper driver is not loading for me, so either my ISP is being dumb or that site is no longer up. I do think I was able to locate what driver i need from this site:

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

from that site it would seem that I need this driver:

emu20k1

When I run modprobe, I get
```
$ sudo modprobe snd-
FATAL: Module snd_ not found.
```

When I procced to running dpkg-reconfigure alsa-source the driver I believe I need is not listed. So, Sorry if im derping hard, but I'm unsure of how to proceed.

A couple other random pieces of information:

```
$ stat /dev/snd
  File: `/dev/snd'
  Size: 380       	Blocks: 0          IO Block: 4096   directory
Device: 5h/5d	Inode: 7446        Links: 3
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2012-12-05 01:19:25.928285999 -0600
Modify: 2012-12-05 01:18:22.305705192 -0600
Change: 2012-12-05 01:18:22.305705192 -0600
 Birth: -
$ uname -mrs
Linux 3.2.0-34-generic x86_64

```

Thank you all so much for any help you can provide!

---

