---
title: "Help with underclocking Radeon X1600"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by 67GTA on 2007-04-20
I am using the xorg-driver-fglrx 8.34 from the repository. It seems that the core/memory settings are maxed out. I get artifacts on certain colors of blue, and the card fan runs too fast and never quits. I installed rovclock and wanted to see if lowering this would help. What is a safe minimum setting? Is there a method to the numbers? I also posted my rovclock info, but not educated enough to know what it all means.

shawnr@fastback:~$ aticonfig --lsp
    core/mem      [flags]
-----------------
* 1: 500/405 MHz  [default state]

shawnr@fastback:~$ sudo rovclock -i
Password:
Radeon overclock 0.6e by Hasw (hasw@hasw.net)

Found ATI card on 01:00, device id: 0x71c2
I/O base address: 0x2000
Video BIOS shadow found @ 0xc0000
Invalid reference clock from BIOS: 0.0 MHz
Memory size: 524288 kB
Memory channels: 0, CD,CH only: 0
tRcdRD:   3
tRcdWR:   1
tRP:      3
tRAS:     6
tRRD:     1
tR2W-CL:  1
tWR:      1
tW2R:     0
tW2Rsb:   0
tR2R:     1
tRFC:     13
tWL(0.5): 0
tCAS:     0
tCMD:     0
tSTR:     0
XTAL: 27.0 MHz, RefDiv: 13

Core: 0.15 MHz, Mem: 0.0 MHz

---

