---
title: "Bttv on ASUS M3N78-EM working only with acpi=off"
date: 2010-01-17
forum: Multimedia Software
---

### Post by Jonie on 2010-01-17
After a recent board upgrade (ASUS M3N78-EM now) I noticed that my Winfast TV 2000/XP does not work anymore. The picture I get in any application or just while capturing is nothing but a slideshow. Booting with the option acpi=noirq makes it display a few frames per second instead of one frame per a few seconds but a smooth picture is achieved only if acpi is fully disabled (acpi=off). When ACPI is enabled, it does not however make any load on CPU, just can't push data over PCI bus.

Dmesg is full of such entries (if ACPI is on):

[  766.372328] bttv0: timeout: drop=803 irq=2977/2977, risc=4d4d4bf4, bits: HSYNC OFLOW
[  767.932339] bttv0: timeout: drop=833 irq=3093/3093, risc=4d4d6be4, bits: HSYNC OFLOW

Tested on both Hardy with 2.6.29 mainline and Karmic with default kernel. (64-bit)

I tried to shuffle PCI cards with no success. Windows 7 seems to have no problem with this configuration.

Edit: It looks like the C1E state of the processor increases IRQ latencies. Disabling it in BIOS solves the issue.

---

