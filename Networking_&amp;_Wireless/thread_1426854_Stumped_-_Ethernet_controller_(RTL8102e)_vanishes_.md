---
title: "Stumped - Ethernet controller (RTL8102e) vanishes without trace"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by FatsBollinger on 2010-03-10
Ok, I'm stumped on this one. A couple weeks ago the wired ethernet controller completely disappeared on my machine (64-bit Karmic on a Dell Inspiron Desktop 537ST, purchased in November).

The controller is a Realtek RTL8102e, which until recently was used successfully with the r8169 driver. But now:

* There is no reference to an Ethernet controller in lspci, lsusb, or ifconfig

* There are no references to the ethernet controller in dmesg or recent kernel logs

I have tried, without success:

* Booting from the original kernel, 2.6.31-14 -- no luck

* Booting from the original install/LiveCD -- no luck

* Shutting down and unplugging the computer for a minute (according to other threads this fixed a similar problem for dual-booting users) -- still no luck

* Playing with various network-related BIOS options -- yet again no luck

* Adding acpi=off to Grub options -- noper

* Installing the latest r8101 kernel from Realtek -- luckless once more


Any ideas?? What else can I try?? I can show you output from the programs I mentioned but like I said, they pretend the ethernet controller just doesn't exist. The light on the physical adapter comes on when I plug in an ethernet cord so I know it's not completely broken.

Kernel version: 2.6.31-19. NOT dual-booting

Thanks!!!

---

