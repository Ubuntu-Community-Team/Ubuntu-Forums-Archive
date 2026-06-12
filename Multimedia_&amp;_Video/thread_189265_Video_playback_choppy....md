---
title: "Video playback choppy..."
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by imrazor on 2006-06-05
...when there's any kind of background activity. Breezy was about perfect in this respect - playback was smooth as silk unless there was something really chewing up the CPU. Now, video playback skips about once a minute if there's nothing going on, or much more frequently if there's any sort of background activity. Furthermore, the system slows to a crawl when there's video and background activity. Disk transfer speed slows down, extraction takes much longer, and the system is not very responsive. I've tried different different media players (Kaffeine, Totem, Mplayer) and drivers (fglrx, radeon, ati) all with the same results. Curiously, top only shows about 10% CPU usage for Xorg and 3-5% for kaffeine but the system acts like CPU usage is at 95%. Anyone have a clue what might be causing this? System specs below...

Dapper Drake i386
Emachines M6805
AMD Mobile Athlon 64 3000+
768MB DDR333 RAM
ATI Radeon Mobility 9600 64MB
Via VT8235 Sound "card"
Via K8T800 chipset

---

### Post by imrazor on 2006-06-07
FIxed it myself. There were two problems. One was that journaling on ext3 was causing stuttering. Solution: reformat drive to ext2. Problem 2 was that multi-sector I/O was disabled on the hard drive. Editing /etc/hdparm.conf set it to 16 and greatly decreased stuttering and slowdowns. I reverted to Breezy in the process, and generally prefer it since hibernation actually works.

---

### Post by gerbman on 2006-06-08
[QUOTE=imrazor]FIxed it myself. There were two problems. One was that journaling on ext3 was causing stuttering. Solution: reformat drive to ext2. Problem 2 was that multi-sector I/O was disabled on the hard drive. Editing /etc/hdparm.conf set it to 16 and greatly decreased stuttering and slowdowns. I reverted to Breezy in the process, and generally prefer it since hibernation actually works.[/QUOTE]You could have checked to make sure DMA is enabled on the drive. If you're still curious about this, read [here]("https://wiki.ubuntu.com/DMA?highlight=%28dma%29").

---

### Post by imrazor on 2006-06-08
[QUOTE=gerbman]You could have checked to make sure DMA is enabled on the drive. If you're still curious about this, read [here]("https://wiki.ubuntu.com/DMA?highlight=%28dma%29").[/QUOTE]

I *did* check the DMA and it was enabled. The only thing that wasn't enabled was the multi-sector I/O transfers. Now video plays smoothly through just about anything I do, but playing video still seems to slow the system far more than top (i.e., CPU usage) would seem to indicate.

---

