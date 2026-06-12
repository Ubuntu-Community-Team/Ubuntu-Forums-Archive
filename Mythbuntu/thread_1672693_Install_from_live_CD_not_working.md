---
title: "Install from live CD not working"
date: 2011-01-21
forum: Mythbuntu
---

### Post by ill_switch on 2011-01-21
Hello forum,

I am new to mythbuntu and working on installing on a newly built PC. The computer consists of:

Foxconn M61PMP-K AM3 NVIDIA MCP61P Micro ATX AMD Motherboard
AMD Athlon II X2 240 Regor 2.8GHz Socket AM3 65W Dual-Core Processor ADX240OCGQBOX
Patriot 2GB 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10600) Desktop Memory Model PSD32G13332
HITACHI Deskstar 7K1000.C HDS721010CLA332 (0F10383) 1TB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive

Plus an old case and PSU and an old 18gb IDE drive, and an old CD-RW drive.

The BIOS recognizes all hardware. I have a live CD created from the latest 64 bit image on the download section of the mythbuntu website (version 10.10). The CD is in the CD drive, and the CD drive is before the two HDD's in boot order.

When the machine boots, the BIOS gives an error message about keyboard not found (I'm using a cheap logitech wireless keyboard, not sure why it can't find it because it responds to key inputs).

Then, I get a blinking cursor, and a second later, "GRUB" followed by a blinking cursor. Then, nothing. It just sits there with the word GRUB staring at me.

I'm hoping this is something obvious to you more seasoned linux experts but I'm stuck. Any ideas?

---

### Post by ill_switch on 2011-01-21
Ok, problem solved. I feel foolish. It was trying to boot off the old 18gb drive, which had a (failed) install of another distro on it from years ago. Apparently I didn't have the device boot order set correctly after all.

Fixed that and now I have another problem. I'm seeing the Mythbuntu boot screen ("Mythbuntu" with the little dots under it) and then this:

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

---

### Post by ill_switch on 2011-01-23
And, that problem solved as well. It was a corrupt CD.

---

