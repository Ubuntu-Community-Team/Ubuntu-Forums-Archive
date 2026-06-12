---
title: "boot from SD"
date: 2013-02-13
forum: Mythbuntu
---

### Post by jsprenkl on 2013-02-13
Good morning,
I have an ASUS EB1033 box for my htpc build. I need some advice on installing mythbuntu.

The ASUS specs:
* Intel ATOM NM10 dual core
* 4GB ram
* Video Nvidia GeForce 610M w/512MB RAM
* 16GB SD card
* hdmi and regular vga outputs
* Space for a 2.5 inch sata disk. No disk is installed
* rosewill external usb drive
* streamzap remote

I'd like to run this as a disk less front end only for mythtv.
I have a combined backend with loads of disk storage on my network.

As a test I have installed the latest Mythbuntu.
* The system installed to the SD card without issue.
* I haven't tested the hdmi output
* the vga video works fine.
* The box boots from SD but the front end just crashes. My backend does not use the current schema and the front end will not start at all until I upgrade.
* VLC plays DVD's fine on the vga video output 

I assume this install is using the SD card for it's file system just as it would a regular disk. So I believe it's writing temp files and putting the swap partition on the SD card. Since this isn't wear leveled and is using flash memory this seems like a really bad setup.

I looked at minimyth but it looks like it I have to almost build my own distro to get it to work in this mode.

Q: Is there a distro or install option to use mythbunutu in diskless mode with a RAMFS? I could add an SSD but that would add cost to the build.

Q: What's the correct driver/setting for the HDMI output? This box only provides sound via the HDMI cable

Thanks

---

