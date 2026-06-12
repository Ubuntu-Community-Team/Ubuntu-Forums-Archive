---
title: "Can't play DVDs /dev/sr0 i/o errors"
date: 2009-05-05
forum: Multimedia Software
---

### Post by frugal on 2009-05-05
Hi,

Sorry to be posting yet another can't play DVDs thread but I've done quite a bit of searching on this one and can't seem to solve it.

I'm running Mythbuntu jaunty on an Intel DG45ID motherboard and have just about everything working great except for DVD playback. I installed from this CD using the live CD so I know the drive at least works for reading CDs.

I've followed the restricted packages info so I should have all the software installed. The issue I'm seeing though are tons of I/O errors whenever I insert a disk although an audio CD at least plays and I can mount a DVD and browse it fine, just can't play them.

Here's the output in /var/log/messages when I try to insert a DVD:

```

May  5 19:26:09 pvr kernel: [  487.860870] UDF-fs: Partition marked readonly; forcing readonly mountMay  5 19:26:09 pvr kernel: [  487.911851] UDF-fs INFO UDF: Mounting volume 'AKIRA_DISC2', timestamp 2001/05/24 04:13 (1000)
May  5 19:26:23 pvr kernel: [  502.163922] sr: Sense Key : Hardware Error [current]
May  5 19:26:23 pvr kernel: [  502.163925] sr: Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
```Here's the info from hdparm -I /dev/sr0:

```

/dev/sr0:

ATAPI CD-ROM, with removable media
        Model Number:       PIONEER DVD-RW  DVR-K06                 
        Serial Number:      HFDL065548WL       
        Firmware Revision:  1.01    
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(can be disabled)
        Buffer size: 64.0kB
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    Power Management feature set
           *    PACKET command feature set
           *    DEVICE_RESET command
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper

```The one thing I'm not sure if is causing an issue is this is a PATA laptop drive connected with a SATA adapter, obviously the drive is detecting and as I said, I installed fine from this drive so the adapter seems to be working but I'm wondering if that's not part of the issue with what's causing the I/O errors and if there's not a kernel argument that I need to use to tell it that it's a PATA drive.

I'm strongly suspecting that the I/O errors are at least part of my problem, if not the entire issue but if someone has other suggestions that might resolve this I'm open to them.

Thanks for any assistance.

---

### Post by lisati on 2009-05-05
Do the I/O errors happen all DVDs or just one or two? Sometimes all that is needed to check the disks for dirt and scratches.

---

### Post by frugal on 2009-05-06
D'oh! Chalk this up to seeing "inappropriate ioctl" under hdparm and not knowing why that's there with modern libata and then the i/o errors in the kernel messages really made me think this was something bigger.

I tried a few other DVDs and am only batting 1 out of 4 so far but I haven't tried cleaning up the other disks. Had a couple minor issues with stuttering playback, especially in the internal player in myth but that was solved by increasing the readahead.

Gotta try some more disks yet and see if my odds improve or if the 1 disk that worked is the exception rather than the rule.

---

