---
title: "DVD playback choppy"
date: 2008-11-10
forum: Multimedia Software
---

### Post by jtdelasalas on 2008-11-10
I recently installed Ubuntu 8.10 and encountered only one issue.  I'm unable to play a DVD without it being choppy/the player draining system resources.  I was wondering if anyone else had this problem and if there is some sort of fix.

---

### Post by cybergalvez on 2008-11-10
> **jtdelasalas said:**
> I recently installed Ubuntu 8.10 and encountered only one issue.  I'm unable to play a DVD without it being choppy/the player draining system resources.  I was wondering if anyone else had this problem and if there is some sort of fix.

Does it look like this:
[http://ubuntuforums.org/showthread.php?t=977165](http://ubuntuforums.org/showthread.php?t=977165)

If so I'm looking for an answer too
Jose

---

### Post by jtdelasalas on 2008-11-10
It's not scrambled.  It's just choppy as if the video is eating up all system resources, I don't understand why.  This didn't happen until my transition to 8.10.

---

### Post by DrMega on 2008-11-10
What video player software are you using? Are you using Totem (appears as Movie Player in the "Sound and Video" menu of a default setup)?

If so, what I always do on a new install is replace the default Totem-GStreamer with Totem-xine. The Xine version seems to use less resources and seems happier to use your video hardware rather than making your CPU do lots of work.

---

### Post by jtdelasalas on 2008-11-10
I tried the Totem-Xine method.  For a while it wasn't choppy.  It started up again.  I doubt it is a hardware issue as installing Ubuntu still happened in a flash.  A few days ago I did the upgrade via synaptic.  That's when everything started to become choppy.  I thoght a fresh install of 8.10 would cure it, DVD playback is still choppy.

---

### Post by jtdelasalas on 2008-11-11
So I heard that I may have to enable DMA as a possible solution. How do I go about this?

---

### Post by DrMega on 2008-11-11
> **jtdelasalas said:**
> So I heard that I may have to enable DMA as a possible solution. How do I go about this?

DMA should be enabled by default, but I don't know how to check (someone here will know).

You haven't inadvertantly enabled XGL desktop have you? I did once and lost all my hardware rendering (I think it is there as an option to allow GL apps to work with hardware that doesn't support GL directly.

Also, What is the output of this command:

```

glxinfo | grep rendering

```

---

### Post by jtdelasalas on 2008-11-11
I don't know if I did or not.  How would I of enabled it?

I ran glxinfo | grep rendering

It shot out:  direct rendering:yes

---

### Post by DrMega on 2008-11-11
> **jtdelasalas said:**
> I don't know if I did or not.  How would I of enabled it?

I ran glxinfo | grep rendering

It shot out:  direct rendering:yes

Ok. That indicates that your system knows it can get the graphics card to do much of the work, so I'm kind of at a loss now as to why you'd get the issues you describe.

Just out of curiosity, what is your hardware spec?

---

### Post by jtdelasalas on 2008-11-11
I have an HP dv2410us.  It has a 2 Ghz processor and 2 gigs of RAM.  Like I said before I haven't really had any problems with it until recently when I first upgraded to 8.10 then did a fresh install with 8.10.

How could I disable XGL to see if that is causing my problem?

---

### Post by DrMega on 2008-11-11
> **jtdelasalas said:**
> 

How could I disable XGL to see if that is causing my problem?

When I accidentally did it, I had to find the package xgl-desktop (or something like that) and uninstall it. You don't need to worry about that though, because the fact that your direct rendering is enabled indicates that you haven't enabled the xgl desktop.

---

### Post by psyke83 on 2008-11-11
> **jtdelasalas said:**
> I recently installed Ubuntu 8.10 and encountered only one issue.  I'm unable to play a DVD without it being choppy/the player draining system resources.  I was wondering if anyone else had this problem and if there is some sort of fix.

There are three basic avenues you should investigate:
1. Graphics card drivers (unlikely): if you have ATI or NVIDIA graphics, ensure you are using the proprietary drivers. The free drivers don't usually have problems, though at the very least be sure you're not using the VESA driver.

2. DMA settings (likely): ensure your drives are using DMA correctly. Due to the way libata works, hdparm can no longer read or set DMA modes correctly. Check your dmesg log for warnings:

```
$ dmesg | grep -i dma
```

3. Buggy GStreamer plugins/missing libraries (possible): try using a different media player, such as VLC.

---

### Post by jtdelasalas on 2008-11-11
Whenever I try to play a DVD my system gets bogged down, according to system monitor my CPU goes right up between 80-100% per core.

The resource goblling literally happens after 2 minutes

---

### Post by jtdelasalas on 2008-11-11
1.)  I'm using the most recent Nvidia proprietary drivers

2.)  This is the output for that:

~$ dmesg | grep -i dma
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    3.777519] ata1: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 18
[    3.777523] ata2: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 18
[    4.260253] ata1.00: ATA-7: ST9160821AS, 3.BHD, max UDMA/100
[    4.276234] ata1.00: configured for UDMA/100
[    5.124569] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[    5.202608] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    5.202612] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    5.528559] ata4.00: ATAPI: MATSHITADVD-RAM UJ-851S, 1.50, max MWD

3.)  How would I check for this one?

---

### Post by psyke83 on 2008-11-11
> **jtdelasalas said:**
> 1.)  I'm using the most recent Nvidia proprietary drivers

2.)  This is the output for that:

~$ dmesg | grep -i dma
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    3.777519] ata1: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 18
[    3.777523] ata2: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 18
[    4.260253] ata1.00: ATA-7: ST9160821AS, 3.BHD, max UDMA/100
[    4.276234] ata1.00: configured for UDMA/100
[    5.124569] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[    5.202608] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[    5.202612] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[    5.528559] ata4.00: ATAPI: MATSHITADVD-RAM UJ-851S, 1.50, max MWD

3.)  How would I check for this one?

Ok, your problem may be due to the overhead caused by compiz. Disable Desktop Effects and see if your CPU usage/stuttering is reduced.

---

### Post by jtdelasalas on 2008-11-11
I disabled visual effects, for the most part it still takes 2 minutes and the dvd becomes choppy again.

---

### Post by jtdelasalas on 2008-11-12
Could this be a kernel issue?  I was able to actually multitask while watching a movie, but now the moment a movie starts all system resources are sucked up.

---

### Post by jtdelasalas on 2008-11-13
What kind of test could I do to determine if this is a hardware issue?

---

