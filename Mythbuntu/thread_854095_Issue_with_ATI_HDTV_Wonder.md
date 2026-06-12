---
title: "Issue with ATI HDTV Wonder"
date: 2008-07-09
forum: Mythbuntu
---

### Post by jablack on 2008-07-09
The system I'm running this in is:

Intel Pentium Dual Core 2.2 GHZ
2 GB of Corsair RAM
4 GB Swap partition
Abit IP35Pro Motherboard (P35 chipset with the ICH9R southbridge)
Nvidia 7300GS (Used for display)
ATI HDTV Wonder
Hauppauge WinTV PVR-350 (Using only the inputs)
Hauppauge WinTV PVR-500

Sometimes when I try to record on the HDTV Wonder the mythbackend.log will show:

2008-07-09 05:19:05.605 RingBuffer::RingBuffer(): Failed to open remote file ()
2008-07-09 05:19:05.943 DVBSH(0): Failed to open DVR device /dev/dvb/adapter0/dvr0 : Cannot allocate memory

Also the following is added to the dmesg output:

[ 1902.248734] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.
[ 1902.679615] allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.


When this happens, I am unable to record from the HDTV card. Sometimes if I reboot the problems will go away for a while. I've tested the memory on the unit and it appears to be working fine (Though I couldn't get the memory test from the Mythbuntu menu to run.... I had to go burn a Memtest disk). I've also tested the hard disk the operating system is running on and it appears to be fine as well. The problems I have may be related to a problem with system stability, but I don't know how to test the system beyond what I have. I've also attached my lspci and dmesg output.

Also this is the latest version of Mythbuntu with all the updates installed.

Thanks!

Jonathan

---

