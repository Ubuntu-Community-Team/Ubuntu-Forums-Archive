---
title: "Two video capture cards -- one hard drive"
date: 2009-02-24
forum: Mythbuntu
---

### Post by brian_hayward on 2009-02-24
I want to use two hauppauge PVR-350 video capture cards in my mythbuntu system with a 7200 RPM hard drive and 512gb of memory.  Will I have trouble recording two shows at the same time with just one hard drive??  

If anybody is currently using this type of setup please let me know about your experiences.  Thanks.

---

### Post by newlinux on 2009-02-24
I have a couple of systems with 2+ tuners recording to one hard drive, including a system with two kworld ATSC 110s and a PVR-150 all recording to the same hard drive and I haven't run into any conflicts of multiple usage. My machines all have 1-2GB of RAM, however, but I don't think that will be an issue. Multiple SD streams shouldn't be a problem. I recommend you use a separate partition than your root filesystem for recordings.

Depending on your CPU, multiple simultaneous commflagging might be more of an issue - but you can schedule those for low usage times if that is an issue.

---

### Post by klc5555 on 2009-02-24
> **brian_hayward said:**
> I want to use two hauppauge PVR-350 video capture cards in my mythbuntu system with a 7200 RPM hard drive and 512gb of memory.  Will I have trouble recording two shows at the same time with just one hard drive??  

If anybody is currently using this type of setup please let me know about your experiences.  Thanks.

Analog doesn't write that much data to harddisk, so two recordings onto one disk OUGHT to be OK for you, even with a slow IDE drive and the swap partition on that drive. 512M of memory is not a lot and may certainly prove to be a bottleneck (as may processor speed), but the 350 is a hardware encoder and doesn't drag the hardware much.

For a (very) brief while I used two pchd5500s in a single IDE drive system. Unlike the PVR 350, the pchdtv5500 is a software encoder in both digital and analog, and I found that I could:

1) Record 1 HD show (and do nothing else) (IDE hard disk speed problems with all the simultaneous read/writes, incl. swap)
2) Record 2 SD shows simultaneously.
3) Record 1 SD show and 1 analog show.
4) Record 2 simultaneous analog shows only if I used RTJPEG; MPEG4 was too resource intensive.

After a few weeks I added a fast SATA drive just for recordings, kept my original IDE drive just for the OS and swap, and upped memory from 1.0 to 1.5 G. This removed all bottlenecks, and when I added a PVR150, I could record all three tuners simultaneously to the single recordings harddisk without difficulty.

Cheers!

---

### Post by brian_hayward on 2009-02-24
> **newlinux said:**
> I have a couple of systems with 2+ tuners recording to one hard drive, including a system with two kworld ATSC 110s and a PVR-150 all recording to the same hard drive and I haven't run into any conflicts of multiple usage. My machines all have 1-2GB of RAM, however, but I don't think that will be an issue. Multiple SD streams shouldn't be a problem. I recommend you use a separate partition than your root filesystem for recordings.

Depending on your CPU, multiple simultaneous commflagging might be more of an issue - but you can schedule those for low usage times if that is an issue.

One additional comment, i am recording analog cable shows, which i understand takes more processing power to record.  

Also, I've read about using separate partitions for the operating system and recordings, but what I don't ever see is an explanation as to why this is.  Can you provide me one or point me in the direction of an explanation?  Thanks.

---

### Post by newlinux on 2009-02-24
> **brian_hayward said:**
> One additional comment, i am recording analog cable shows, which i understand takes more processing power to record.  

Also, I've read about using separate partitions for the operating system and recordings, but what I don't ever see is an explanation as to why this is.  Can you provide me one or point me in the direction of an explanation?  Thanks.

analog recording in software only takes a little CPU power by today's standards. You are using onboard hardware encoding with the PVR-350, so most of the processing is done by the tuner cards, not the CPU - so this should be of minimal impact to your system. 

I can give you a couple of good reasons.

1. if you ever have to rebuild your system or do a reinstall, your recordings will be on a separate partition from your OS, so they won't be deleted.

2. The filesystem type for your recordings should be something probably more robust for large files, like XFS or JFS. You root partition would probably be better off being EXT3 for stability and recovery. If they are all the same partition you have to pick one or the other.


There are some other reasons... but I gotta run. You can google it though...

---

