---
title: "&quot;Graphics&quot; Bug when boot liveCD in UEFI Board"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by alphaamanitin on 2011-04-24
Hello,

I have a ASRock 880G Pro3 motherboard.  At first neither the 11.04 beta1 AMD64 or 11.04.2 beta2 AMD64 LiveCDs would boot in UEFI mode.  After updating the boards software from 1.1 to 1.2 both LiveCDs would boot in UEFI mode.  I would first get this text, "Error: "prefix" failure to load" or something like that.  Then I would get a screen letting me select three options, try ubuntu, install ubuntu, or check disk for errors.  No matter what option I chose I get the following odd graphics:

The amount of screen visible is slightly variable, but in all cases there is any where from 2 mm to 4 mm of actually screen across the top of the monitor.  In this screen I can see anything that is there, the ubuntu buttons, the mouse, etc.  Sometimes the screen looks like it is flashing up there.  Now, below that point it is black or a black/purple.  If I move the mouse to the very top right of the screen I get various graphical errors that are not predictable.  Most of the time though it turns the screen into black and white vertical strips ~1cm wide.  I do mean the entire screen in this case, including the area at the very top of the scree.  

Here is my setup:
MOBO: ASRock 880G Pro3 v1.2 firmware
CPU: AMD Phenom II x6 Black Edition Thuban ~3.3ghz
HD: Crucial 64 gb 2.5" SATAIII SSD-Boot drive
       Seagate barracude SATAIII 2TB
RAM: 16 gb (4x4gb) G.Skill Ripjaw series 1333
GPU: Asus EAH6850 AMD 6850 video card
PSU: Corsair 750W PSU
Keyboard: Microsoft Ergonomic 4000
Mouse: Logitech LS1 laser mouse
USB wireless adapter: Belkin G MIMO USB wireless adapter FD050(I think) v4000
Optical Drive: Sony DVD CD +/- combo drive

Think that is it.  Cannot think of anything else that is attached to that computer.

AlphaA

---

### Post by alphaamanitin on 2011-04-25
Solved.  Change boot location of cd by hitting 'e' at choices screen (try ubuntu, install ubuntu, check disk for errors) to: ```
/cdrom/efi/boot/bootx64.efi
```After booting into the LiveCD environment ran: ```
dmesg | grep EFI
``` Here is the  output:```
ubuntu@ubuntu:~$ dmesg | grep EFI
[    0.000000] EFI v2.00 by American Megatrends
[    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
[    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x000000000007f000) (0MB)
[    0.000000] EFI: mem02: type=4, attr=0xf, range=[0x000000000007f000-0x0000000000080000) (0MB)
[    0.000000] EFI: mem03: type=3, attr=0xf, range=[0x0000000000080000-0x00000000000a0000) (0MB)
[    0.000000] EFI: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x000000000064d000) (5MB)
[    0.000000] EFI: mem05: type=7, attr=0xf, range=[0x000000000064d000-0x0000000001000000) (9MB)
[    0.000000] EFI: mem06: type=4, attr=0xf, range=[0x0000000001000000-0x0000000001565000) (5MB)
[    0.000000] EFI: mem07: type=3, attr=0xf, range=[0x0000000001565000-0x0000000001569000) (0MB)
[    0.000000] EFI: mem08: type=4, attr=0xf, range=[0x0000000001569000-0x0000000001596000) (0MB)
[    0.000000] EFI: mem09: type=3, attr=0xf, range=[0x0000000001596000-0x000000000159c000) (0MB)
[    0.000000] EFI: mem10: type=4, attr=0xf, range=[0x000000000159c000-0x000000000159f000) (0MB)
[    0.000000] EFI: mem11: type=3, attr=0xf, range=[0x000000000159f000-0x00000000015a2000) (0MB)
[    0.000000] EFI: mem12: type=4, attr=0xf, range=[0x00000000015a2000-0x00000000015a5000) (0MB)
[    0.000000] EFI: mem13: type=3, attr=0xf, range=[0x00000000015a5000-0x00000000015a8000) (0MB)
[    0.000000] EFI: mem14: type=4, attr=0xf, range=[0x00000000015a8000-0x00000000015aa000) (0MB)
[    0.000000] EFI: mem15: type=3, attr=0xf, range=[0x00000000015aa000-0x00000000015ac000) (0MB)
[    0.000000] EFI: mem16: type=4, attr=0xf, range=[0x00000000015ac000-0x00000000015ad000) (0MB)
[    0.000000] EFI: mem17: type=3, attr=0xf, range=[0x00000000015ad000-0x00000000015af000) (0MB)
[    0.000000] EFI: mem18: type=4, attr=0xf, range=[0x00000000015af000-0x00000000015b3000) (0MB)
[    0.000000] EFI: mem19: type=3, attr=0xf, range=[0x00000000015b3000-0x00000000015b5000) (0MB)
[    0.000000] EFI: mem20: type=4, attr=0xf, range=[0x00000000015b5000-0x00000000015b6000) (0MB)
[    0.000000] EFI: mem21: type=3, attr=0xf, range=[0x00000000015b6000-0x00000000015b7000) (0MB)
[    0.000000] EFI: mem22: type=4, attr=0xf, range=[0x00000000015b7000-0x00000000015bf000) (0MB)
[    0.000000] EFI: mem23: type=3, attr=0xf, range=[0x00000000015bf000-0x00000000015c2000) (0MB)
[    0.000000] EFI: mem24: type=4, attr=0xf, range=[0x00000000015c2000-0x00000000015d3000) (0MB)
[    0.000000] EFI: mem25: type=3, attr=0xf, range=[0x00000000015d3000-0x00000000015de000) (0MB)
[    0.000000] EFI: mem26: type=4, attr=0xf, range=[0x00000000015de000-0x00000000015e8000) (0MB)
[    0.000000] EFI: mem27: type=3, attr=0xf, range=[0x00000000015e8000-0x00000000015ef000) (0MB)
[    0.000000] EFI: mem28: type=4, attr=0xf, range=[0x00000000015ef000-0x00000000015f4000) (0MB)
[    0.000000] EFI: mem29: type=3, attr=0xf, range=[0x00000000015f4000-0x00000000015f5000) (0MB)
[    0.000000] EFI: mem30: type=4, attr=0xf, range=[0x00000000015f5000-0x00000000015fc000) (0MB)
[    0.000000] EFI: mem31: type=3, attr=0xf, range=[0x00000000015fc000-0x00000000015fd000) (0MB)
[    0.000000] EFI: mem32: type=4, attr=0xf, range=[0x00000000015fd000-0x0000000001628000) (0MB)
[    0.000000] EFI: mem33: type=3, attr=0xf, range=[0x0000000001628000-0x000000000162a000) (0MB)
[    0.000000] EFI: mem34: type=4, attr=0xf, range=[0x000000000162a000-0x000000000162f000) (0MB)
[    0.000000] EFI: mem35: type=3, attr=0xf, range=[0x000000000162f000-0x0000000001631000) (0MB)
[    0.000000] EFI: mem36: type=4, attr=0xf, range=[0x0000000001631000-0x0000000001633000) (0MB)
[    0.000000] EFI: mem37: type=3, attr=0xf, range=[0x0000000001633000-0x000000000165a000) (0MB)
[    0.000000] EFI: mem38: type=4, attr=0xf, range=[0x000000000165a000-0x000000000165b000) (0MB)
[    0.000000] EFI: mem39: type=3, attr=0xf, range=[0x000000000165b000-0x000000000165c000) (0MB)
[    0.000000] EFI: mem40: type=4, attr=0xf, range=[0x000000000165c000-0x000000000165e000) (0MB)
[    0.000000] EFI: mem41: type=3, attr=0xf, range=[0x000000000165e000-0x000000000166e000) (0MB)
[    0.000000] EFI: mem42: type=4, attr=0xf, range=[0x000000000166e000-0x000000000167f000) (0MB)
[    0.000000] EFI: mem43: type=3, attr=0xf, range=[0x000000000167f000-0x0000000001683000) (0MB)
[    0.000000] EFI: mem44: type=4, attr=0xf, range=[0x0000000001683000-0x0000000001684000) (0MB)
[    0.000000] EFI: mem45: type=3, attr=0xf, range=[0x0000000001684000-0x0000000001689000) (0MB)
[    0.000000] EFI: mem46: type=4, attr=0xf, range=[0x0000000001689000-0x0000000001691000) (0MB)
[    0.000000] EFI: mem47: type=3, attr=0xf, range=[0x0000000001691000-0x0000000001693000) (0MB)
[    0.000000] EFI: mem48: type=4, attr=0xf, range=[0x0000000001693000-0x0000000001695000) (0MB)
[    0.000000] EFI: mem49: type=3, attr=0xf, range=[0x0000000001695000-0x0000000001698000) (0MB)
[    0.000000] EFI: mem50: type=4, attr=0xf, range=[0x0000000001698000-0x000000000169a000) (0MB)
[    0.000000] EFI: mem51: type=3, attr=0xf, range=[0x000000000169a000-0x000000000169e000) (0MB)
[    0.000000] EFI: mem52: type=4, attr=0xf, range=[0x000000000169e000-0x00000000016a3000) (0MB)
[    0.000000] EFI: mem53: type=3, attr=0xf, range=[0x00000000016a3000-0x00000000016a4000) (0MB)
[    0.000000] EFI: mem54: type=4, attr=0xf, range=[0x00000000016a4000-0x00000000016b0000) (0MB)
[    0.000000] EFI: mem55: type=3, attr=0xf, range=[0x00000000016b0000-0x00000000016b9000) (0MB)
[    0.000000] EFI: mem56: type=4, attr=0xf, range=[0x00000000016b9000-0x00000000016bb000) (0MB)
[    0.000000] EFI: mem57: type=3, attr=0xf, range=[0x00000000016bb000-0x00000000016c6000) (0MB)
[    0.000000] EFI: mem58: type=4, attr=0xf, range=[0x00000000016c6000-0x00000000016c8000) (0MB)
[    0.000000] EFI: mem59: type=3, attr=0xf, range=[0x00000000016c8000-0x00000000016d0000) (0MB)
[    0.000000] EFI: mem60: type=4, attr=0xf, range=[0x00000000016d0000-0x00000000016d2000) (0MB)
[    0.000000] EFI: mem61: type=3, attr=0xf, range=[0x00000000016d2000-0x00000000016d4000) (0MB)
[    0.000000] EFI: mem62: type=4, attr=0xf, range=[0x00000000016d4000-0x00000000016d5000) (0MB)
[    0.000000] EFI: mem63: type=3, attr=0xf, range=[0x00000000016d5000-0x00000000016d8000) (0MB)
[    0.000000] EFI: mem64: type=4, attr=0xf, range=[0x00000000016d8000-0x00000000016df000) (0MB)
[    0.000000] EFI: mem65: type=3, attr=0xf, range=[0x00000000016df000-0x00000000016e6000) (0MB)
[    0.000000] EFI: mem66: type=4, attr=0xf, range=[0x00000000016e6000-0x00000000016fb000) (0MB)
[    0.000000] EFI: mem67: type=3, attr=0xf, range=[0x00000000016fb000-0x000000000170a000) (0MB)
[    0.000000] EFI: mem68: type=4, attr=0xf, range=[0x000000000170a000-0x000000000170b000) (0MB)
[    0.000000] EFI: mem69: type=3, attr=0xf, range=[0x000000000170b000-0x000000000170e000) (0MB)
[    0.000000] EFI: mem70: type=4, attr=0xf, range=[0x000000000170e000-0x000000000171e000) (0MB)
[    0.000000] EFI: mem71: type=3, attr=0xf, range=[0x000000000171e000-0x0000000001729000) (0MB)
[    0.000000] EFI: mem72: type=4, attr=0xf, range=[0x0000000001729000-0x0000000001735000) (0MB)
[    0.000000] EFI: mem73: type=3, attr=0xf, range=[0x0000000001735000-0x0000000001739000) (0MB)
[    0.000000] EFI: mem74: type=4, attr=0xf, range=[0x0000000001739000-0x000000000173d000) (0MB)
[    0.000000] EFI: mem75: type=3, attr=0xf, range=[0x000000000173d000-0x000000000173e000) (0MB)
[    0.000000] EFI: mem76: type=4, attr=0xf, range=[0x000000000173e000-0x000000000173f000) (0MB)
[    0.000000] EFI: mem77: type=3, attr=0xf, range=[0x000000000173f000-0x0000000001742000) (0MB)
[    0.000000] EFI: mem78: type=4, attr=0xf, range=[0x0000000001742000-0x0000000001748000) (0MB)
[    0.000000] EFI: mem79: type=3, attr=0xf, range=[0x0000000001748000-0x000000000178a000) (0MB)
[    0.000000] EFI: mem80: type=4, attr=0xf, range=[0x000000000178a000-0x0000000001794000) (0MB)
[    0.000000] EFI: mem81: type=3, attr=0xf, range=[0x0000000001794000-0x0000000001799000) (0MB)
[    0.000000] EFI: mem82: type=4, attr=0xf, range=[0x0000000001799000-0x00000000017a1000) (0MB)
[    0.000000] EFI: mem83: type=3, attr=0xf, range=[0x00000000017a1000-0x00000000017a7000) (0MB)
[    0.000000] EFI: mem84: type=4, attr=0xf, range=[0x00000000017a7000-0x00000000017a9000) (0MB)
[    0.000000] EFI: mem85: type=3, attr=0xf, range=[0x00000000017a9000-0x00000000017ab000) (0MB)
[    0.000000] EFI: mem86: type=4, attr=0xf, range=[0x00000000017ab000-0x00000000017ad000) (0MB)
[    0.000000] EFI: mem87: type=3, attr=0xf, range=[0x00000000017ad000-0x00000000017af000) (0MB)
[    0.000000] EFI: mem88: type=4, attr=0xf, range=[0x00000000017af000-0x00000000017b3000) (0MB)
[    0.000000] EFI: mem89: type=3, attr=0xf, range=[0x00000000017b3000-0x00000000017b5000) (0MB)
[    0.000000] EFI: mem90: type=4, attr=0xf, range=[0x00000000017b5000-0x00000000017b9000) (0MB)
[    0.000000] EFI: mem91: type=3, attr=0xf, range=[0x00000000017b9000-0x00000000017bb000) (0MB)
[    0.000000] EFI: mem92: type=4, attr=0xf, range=[0x00000000017bb000-0x00000000017bc000) (0MB)
[    0.000000] EFI: mem93: type=3, attr=0xf, range=[0x00000000017bc000-0x00000000017be000) (0MB)
[    0.000000] EFI: mem94: type=4, attr=0xf, range=[0x00000000017be000-0x0000000001c97000) (4MB)
[    0.000000] EFI: mem95: type=3, attr=0xf, range=[0x0000000001c97000-0x0000000001c99000) (0MB)
[    0.000000] EFI: mem96: type=4, attr=0xf, range=[0x0000000001c99000-0x0000000001cad000) (0MB)
[    0.000000] EFI: mem97: type=3, attr=0xf, range=[0x0000000001cad000-0x0000000001caf000) (0MB)
[    0.000000] EFI: mem98: type=4, attr=0xf, range=[0x0000000001caf000-0x0000000001cb1000) (0MB)
[    0.000000] EFI: mem99: type=3, attr=0xf, range=[0x0000000001cb1000-0x0000000001cb3000) (0MB)
[    0.000000] EFI: mem100: type=4, attr=0xf, range=[0x0000000001cb3000-0x0000000001cb5000) (0MB)
[    0.000000] EFI: mem101: type=3, attr=0xf, range=[0x0000000001cb5000-0x0000000001cbf000) (0MB)
[    0.000000] EFI: mem102: type=4, attr=0xf, range=[0x0000000001cbf000-0x0000000001cc1000) (0MB)
[    0.000000] EFI: mem103: type=3, attr=0xf, range=[0x0000000001cc1000-0x0000000001cc3000) (0MB)
[    0.000000] EFI: mem104: type=4, attr=0xf, range=[0x0000000001cc3000-0x0000000001cc5000) (0MB)
[    0.000000] EFI: mem105: type=3, attr=0xf, range=[0x0000000001cc5000-0x0000000001cc7000) (0MB)
[    0.000000] EFI: mem106: type=4, attr=0xf, range=[0x0000000001cc7000-0x0000000001cc8000) (0MB)
[    0.000000] EFI: mem107: type=3, attr=0xf, range=[0x0000000001cc8000-0x0000000001ccc000) (0MB)
[    0.000000] EFI: mem108: type=4, attr=0xf, range=[0x0000000001ccc000-0x0000000001cd3000) (0MB)
[    0.000000] EFI: mem109: type=3, attr=0xf, range=[0x0000000001cd3000-0x0000000001cd5000) (0MB)
[    0.000000] EFI: mem110: type=4, attr=0xf, range=[0x0000000001cd5000-0x0000000001ce3000) (0MB)
[    0.000000] EFI: mem111: type=3, attr=0xf, range=[0x0000000001ce3000-0x0000000001ce5000) (0MB)
[    0.000000] EFI: mem112: type=4, attr=0xf, range=[0x0000000001ce5000-0x0000000001ce6000) (0MB)
[    0.000000] EFI: mem113: type=3, attr=0xf, range=[0x0000000001ce6000-0x0000000001ced000) (0MB)
[    0.000000] EFI: mem114: type=4, attr=0xf, range=[0x0000000001ced000-0x0000000001cf3000) (0MB)
[    0.000000] EFI: mem115: type=3, attr=0xf, range=[0x0000000001cf3000-0x0000000001cf6000) (0MB)
[    0.000000] EFI: mem116: type=4, attr=0xf, range=[0x0000000001cf6000-0x0000000001d16000) (0MB)
[    0.000000] EFI: mem117: type=3, attr=0xf, range=[0x0000000001d16000-0x0000000001d26000) (0MB)
[    0.000000] EFI: mem118: type=4, attr=0xf, range=[0x0000000001d26000-0x000000000213d000) (4MB)
[    0.000000] EFI: mem119: type=3, attr=0xf, range=[0x000000000213d000-0x000000000213e000) (0MB)
[    0.000000] EFI: mem120: type=4, attr=0xf, range=[0x000000000213e000-0x0000000002140000) (0MB)
[    0.000000] EFI: mem121: type=3, attr=0xf, range=[0x0000000002140000-0x0000000002141000) (0MB)
[    0.000000] EFI: mem122: type=4, attr=0xf, range=[0x0000000002141000-0x0000000002147000) (0MB)
[    0.000000] EFI: mem123: type=3, attr=0xf, range=[0x0000000002147000-0x0000000002153000) (0MB)
[    0.000000] EFI: mem124: type=4, attr=0xf, range=[0x0000000002153000-0x0000000002258000) (1MB)
[    0.000000] EFI: mem125: type=7, attr=0xf, range=[0x0000000002258000-0x0000000002271000) (0MB)
[    0.000000] EFI: mem126: type=4, attr=0xf, range=[0x0000000002271000-0x000000000237b000) (1MB)
[    0.000000] EFI: mem127: type=7, attr=0xf, range=[0x000000000237b000-0x0000000002387000) (0MB)
[    0.000000] EFI: mem128: type=4, attr=0xf, range=[0x0000000002387000-0x0000000002388000) (0MB)
[    0.000000] EFI: mem129: type=7, attr=0xf, range=[0x0000000002388000-0x0000000002389000) (0MB)
[    0.000000] EFI: mem130: type=4, attr=0xf, range=[0x0000000002389000-0x000000000238a000) (0MB)
[    0.000000] EFI: mem131: type=7, attr=0xf, range=[0x000000000238a000-0x000000000238c000) (0MB)
[    0.000000] EFI: mem132: type=4, attr=0xf, range=[0x000000000238c000-0x0000000002466000) (0MB)
[    0.000000] EFI: mem133: type=7, attr=0xf, range=[0x0000000002466000-0x000000000249e000) (0MB)
[    0.000000] EFI: mem134: type=4, attr=0xf, range=[0x000000000249e000-0x000000000249f000) (0MB)
[    0.000000] EFI: mem135: type=7, attr=0xf, range=[0x000000000249f000-0x00000000024ab000) (0MB)
[    0.000000] EFI: mem136: type=4, attr=0xf, range=[0x00000000024ab000-0x00000000024ac000) (0MB)
[    0.000000] EFI: mem137: type=7, attr=0xf, range=[0x00000000024ac000-0x00000000024c6000) (0MB)
[    0.000000] EFI: mem138: type=4, attr=0xf, range=[0x00000000024c6000-0x00000000024e8000) (0MB)
[    0.000000] EFI: mem139: type=7, attr=0xf, range=[0x00000000024e8000-0x00000000024ea000) (0MB)
[    0.000000] EFI: mem140: type=4, attr=0xf, range=[0x00000000024ea000-0x00000000024eb000) (0MB)
[    0.000000] EFI: mem141: type=7, attr=0xf, range=[0x00000000024eb000-0x00000000024ec000) (0MB)
[    0.000000] EFI: mem142: type=4, attr=0xf, range=[0x00000000024ec000-0x00000000024ed000) (0MB)
[    0.000000] EFI: mem143: type=7, attr=0xf, range=[0x00000000024ed000-0x00000000024ef000) (0MB)
[    0.000000] EFI: mem144: type=4, attr=0xf, range=[0x00000000024ef000-0x00000000024f0000) (0MB)
[    0.000000] EFI: mem145: type=7, attr=0xf, range=[0x00000000024f0000-0x00000000024f1000) (0MB)

```Confirms that the computer is booted in UEFI mode.  No graphical anomalies to be reported.

AlphaA

---

### Post by alphaamanitin on 2011-04-25
Well, keeps crashing when trying to install the grub2 package, big shock.

AlphaA

---

