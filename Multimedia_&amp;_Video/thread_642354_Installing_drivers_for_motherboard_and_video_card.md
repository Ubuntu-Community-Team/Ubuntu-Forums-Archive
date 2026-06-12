---
title: "Installing drivers for motherboard and video card"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by monkeythumpa on 2007-12-16
I have searched the forum and googled but to no avail. The short: How do I install drivers?

The long: I put together a system and it is working pretty well. MythTV is installed and they system is stable. I got it networking with the computers, MS and Apples. The motherboard and videocard are doing well but I fear they are not "all there". When there is a lot of action on the DVDs, the video gets a line in it, like when you take a picture of an interlaced screen. And the optical out of the motherboard is not shining a laser. I tried to turn it on through the bios but there is no option for that.

So I have the linux drivers for the motherboard and video card on CDs, but how do I install them? I am a noob to Linux, although I have been working with Unix for years and the command line interface doesn't scare me. Thanks!

Here are my specs:
3 gigs of SLI RAM
AMD Athlon 64 X2 6000+ Windsor 3.0GHz Socket AM2 Dual-Core Processor Model ADX6000CZBOX
ASUS M2N32-SLI Deluxe Wireless Edition AM2 NVIDIA nForce 590 SLI MCP ATX AMD Motherboard
ASUS EN8500GT SILENT/HTP/256M GeForce 8500GT 256MB 128-bit GDDR2 PCI Express x16 HDCP Ready Video Card
ASUS 20X DVD±R DVD Burner with LightScribe Black SATA Model DRW-2014L1T
Seagate Barracuda 7200.11 ST3500320AS 500GB 7200 RPM SATA 3.0Gb/s Hard Drive
Rosewill RP600V2-S-SL-S ATX12V v2.01 600W Power Supply
SILVERSTONE LASCALA 10 CS-SST-LC10B Black Aluminum front panel, 1.0mm SECC body ATX Media Center

---

### Post by acoustibop on 2007-12-16
Motherboard drivers should be included in the OS, monkeythumpa.  It's unusual to have to install anything extra.

I presume you're running Gutsy?  As far as your videocard is concerned, you have two options - use the Restricted Drivers Manager (System -> Administration -> Restricted Drivers Manager) to install a proprietary Nvidia driver - easy - just check a box and reboot.

Or, visit the Nvidia support site and download the current proprietary driver - I'm not sure about installing it, but there should be instructions on the site or in the package.

---

