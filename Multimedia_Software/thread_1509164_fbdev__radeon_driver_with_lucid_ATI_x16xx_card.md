---
title: "fbdev / radeon driver with lucid ATI x16xx card"
date: 2010-06-13
forum: Multimedia Software
---

### Post by petersk on 2010-06-13
I just upgraded to LTS, where my ATI x1650 stopped working (let alone supporting both monitors any more).  Regardless, to get the card to even work I had to edit etc/X11/xorg.conf with the fbdev driver.  I got kms to load (or at least it seems to be loaded):
```
dmesg | grep drm
[    0.000000] Linux version 2.6.32-22-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
[   17.408665] [drm] Initialized drm 1.1.0 20060810
[   17.674438] [drm] radeon kernel modesetting enabled.
[   17.716224] [drm] radeon: Initializing kernel modesetting.
[   17.719583] [drm] register mmio base: 0xBF800000
[   17.719589] [drm] register mmio size: 65536
[   17.721492] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[   17.721760] [drm] Generation 2 PCI interface, using max accessible memory
[   17.736164] [drm] radeon: VRAM 256M
[   17.736167] [drm] radeon: VRAM from 0x00000000 to 0x0FFFFFFF
[   17.736170] [drm] radeon: GTT 256M
[   17.736173] [drm] radeon: GTT from 0xC0000000 to 0xCFFFFFFF
[   17.736313] [drm] radeon: using MSI.
[   17.736360] [drm] radeon: irq initialized.
[   17.736369] [drm] Detected VRAM RAM=256M, BAR=256M
[   17.736372] [drm] RAM width 128bits DDR
[   17.738497] [drm] radeon: 256M of VRAM memory ready
[   17.738505] [drm] radeon: 256M of GTT memory ready.
[   17.738558] [drm] GART: num cpu pages 65536, num gpu pages 65536
[   17.740854] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[   17.741116] [drm] radeon: cp idle (0x10000C03)
[   17.741552] [drm] Loading R500 Microcode
[   17.791401] [drm] radeon: ring at 0x00000000C0000000
[   17.791441] [drm] ring test succeeded in 6 usecs
[   17.795621] [drm] radeon: ib pool ready.
[   19.792039] [drm] ib test succeeded in 0 usecs
[   19.792263] [drm] Default TV standard: NTSC
[   19.792364] [drm] Radeon Display Connectors
[   19.792367] [drm] Connector 0:
[   19.792370] [drm]   VGA
[   19.792373] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   19.792376] [drm]   Encoders:
[   19.792379] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   19.792381] [drm] Connector 1:
[   19.792383] [drm]   S-video
[   19.792385] [drm]   Encoders:
[   19.792387] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   19.792390] [drm] Connector 2:
[   19.792392] [drm]   DVI-I
[   19.792394] [drm]   HPD1
[   19.792397] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   19.792400] [drm]   Encoders:
[   19.792402] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   19.792404] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[   20.178561] [drm] fb mappable at 0xE0080000
[   20.178566] [drm] vram apper at 0xE0000000
[   20.178569] [drm] size 5242880
[   20.178571] [drm] fb depth is 24
[   20.178574] [drm]    pitch is 5120
[   20.197072] fb0: radeondrmfb frame buffer device
[   20.197091] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
```

Anyone have any ideas on how to load the FOSS driver for ATI? NOTE: I've given up on the proprietary drivers since ATI dropped support for my card back at Koala.

Kurt

---

### Post by Mark Phelps on 2010-06-14
I, too, have an x1650 card, installed Lucid 32-bit -- and the card works "out of the box" with no changes needed or xorg file, either.

Try renaming the xorg.conf file and rebooting.  Ubuntu should automatically load and install the open source drivers.

If that doesn't work, read through the details on the link below about removing the fglrx stuff.  Perhaps there's still some stuff lying around:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by petersk on 2010-06-14
can you send the contents of your xorg.conf file?

---

### Post by Mark Phelps on 2010-06-17
> **petersk said:**
> can you send the contents of your xorg.conf file?

NO -- because I don't have one.  I allowed the video to default and it works fine without such a file.

---

### Post by petersk on 2010-07-01
Well, I followed the purge instructions and also removed my /etc/X11/xorg.conf, and all I got was a frozen machine with vertical lines on each monitor.  

Do you or anyone else have any other suggestions on how "better" purge the old drivers and use two monitors?
Kurt

---

### Post by petersk on 2010-07-18
Anyone have any ideas how to purge the old ATI drivers? See the above problem?

---

