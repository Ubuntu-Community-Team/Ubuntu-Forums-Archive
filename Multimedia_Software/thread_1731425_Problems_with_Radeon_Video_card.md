---
title: "Problems with Radeon Video card"
date: 2011-04-17
forum: Multimedia Software
---

### Post by ronnielsen1 on 2011-04-17
I'm having problems with trying to play 3d games or xbmc on a Compaq Evo N1020v laptop with Ati Radeon IGP 330M/340M/350M graphic card. Compiz works, glxgears works but any attempt to play 3d games results in failure.


> ron@laptop:~$ billard-gl

 BillardGL (C) 2001, 2002 Tobias Nopper, Stefan Disch, Martina Welte

drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.
ron@laptop:~$ 


```
ron@laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Memory at f4000000 (32-bit, prefetchable) [size=64M]
    Memory at f0600000 (32-bit, prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-ati
    Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
    Flags: bus master, 66MHz, medium devsel, latency 99
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f0300000-f03fffff
    Prefetchable memory behind bridge: f8000000-fbffffff
    Kernel modules: shpchp

00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
    Subsystem: Compaq Computer Corporation Device 0056
    Flags: bus master, medium devsel, latency 64, IRQ 5
    I/O ports at 8400 [size=256]
    Memory at f0014000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ALI 5451
    Kernel modules: snd-ali5451

00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
    Subsystem: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: alim7101_wdt, alim1535_wdt

00:0a.0 CardBus bridge: Texas Instruments PCI4410 PC card Cardbus Controller (rev 02)
    Subsystem: Compaq Computer Corporation Device 0056
    Flags: bus master, medium devsel, latency 168, IRQ 10
    Memory at ffbfe000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
    Memory window 0: 50000000-53fff000 (prefetchable)
    Memory window 1: 54000000-57fff000
    I/O window 0: 00001000-000010ff
    I/O window 1: 00001400-000014ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

00:0a.1 FireWire (IEEE 1394): Texas Instruments PCI4410 FireWire Controller (rev 02) (prog-if 10)
    Subsystem: Compaq Computer Corporation Device 0056
    Flags: bus master, medium devsel, latency 64, IRQ 10
    Memory at f0018000 (32-bit, non-prefetchable) [size=2K]
    Memory at f0010000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
    Subsystem: Compaq Computer Corporation Device 0056
    Flags: bus master, medium devsel, latency 64, IRQ 10
    I/O ports at 9000 [size=256]
    Memory at f0018800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139cp
    Kernel modules: 8139too, 8139cp

00:0c.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
    Subsystem: Compaq Computer Corporation Device 8d88
    Flags: medium devsel, IRQ 11
    Memory at f0000000 (32-bit, non-prefetchable) [size=64K]
    I/O ports at 8090 [size=8]
    Capabilities: <access denied>

00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if fa)
    Subsystem: ALi Corporation M5229 IDE
    Flags: bus master, medium devsel, latency 64
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at 8080 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_ali
    Kernel modules: pata_ali

00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
    Subsystem: ALi Corporation M7101 Power Management Controller [PMU]
    Flags: medium devsel
    Kernel driver in use: ali1535_smbus
    Kernel modules: alim7101_wdt, i2c-ali15x3, i2c-ali1535

00:13.0 USB Controller: NEC Corporation USB (rev 41) (prog-if 10)
    Subsystem: Compaq Computer Corporation Device 0056
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f0016000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: NEC Corporation USB (rev 41) (prog-if 10)
    Subsystem: Compaq Computer Corporation Device 0056
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f0017000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: NEC Corporation USB 2.0 (rev 02) (prog-if 20)
    Subsystem: Compaq Computer Corporation Device 0056
    Flags: bus master, medium devsel, latency 132, IRQ 11
    Memory at f0018c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
    Subsystem: Compaq Computer Corporation Device 0056
    Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 5
    Memory at f8000000 (32-bit, prefetchable) [size=64M]
    I/O ports at a000 [size=256]
    Memory at f0300000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at f0320000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon

02:00.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Subsystem: Belkin Device 701d
    Flags: bus master, medium devsel, latency 168, IRQ 10
    Memory at 54000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

ron@laptop:~$ 

```

```
ron@laptop:~$ xbmc
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.
*** glibc detected *** /usr/lib/xbmc/xbmc.bin: corrupted double-linked list: 0x0b530518 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0xb617a591]
/lib/tls/i686/cmov/libc.so.6(+0x6ced3)[0xb617bed3]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xb617eecd]
/usr/lib/libSDL-1.2.so.0(SDL_WaitThread+0x44)[0xb63aa894]
/usr/lib/libSDL-1.2.so.0(SDL_AudioQuit+0x41)[0xb63a2291]
/usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x65)[0xb63a16f5]
/usr/lib/libSDL-1.2.so.0(SDL_Quit+0x1e)[0xb63a177e]
/lib/tls/i686/cmov/libc.so.6(+0x2f1bf)[0xb613e1bf]
/lib/tls/i686/cmov/libc.so.6(+0x2f22f)[0xb613e22f]
/usr/lib/dri/radeon_dri.so(+0xa6c5d)[0xb5532c5d]
/usr/lib/dri/radeon_dri.so(rcommonFlushCmdBuf+0x78)[0xb54d80d8]
/usr/lib/dri/radeon_dri.so(radeonFlush+0x132)[0xb54d82c2]
/usr/lib/dri/radeon_dri.so(_mesa_flush+0x23)[0xb54f4193]
/usr/lib/dri/radeon_dri.so(_mesa_Flush+0x3b)[0xb54f433b]
/usr/lib/mesa/libGL.so.1(glXSwapBuffers+0x40)[0xb6b9c110]
/usr/lib/xbmc/xbmc.bin(_ZN15CWinSystemX11GL17PresentRenderImplEv+0x42)[0x85ca322]
/usr/lib/xbmc/xbmc.bin(_ZN15CRenderSystemGL13PresentRenderEv+0x45)[0x8604385]
/usr/lib/xbmc/xbmc.bin(_ZN15CGraphicContext4FlipEv+0x26)[0x8697786]
/usr/lib/xbmc/xbmc.bin(_ZN12CApplication6RenderEv+0x2ef)[0x83158bf]
/usr/lib/xbmc/xbmc.bin(_ZN16CXBApplicationEx3RunEv+0xc4)[0x8581894]
/usr/lib/xbmc/xbmc.bin(main+0x4c8)[0x85822a8]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xb6125bd6]
/usr/lib/xbmc/xbmc.bin[0x82064d1]
======= Memory map: ========
08048000-08baf000 r-xp 00000000 08:01 1057279    /usr/lib/xbmc/xbmc.bin
08baf000-08bd5000 r-xp 00b66000 08:01 1057279    /usr/lib/xbmc/xbmc.bin
08bd5000-08c0c000 rwxp 00b8c000 08:01 1057279    /usr/lib/xbmc/xbmc.bin
08c0c000-08c27000 rwxp 00000000 00:00 0 
0ab1f000-0b5ae000 rwxp 00000000 00:00 0          [heap]
abec1000-ac2c2000 rwxp 00000000 00:00 0 
ac600000-ac621000 rwxp 00000000 00:00 0 
ac621000-ac700000 ---p 00000000 00:00 0 
ac716000-ac717000 ---p 00000000 00:00 0 
ac717000-acf17000 rwxp 00000000 00:00 0 
acf17000-b0f18000 rwxs 00000000 00:10 84821      /dev/shm/pulse-shm-3096478705
b0f18000-b0f19000 ---p 00000000 00:00 0 
b0f19000-b1719000 rwxp 00000000 00:00 0 
b179b000-b1833000 r-xp 00000000 08:01 1575887    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b1833000-b1834000 ---p 00000000 00:00 0 
b1834000-b2034000 rwxp 00000000 00:00 0 
b2034000-b2035000 ---p 00000000 00:00 0 
b2035000-b2835000 rwxp 00000000 00:00 0 
b2835000-b2836000 ---p 00000000 00:00 0 
b2836000-b3036000 rwxp 00000000 00:00 0 
b3036000-b3037000 ---p 00000000 00:00 0 
b3037000-b38b8000 rwxp 00000000 00:00 0 
b38b8000-b3944000 r-xp 00000000 08:01 1575886    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b3944000-b39cd000 r-xp 00000000 08:01 1062868    /usr/share/xbmc/addons/skin.confluence/fonts/DejaVuSans-Bold-Caps.ttf
b39cd000-b3a59000 r-xp 00000000 08:01 1575886    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b3a59000-b3ae5000 r-xp 00000000 08:01 1575886    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b3ae5000-b3b71000 r-xp 00000000 08:01 1575886    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b3b71000-b3bfd000 r-xp 00000000 08:01 1575886    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b3bfd000-b3c89000 r-xp 00000000 08:01 1575886    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b3c89000-b3d15000 r-xp 00000000 08:01 1575886    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b3d15000-b3da1000 r-xp 00000000 08:01 1575886    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b3da1000-b3e39000 r-xp 00000000 08:01 1575887    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b3e39000-b3ed1000 r-xp 00000000 08:01 1575887    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b3ed1000-b3f7e000 r-xp 00000000 08:01 1062869    /usr/share/xbmc/addons/skin.confluence/fonts/DefaultCaps.ttf
b3f7e000-b402b000 r-xp 00000000 08:01 1062869    /usr/share/xbmc/addons/skin.confluence/fonts/DefaultCaps.ttf
b402b000-b42d6000 rwxs 109658000 00:05 3616      /dev/dri/card0
b4336000-b43ce000 r-xp 00000000 08:01 1575887    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b43ce000-b447b000 r-xp 00000000 08:01 1062869    /usr/share/xbmc/addons/skin.confluence/fonts/DefaultCaps.ttf
b447b000-b4513000 r-xp 00000000 08:01 1575887    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4513000-b45ab000 r-xp 00000000 08:01 1575887    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b45ab000-b4fab000 rwxp 00000000 00:00 0 
b4fab000-b503d000 r-xp 00000000 08:01 1058921    /usr/lib/xbmc/system/ImageLib-i486-linux.so
b503d000-b5040000 r-xp 00091000 08:01 1058921    /usr/lib/xbmc/system/ImageLib-i486-linux.so
b5040000-b5044000 rwxp 00094000 08:01 1058921    /usr/lib/xbmc/system/ImageLib-i486-linux.so
b5044000-b548c000 rwxp 00000000 00:00 0 
b548c000-b56ec000 r-xp 00000000 08:01 791455     /usr/lib/dri/radeon_dri.so
b56ec000-b56f1000 r-xp 0025f000 08:01 791455     /usr/lib/dri/radeon_dri.so
b56f1000-b56f3000 rwxp 00264000 08:01 791455     /usr/lib/dri/radeon_dri.so
b56f3000-b571a000 rwxp 00000000 00:00 0 
b571a000-b5754000 rwxp 00000000 00:00 0 
b578a000-b57a0000 rwxs 10921e000 00:05 3616      /dev/dri/card0
b57a0000-b57b0000 rwxs 10920e000 00:05 3616      /dev/dri/card0
b57b0000-b57b1000 ---p 00000000 00:00 0 
b57b1000-b57c1000 rwxp 00000000 00:00 0 
b57c1000-b57d1000 rwxs 1091fe000 00:05 3616      /dev/dri/card0
b57d1000-b57d9000 r-xp 00000000 08:01 789297     /usr/lib/libXcursor.so.1.0.2
b57d9000-b57da000 r-xp 00007000 08:01 789297     /usr/lib/libXcursor.so.1.0.2
b57da000-b57db000 rwxp 00008000 08:01 789297     /usr/lib/libXcursor.so.1.0.2
b57e1000-b57e3000 rwxs 109234000 00:05 3616      /dev/dri/card0
b57e3000-b57e6000 r-xp 00000000 08:01 2621512    /lib/libdrm_radeon.so.1.0.0
b57e6000-b57e7000 r-xp 00002000 08:01 2621512    /lib/libdrm_radeon.so.1.0.0
b57e7000-b57e8000 rwxp 00003000 08:01 2621512    /lib/libdrm_radeon.so.1.0.0
b57e8000-b57f6000 r-xp 00000000 08:01 1058910    /usr/lib/xbmc/system/libcpluff-i486-linux.so
b57f6000-b57f7000 r-xp 0000d000 08:01 1058910    /usr/lib/xbmc/system/libcpluff-i486-linux.so
b57f7000-b57f8000 rwxp 0000e000 08:01 1058910    /usr/lib/xbmc/system/libcpluff-i486-linux.so
b57f8000-b5808000 r-xs 00000000 08:01 1191449    /usr/share/samba/valid.dat
b5808000-b580a000 r-xp 00000000 08:01 793039     /usr/lib/gconv/UTF-16.so
b580a000-b580b000 r-xp 00001000 08:01 793039     /usr/lib/gconv/UTF-16.so
b580b000-b580c000 rwxp 00002000 08:01 793039     /usr/lib/gconv/UTF-16.so
b580c000-b584b000 r-xp 00000000 08:01 794335     /usr/lib/locale/en_US.utf8/LC_CTYPE
b584b000-b5969000 r-xp 00000000 08:01 794334     /usr/lib/locale/en_US.utf8/LC_COLLATE
b5969000-b5989000 r-xs 00000000 08:01 1181104    /usr/share/samba/lowcase.dat
b5989000-b59a9000 r-xs 00000000 08:01 1191448    /usr/share/samba/upcase.dat
b59a9000-b59b0000 rwxp 00000000 00:00 0 
b59b0000-b59fb000 r-xp 00000000 08:01 789240     /usr/lib/libFLAC.so.8.2.0
b59fb000-b59fc000 r-xp 0004a000 08:01 789240     /usr/lib/libFLAC.so.8.2.0
b59fc000-b59fd000 rwxp 0004b000 08:01 789240     /usr/lib/libFLAC.so.8.2.0
b59fd000-b5a01000 r-xp 00000000 08:01 789301     /usr/lib/libXdmcp.so.6.0.0
b5a01000-b5a02000 r-xp 00003000 08:01 789301     /usr/lib/libXdmcp.so.6.0.0
b5a02000-b5a03000 rwxp 00004000 08:01 789301     /usr/lib/libXdmcp.so.6.0.0
b5a03000-b5a05000 r-xp 00000000 08:01 789290     /usr/lib/libXau.so.6.0.0
b5a05000-b5a06000 r-xp 00001000 08:01 789290     /usr/lib/libXau.so.6.0.0
b5a06000-b5a07000 rwxp 00002000 08:01 789290     /usr/lib/libXau.so.6.0.0
b5a07000-b5a08000 rwxp 00000000 00:00 0 
b5a08000-b5a0b000 r-xp 00000000 08:01 2621529    /lib/libgpg-error.so.0.4.0
b5a0b000-b5a0c000 r-xp 00002000 08:01 2621529    /lib/libgpg-error.so.0.4.0
b5a0c000-b5a0d000 rwxp 00003000 08:01 2621529    /lib/libgpg-error.so.0.4.0
b5a0d000-b5a1c000 r-xp 00000000 08:01 790202     /usr/lib/libtasn1.so.3.1.7
b5a1c000-b5a1d000 r-xp 0000e000 08:01 790202     /usr/lib/libtasn1.so.3.1.7
b5a1d000-b5a1e000 rwxp 0000f000 08:01 790202     /usr/lib/libtasn1.so.3.1.7Aborted (core dumped)
ron@laptop:~$ 

```

```
ron@laptop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-31-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 (Ubuntu 2.6.32-31.61-generic 2.6.32.32+drm33.14)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003df70000 (usable)
[    0.000000]  BIOS-e820: 000000003df70000 - 000000003df7f000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003df7f000 - 000000003df80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003df80000 - 000000003e000000 (reserved)
[    0.000000]  BIOS-e820: 000000004df80000 - 000000004e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x3df70 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DBFFF uncachable
[    0.000000]   DC000-DFFFF write-back
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 038000000 mask FFC000000 write-back
[    0.000000]   4 base 03C000000 mask FFE000000 write-back
[    0.000000]   5 base 04DF80000 mask FFFF80000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003df70000 (usable)
[    0.000000]  modified: 000000003df70000 - 000000003df7f000 (ACPI data)
[    0.000000]  modified: 000000003df7f000 - 000000003df80000 (ACPI NVS)
[    0.000000]  modified: 000000003df80000 - 000000003e000000 (reserved)
[    0.000000]  modified: 000000004df80000 - 000000004e000000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2e03b000 - 2e7d3049
[    0.000000] ACPI: RSDP 000f6bc0 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 3df7a625 0002C (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 3df7ef64 00074 (v01 COMPAQ 0818     06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 3df7a651 04913 (v01 COMPAQ     0818 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3df7ffc0 00040
[    0.000000] ACPI: BOOT 3df7efd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] 103MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e1ed8]    TEXT DATA BSS ==> [0000100000 - 00008e1ed8]
[    0.000000]   #4 [002e03b000 - 002e7d3049]          RAMDISK ==> [002e03b000 - 002e7d3049]
[    0.000000]   #5 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #6 [00008e2000 - 00008e5188]              BRK ==> [00008e2000 - 00008e5188]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003df70
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003df70
[    0.000000] On node 0 totalpages: 253707
[    0.000000] free_area_init_node: node 0, pgdat c079c940, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 207 pages used for memmap
[    0.000000]   HighMem zone: 26275 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 4e000000 (gap: 4e000000:b1f80000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 251724
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-31-generic root=UUID=b14c21f1-629a-447c-a0a1-d4a90b266d79 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5076160 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003df70)
[    0.000000] Memory: 984556k/1015232k available (4689k kernel code, 29664k reserved, 2121k data, 664k init, 105928k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a7000 - 0xc084d000   ( 664 kB)
[    0.000000]       .data : 0xc05947c7 - 0xc07a6f08   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05947c7   (4689 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2388.164 MHz processor.
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 4776.32 BogoMIPS (lpj=9552656)
[    0.004056] Security Framework initialized
[    0.004121] AppArmor: AppArmor initialized
[    0.004137] Mount-cache hash table entries: 512
[    0.004443] Initializing cgroup subsys ns
[    0.004454] Initializing cgroup subsys cpuacct
[    0.004462] Initializing cgroup subsys memory
[    0.004481] Initializing cgroup subsys devices
[    0.004490] Initializing cgroup subsys freezer
[    0.004497] Initializing cgroup subsys net_cls
[    0.004550] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004555] CPU: L2 cache: 512K
[    0.004559] CPU: Hyper-Threading is disabled
[    0.004568] mce: CPU supports 4 MCE banks
[    0.004609] Performance Events: no PMU driver, software events only.
[    0.004625] Checking 'hlt' instruction... OK.
[    0.021632] SMP alternatives: switching to UP code
[    0.036452] Freeing SMP alternatives: 19k freed
[    0.036501] ACPI: Core revision 20090903
[    0.056525] ACPI: setting ELCR to 0200 (from 0c20)
[    0.060021] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.060033] ftrace: allocating 21804 entries in 43 pages
[    0.064195] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.064204] weird, boot CPU (#0) not listed by the BIOS.
[    0.064207] SMP motherboard not detected.
[    0.064211] Local APIC not detected. Using dummy APIC emulation.
[    0.064214] SMP disabled
[    0.064576] Brought up 1 CPUs
[    0.064581] Total of 1 processors activated (4776.32 BogoMIPS).
[    0.064608] CPU0 attaching NULL sched-domain.
[    0.064864] devtmpfs: initialized
[    0.065505] regulator: core version 0.5
[    0.065554] Time:  9:47:16  Date: 04/17/11
[    0.065636] NET: Registered protocol family 16
[    0.065877] EISA bus registered
[    0.065897] ACPI: bus type pci registered
[    0.068271] PCI: PCI BIOS revision 2.10 entry at 0xfd86e, last bus=1
[    0.068275] PCI: Using configuration type 1 for base access
[    0.069842] bio: create slab <bio-0> at 0
[    0.070705] ACPI: EC: Look up EC in DSDT
[    0.109754] ACPI: Interpreter enabled
[    0.109762] ACPI: (supports S0 S3 S4 S5)
[    0.109792] ACPI: Using PIC for interrupt routing
[    0.180200] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.180444] ACPI: No dock devices found.
[    0.180806] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.180890] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xf4000000-0xf7ffffff]
[    0.180898] pci 0000:00:00.0: reg 14 32bit mmio pref: [0xf0600000-0xf0600fff]
[    0.180995] pci 0000:00:06.0: reg 10 io port: [0x8400-0x84ff]
[    0.181002] pci 0000:00:06.0: reg 14 32bit mmio: [0xf0014000-0xf0014fff]
[    0.181037] pci 0000:00:06.0: supports D1 D2
[    0.181041] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.181046] pci 0000:00:06.0: PME# disabled
[    0.181151] pci 0000:00:0a.0: reg 10 32bit mmio: [0xffbfe000-0xffbfefff]
[    0.181170] pci 0000:00:0a.0: supports D1 D2
[    0.181172] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.181177] pci 0000:00:0a.0: PME# disabled
[    0.181216] pci 0000:00:0a.1: reg 10 32bit mmio: [0xf0018000-0xf00187ff]
[    0.181224] pci 0000:00:0a.1: reg 14 32bit mmio: [0xf0010000-0xf0013fff]
[    0.181263] pci 0000:00:0a.1: PME# supported from D3hot
[    0.181268] pci 0000:00:0a.1: PME# disabled
[    0.181307] pci 0000:00:0b.0: reg 10 io port: [0x9000-0x90ff]
[    0.181315] pci 0000:00:0b.0: reg 14 32bit mmio: [0xf0018800-0xf00188ff]
[    0.181350] pci 0000:00:0b.0: supports D1 D2
[    0.181353] pci 0000:00:0b.0: PME# supported from D1 D2 D3hot D3cold
[    0.181358] pci 0000:00:0b.0: PME# disabled
[    0.181389] pci 0000:00:0c.0: reg 10 32bit mmio: [0xf0000000-0xf000ffff]
[    0.181396] pci 0000:00:0c.0: reg 14 io port: [0x8090-0x8097]
[    0.181430] pci 0000:00:0c.0: PME# supported from D3hot D3cold
[    0.181434] pci 0000:00:0c.0: PME# disabled
[    0.181482] pci 0000:00:10.0: reg 20 io port: [0x8080-0x808f]
[    0.181562] pci 0000:00:11.0: quirk: region 8000-803f claimed by ali7101 ACPI
[    0.181566] pci 0000:00:11.0: quirk: region 8040-805f claimed by ali7101 SMB
[    0.181600] pci 0000:00:13.0: reg 10 32bit mmio: [0xf0016000-0xf0016fff]
[    0.181638] pci 0000:00:13.0: supports D1 D2
[    0.181642] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot
[    0.181646] pci 0000:00:13.0: PME# disabled
[    0.181678] pci 0000:00:13.1: reg 10 32bit mmio: [0xf0017000-0xf0017fff]
[    0.181716] pci 0000:00:13.1: supports D1 D2
[    0.181719] pci 0000:00:13.1: PME# supported from D0 D1 D2 D3hot
[    0.181724] pci 0000:00:13.1: PME# disabled
[    0.181754] pci 0000:00:13.2: reg 10 32bit mmio: [0xf0018c00-0xf0018cff]
[    0.181792] pci 0000:00:13.2: supports D1 D2
[    0.181795] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.181799] pci 0000:00:13.2: PME# disabled
[    0.181873] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xf8000000-0xfbffffff]
[    0.181881] pci 0000:01:05.0: reg 14 io port: [0xa000-0xa0ff]
[    0.181888] pci 0000:01:05.0: reg 18 32bit mmio: [0xf0300000-0xf030ffff]
[    0.181905] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.181926] pci 0000:01:05.0: supports D1 D2
[    0.181963] pci 0000:00:01.0: bridge io port: [0xa000-0xafff]
[    0.181968] pci 0000:00:01.0: bridge 32bit mmio: [0xf0300000-0xf03fffff]
[    0.181974] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf8000000-0xfbffffff]
[    0.181998] pci_bus 0000:00: on NUMA node 0
[    0.182007] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.182116] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.184370] ACPI: PCI Interrupt Link [LNK0] (IRQs *5 6)
[    0.184545] ACPI: PCI Interrupt Link [LNK1] (IRQs 8 10) *11
[    0.184716] ACPI: PCI Interrupt Link [LNK2] (IRQs *10 12)
[    0.184886] ACPI: PCI Interrupt Link [LNK3] (IRQs 6 7 *11 13)
[    0.185081] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[    0.185288] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[    0.185485] ACPI: PCI Interrupt Link [LNK6] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[    0.185659] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
[    0.185828] ACPI: PCI Interrupt Link [LNK8] (IRQs 5) *0, disabled.
[    0.186042] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.186048] vgaarb: loaded
[    0.186286] SCSI subsystem initialized
[    0.186460] libata version 3.00 loaded.
[    0.186602] usbcore: registered new interface driver usbfs
[    0.186631] usbcore: registered new interface driver hub
[    0.186677] usbcore: registered new device driver usb
[    0.186929] ACPI: WMI: Mapper loaded
[    0.186933] PCI: Using ACPI for IRQ routing
[    0.187182] NetLabel: Initializing
[    0.187186] NetLabel:  domain hash size = 128
[    0.187188] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.187221] NetLabel:  unlabeled traffic allowed by default
[    0.187305] Switching to clocksource tsc
[    0.187997] AppArmor: AppArmor Filesystem Enabled
[    0.187997] pnp: PnP ACPI init
[    0.187997] ACPI: bus type pnp registered
[    0.318052] pnp: PnP ACPI: found 13 devices
[    0.318057] ACPI: ACPI bus type pnp unregistered
[    0.318065] PnPBIOS: Disabled by ACPI PNP
[    0.318096] system 00:07: ioport range 0x40b-0x40b has been reserved
[    0.318100] system 00:07: ioport range 0x480-0x48f has been reserved
[    0.318104] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.318108] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
[    0.318113] system 00:07: ioport range 0x8000-0x807f could not be reserved
[    0.318116] system 00:07: ioport range 0xf500-0xf503 has been reserved
[    0.318120] system 00:07: ioport range 0xf510-0xf513 has been reserved
[    0.318129] system 00:08: iomem range 0x0-0x9ffff could not be reserved
[    0.318135] system 00:08: iomem range 0xdc000-0xdffff could not be reserved
[    0.318139] system 00:08: iomem range 0xe0000-0xfffff could not be reserved
[    0.318143] system 00:08: iomem range 0x100000-0x3dffffff could not be reserved
[    0.318148] system 00:08: iomem range 0xfff80000-0xffffffff has been reserved
[    0.353037] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.353042] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.353048] pci 0000:00:01.0:   MEM window: 0xf0300000-0xf03fffff
[    0.353053] pci 0000:00:01.0:   PREFETCH window: 0xf8000000-0xfbffffff
[    0.353060] pci 0000:00:0a.0: CardBus bridge, secondary bus 0000:02
[    0.353063] pci 0000:00:0a.0:   IO window: 0x001000-0x0010ff
[    0.353068] pci 0000:00:0a.0:   IO window: 0x001400-0x0014ff
[    0.353073] pci 0000:00:0a.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.353078] pci 0000:00:0a.0:   MEM window: 0x54000000-0x57ffffff
[    0.353399] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[    0.353404] PCI: setting IRQ 10 as level-triggered
[    0.353411] pci 0000:00:0a.0: PCI INT A -> Link[LNK2] -> GSI 10 (level, low) -> IRQ 10
[    0.353421] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.353424] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.353428] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.353432] pci_bus 0000:01: resource 1 mem: [0xf0300000-0xf03fffff]
[    0.353435] pci_bus 0000:01: resource 2 pref mem [0xf8000000-0xfbffffff]
[    0.353439] pci_bus 0000:02: resource 0 io:  [0x1000-0x10ff]
[    0.353443] pci_bus 0000:02: resource 1 io:  [0x1400-0x14ff]
[    0.353446] pci_bus 0000:02: resource 2 pref mem [0x50000000-0x53ffffff]
[    0.353450] pci_bus 0000:02: resource 3 mem: [0x54000000-0x57ffffff]
[    0.353524] NET: Registered protocol family 2
[    0.353695] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.354298] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.356319] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.357716] TCP: Hash tables configured (established 131072 bind 65536)
[    0.357726] TCP reno registered
[    0.358037] NET: Registered protocol family 1
[    0.358103] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    0.792675] pci 0000:01:05.0: Boot video device
[    0.792879] Simple Boot Flag at 0x38 set to 0x1
[    0.793065] cpufreq-nforce2: No nForce2 chipset.
[    0.793114] Scanning for low memory corruption every 60 seconds
[    0.793334] audit: initializing netlink socket (disabled)
[    0.793359] type=2000 audit(1303033636.792:1): initialized
[    0.802893] Trying to unpack rootfs image as initramfs...
[    0.813265] highmem bounce pool size: 64 pages
[    0.813277] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.819329] VFS: Disk quotas dquot_6.5.2
[    0.819439] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.820390] fuse init (API version 7.13)
[    0.820530] msgmni has been set to 1717
[    0.825042] alg: No test for stdrng (krng)
[    0.825240] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.825248] io scheduler noop registered
[    0.825252] io scheduler anticipatory registered
[    0.825256] io scheduler deadline registered
[    0.825317] io scheduler cfq registered (default)
[    0.825532] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.825571] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.848872] ACPI: AC Adapter [AC] (on-line)
[    0.849056] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.849073] ACPI: Sleep Button [SLPB]
[    0.849143] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.849149] ACPI: Power Button [PWRB]
[    0.849219] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.850232] ACPI: Lid Switch [LID]
[    0.850387] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.850391] ACPI: Power Button [PWRF]
[    0.850466] input: Sleep Button as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input4
[    0.850470] ACPI: Sleep Button [SLPF]
[    0.850727] Marking TSC unstable due to TSC halts in idle
[    0.850800] processor LNXCPU:00: registered as cooling_device0
[    0.860879] Switching to clocksource acpi_pm
[    0.978696] thermal LNXTHERM:01: registered as thermal_zone0
[    0.978714] ACPI: Thermal Zone [TZ0] (25 C)
[    0.979465] ACPI: Invalid passive threshold
[    0.981156] thermal LNXTHERM:02: registered as thermal_zone1
[    0.981176] ACPI: Thermal Zone [TZ1] (30 C)
[    0.983978] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.984232] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.984393] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.984963] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.986609] brd: module loaded
[    0.987337] loop: module loaded
[    0.987535] input: Macintosh mouse button emulation as /devices/virtual/input/input5
[    0.987855] pata_acpi 0000:00:10.0: can't derive routing for PCI INT A
[    0.987948] pata_acpi 0000:00:10.0: setting latency timer to 64
[    0.987971] pata_acpi 0000:00:10.0: can't derive routing for PCI INT A
[    1.006717] isapnp: Scanning for PnP cards...
[    1.016953] Fixed MDIO Bus: probed
[    1.017019] PPP generic driver version 2.4.2
[    1.017187] tun: Universal TUN/TAP device driver, 1.6
[    1.017191] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.017373] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.068735] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 11
[    1.068744] PCI: setting IRQ 11 as level-triggered
[    1.068754] ehci_hcd 0000:00:13.2: PCI INT C -> Link[LNK3] -> GSI 11 (level, low) -> IRQ 11
[    1.068807] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.069000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    1.069094] ACPI: Battery Slot [BAT0] (battery absent)
[    1.092160] ehci_hcd 0000:00:13.2: irq 11, io mem 0xf0018c00
[    1.104130] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 0.95
[    1.104420] usb usb1: configuration #1 chosen from 1 choice
[    1.104479] hub 1-0:1.0: USB hub found
[    1.104503] hub 1-0:1.0: 5 ports detected
[    1.104639] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.104699] ohci_hcd 0000:00:13.0: PCI INT A -> Link[LNK3] -> GSI 11 (level, low) -> IRQ 11
[    1.104741] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.104827] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    1.104863] ohci_hcd 0000:00:13.0: irq 11, io mem 0xf0016000
[    2.010158] Freeing initrd memory: 7776k freed
[    2.117809] isapnp: No Plug & Play device found
[    2.118176] usb usb2: configuration #1 chosen from 1 choice
[    2.118262] hub 2-0:1.0: USB hub found
[    2.118296] hub 2-0:1.0: 3 ports detected
[    2.118425] ohci_hcd 0000:00:13.1: PCI INT B -> Link[LNK3] -> GSI 11 (level, low) -> IRQ 11
[    2.118467] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.118553] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.118594] ohci_hcd 0000:00:13.1: irq 11, io mem 0xf0017000
[    2.678187] usb usb3: configuration #1 chosen from 1 choice
[    2.678229] hub 3-0:1.0: USB hub found
[    2.678245] hub 3-0:1.0: 2 ports detected
[    2.678325] uhci_hcd: USB Universal Host Controller Interface driver
[    2.678523] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.680719] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.680735] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.681006] mice: PS/2 mouse device common for all mice
[    2.681321] rtc_cmos 00:02: RTC can wake from S4
[    2.681408] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.681444] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    2.681619] device-mapper: uevent: version 1.0.3
[    2.681860] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.681951] device-mapper: multipath: version 1.1.0 loaded
[    2.681956] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.682154] EISA: Probing bus 0 at eisa.0
[    2.682169] Cannot allocate resource for EISA slot 1
[    2.682204] Cannot allocate resource for EISA slot 8
[    2.682206] EISA: Detected 0 cards.
[    2.682343] cpuidle: using governor ladder
[    2.682416] cpuidle: using governor menu
[    2.683039] TCP cubic registered
[    2.683227] NET: Registered protocol family 10
[    2.683880] lo: Disabled Privacy Extensions
[    2.684438] NET: Registered protocol family 17
[    2.684557] Using IPI No-Shortcut mode
[    2.684752] PM: Resume from disk failed.
[    2.684776] registered taskstats version 1
[    2.685149]   Magic number: 7:453:778
[    2.685377] rtc_cmos 00:02: setting system clock to 2011-04-17 09:47:19 UTC (1303033639)
[    2.685383] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.685386] EDD information not available.
[    2.685497] Freeing unused kernel memory: 664k freed
[    2.686790] Write protecting the kernel text: 4692k
[    2.686829] Write protecting the kernel read-only data: 1844k
[    2.707469] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input6
[    2.708673] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[    2.735452] udev: starting version 151
[    2.952183] usb 2-3: new full speed USB device using ohci_hcd and address 2
[    3.157398] usb 2-3: configuration #1 chosen from 1 choice
[    3.183481] Floppy drive(s): fd0 is 1.44M
[    3.183771] pata_ali 0000:00:10.0: can't derive routing for PCI INT A
[    3.184290] scsi0 : pata_ali
[    3.185943] scsi1 : pata_ali
[    3.187416] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8080 irq 14
[    3.187422] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8088 irq 15
[    3.193124] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.193601] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[    3.193609] 8139cp 0000:00:0b.0: PCI INT A -> Link[LNK1] -> GSI 10 (level, low) -> IRQ 10
[    3.195020] eth0: RTL-8139C+ at 0xf80d2800, 00:0b:cd:c6:0a:ff, IRQ 10
[    3.196205] ohci1394 0000:00:0a.1: PCI INT A -> Link[LNK2] -> GSI 10 (level, low) -> IRQ 10
[    3.199540] FDC 0 is a post-1991 82077
[    3.253121] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[f0018000-f00187ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.358152] ata1.00: ATA-8: SAMSUNG HM160HC, LQ100-10, max UDMA/100
[    3.358159] ata1.00: 312581808 sectors, multi 16: LBA48 
[    3.374065] ata1.00: configured for UDMA/100
[    3.374316] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HC  LQ10 PQ: 0 ANSI: 5
[    3.374663] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.375318] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    3.375399] sd 0:0:0:0: [sda] Write Protect is off
[    3.375404] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.375444] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.375740]  sda: sda1 sda2 < sda5 sda6 >
[    3.412529] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.536318] ata2.00: ATAPI: DW-224E, A.0H, max MWDMA2
[    3.536349] ata2.00: WARNING: ATAPI DMA disabled for reliability issues.  It can be enabled
[    3.536352] ata2.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    3.552233] ata2.00: configured for MWDMA2
[    3.553622] scsi 1:0:0:0: CD-ROM            TEAC     DW-224E          A.0H PQ: 0 ANSI: 5
[    3.557096] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.557104] Uniform CD-ROM driver Revision: 3.20
[    3.557360] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.557506] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.569462] 8139too Fast Ethernet driver 0.9.28
[    3.967110] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.528339] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000bcd719dc6145a]
[   14.523187] Adding 1993720k swap on /dev/sda6.  Priority:-1 extents:1 across:1993720k 
[   14.626851] udev: starting version 151
[   14.800835] lp: driver loaded but no devices found
[   15.031533] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.149716] Linux agpgart interface v0.103
[   15.239942] agpgart-ati 0000:00:00.0: Ati IGP330/340/345/350/M chipset
[   15.244738] reserve_ram_pages_type failed 0x32fc5000-0x32fc6000, track 0x10, req 0x10
[   15.245307] reserve_ram_pages_type failed 0x32cf5000-0x32cf6000, track 0x10, req 0x10
[   15.245848] reserve_ram_pages_type failed 0x32e7a000-0x32e7b000, track 0x10, req 0x10
[   15.246389] reserve_ram_pages_type failed 0x32d08000-0x32d09000, track 0x10, req 0x10
[   15.246930] reserve_ram_pages_type failed 0x32fdd000-0x32fde000, track 0x10, req 0x10
[   15.247470] reserve_ram_pages_type failed 0x32fdc000-0x32fdd000, track 0x10, req 0x10
[   15.248516] parport_pc 00:09: reported by Plug and Play ACPI
[   15.248637] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   15.362300] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:08/LNXVIDEO:00/input/input7
[   15.362445] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.370128] reserve_ram_pages_type failed 0x32f72000-0x32f73000, track 0x10, req 0x10
[   15.370674] reserve_ram_pages_type failed 0x32ce8000-0x32ce9000, track 0x10, req 0x10
[   15.371214] reserve_ram_pages_type failed 0x32d1a000-0x32d1b000, track 0x10, req 0x10
[   15.371788] reserve_ram_pages_type failed 0x3247c000-0x3247d000, track 0x10, req 0x10
[   15.387531] lp0: using parport0 (interrupt-driven).
[   15.415052] reserve_ram_pages_type failed 0x324fa000-0x324fb000, track 0x10, req 0x10
[   15.415599] reserve_ram_pages_type failed 0x32480000-0x32481000, track 0x10, req 0x10
[   15.416270] reserve_ram_pages_type failed 0x32490000-0x32491000, track 0x10, req 0x10
[   15.416811] reserve_ram_pages_type failed 0x32ecc000-0x32ecd000, track 0x10, req 0x10
[   15.417351] reserve_ram_pages_type failed 0x32cfb000-0x32cfc000, track 0x10, req 0x10
[   15.417891] reserve_ram_pages_type failed 0x3250d000-0x3250e000, track 0x10, req 0x10
[   15.418432] reserve_ram_pages_type failed 0x32510000-0x32511000, track 0x10, req 0x10
[   15.466025] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[   15.570264] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xf4000000
[   15.570386] yenta_cardbus 0000:00:0a.0: CardBus bridge found [0e11:0056]
[   15.570405] yenta_cardbus 0000:00:0a.0: Enabling burst memory read transactions
[   15.570409] yenta_cardbus 0000:00:0a.0: Using CSCINT to route CSC interrupts to PCI
[   15.570412] yenta_cardbus 0000:00:0a.0: Routing CardBus interrupts to PCI
[   15.570418] yenta_cardbus 0000:00:0a.0: TI: mfunc 0x01001c00, devctl 0x64
[   15.686210] type=1505 audit(1303033652.498:2):  operation="profile_load" pid=491 name="/sbin/dhclient3"
[   15.686907] type=1505 audit(1303033652.498:3):  operation="profile_load" pid=491 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.687298] type=1505 audit(1303033652.498:4):  operation="profile_load" pid=491 name="/usr/lib/connman/scripts/dhclient-script"
[   15.720906] type=1505 audit(1303033652.534:5):  operation="profile_load" pid=521 name="/usr/sbin/ntpd"
[   15.785723] [drm] Initialized drm 1.1.0 20060810
[   15.800480] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x0038, PCI irq 10
[   15.800488] yenta_cardbus 0000:00:0a.0: Socket status: 30000020
[   15.837188] ppdev: user-space parallel port driver
[   16.214069] [drm] radeon defaulting to kernel modesetting.
[   16.214080] [drm] radeon kernel modesetting enabled.
[   16.214621] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 5
[   16.214626] PCI: setting IRQ 5 as level-triggered
[   16.214634] radeon 0000:01:05.0: PCI INT A -> Link[LNK0] -> GSI 5 (level, low) -> IRQ 5
[   16.237041] [drm] radeon: Initializing kernel modesetting.
[   16.249906] [drm] register mmio base: 0xF0300000
[   16.249913] [drm] register mmio size: 65536
[   16.250386] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   16.250428] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   16.250455] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   16.250513] radeon 0000:01:05.0: putting AGP V2 device into 4x mode
[   16.250519] [drm] radeon: VRAM 32M
[   16.250522] [drm] radeon: VRAM from 0x3E000000 to 0x3FFFFFFF
[   16.250524] [drm] radeon: GTT 64M
[   16.250527] [drm] radeon: GTT from 0x40000000 to 0x43FFFFFF
[   16.250567] [drm] radeon: irq initialized.
[   16.250786] [drm] Detected VRAM RAM=32M, BAR=64M
[   16.250793] [drm] RAM width 64bits DDR
[   16.253635] [TTM] Zone  kernel: Available graphics memory: 443848 kiB.
[   16.253642] [TTM] Zone highmem: Available graphics memory: 496812 kiB.
[   16.253721] [drm] radeon: 32M of VRAM memory ready
[   16.253726] [drm] radeon: 64M of GTT memory ready.
[   16.282035] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9d48b1, caps: 0x904713/0x4006
[   16.288867] [drm] radeon: cp idle (0x00008080)
[   16.289415] [drm] Loading R100 Microcode
[   16.290587] platform radeon_cp.0: firmware: requesting radeon/R100_cp.bin
[   16.329249] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   16.342709] [drm] radeon: ring at 0x0000000040000000
[   16.342739] [drm] ring test succeeded in 1 usecs
[   16.366899] [drm] radeon: ib pool ready.
[   16.367074] [drm] ib test succeeded in 0 usecs
[   16.368825] [drm] Panel ID String: SEC                     
[   16.368831] [drm] Panel Size 1024x768
[   16.370076] [drm] Default TV standard: NTSC
[   16.370082] [drm] 29.498928713 MHz TV ref clk
[   16.370091] [drm] Default TV standard: NTSC
[   16.370093] [drm] 29.498928713 MHz TV ref clk
[   16.370332] [drm] Radeon Display Connectors
[   16.370338] [drm] Connector 0:
[   16.370340] [drm]   VGA
[   16.370345] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   16.370348] [drm]   Encoders:
[   16.370350] [drm]     CRT1: INTERNAL_DAC1
[   16.370353] [drm] Connector 1:
[   16.370355] [drm]   LVDS
[   16.370359] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   16.370361] [drm]   Encoders:
[   16.370363] [drm]     LCD1: INTERNAL_LVDS
[   16.370366] [drm] Connector 2:
[   16.370368] [drm]   S-video
[   16.370370] [drm]   Encoders:
[   16.370372] [drm]     TV1: INTERNAL_DAC2
[   16.422425] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   16.444147] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   16.444210] pci 0000:02:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]
[   16.518533] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[   16.521376] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   16.522379] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   16.523317] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   16.529474] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   16.586966] cfg80211: Calling CRDA to update world regulatory domain
[   16.682690] cfg80211: World regulatory domain updated:
[   16.682698]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.682703]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.682707]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.682711]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.682714]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.682718]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.707075] ath5k 0000:02:00.0: enabling device (0000 -> 0002)
[   16.707100] ath5k 0000:02:00.0: PCI INT A -> Link[LNK2] -> GSI 10 (level, low) -> IRQ 10
[   16.707230] ath5k 0000:02:00.0: registered as 'phy0'
[   17.341098] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[   17.341108] ALI 5451 0000:00:06.0: PCI INT A -> Link[LNK7] -> GSI 5 (level, low) -> IRQ 5
[   17.430627] [drm] fb mappable at 0xF8040000
[   17.430633] [drm] vram apper at 0xF8000000
[   17.430636] [drm] size 786432
[   17.430638] [drm] fb depth is 8
[   17.430641] [drm]    pitch is 1024
[   17.436528] fb0: radeondrmfb frame buffer device
[   17.436534] registered panic notifier
[   17.436549] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   17.459145] vga16fb: initializing
[   17.459159] vga16fb: mapped to 0xc00a0000
[   17.459171] vga16fb: not registering due to another framebuffer present
[   17.631719] Console: switching to colour frame buffer device 128x48
[   17.745378] ath: EEPROM regdomain: 0x60
[   17.745386] ath: EEPROM indicates we should expect a direct regpair map
[   17.745394] ath: Country alpha2 being used: 00
[   17.745397] ath: Regpair used: 0x60
[   17.792466] phy0: Selected rate control algorithm 'minstrel'
[   17.793716] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   18.245243] type=1505 audit(1303033655.058:6):  operation="profile_load" pid=747 name="/usr/share/gdm/guest-session/Xsession"
[   18.278306] type=1505 audit(1303033655.090:7):  operation="profile_replace" pid=750 name="/sbin/dhclient3"
[   18.279039] type=1505 audit(1303033655.090:8):  operation="profile_replace" pid=750 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.279443] type=1505 audit(1303033655.090:9):  operation="profile_replace" pid=750 name="/usr/lib/connman/scripts/dhclient-script"
[   18.426802] type=1505 audit(1303033655.238:10):  operation="profile_load" pid=753 name="/usr/bin/evince"
[   18.959759] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.976223] eth0: link down
[   18.976507] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.496140] AC'97 1 does not respond - RESET
[   21.512148] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   21.512165] ali mixer 1 creating error.
[   49.938548] wlan0: deauthenticating from 00:1c:df:00:71:db by local choice (reason=3)
[   49.953223] wlan0: direct probe to AP 00:1c:df:00:71:db (try 1)
[   49.956473] wlan0: direct probe responded
[   49.956485] wlan0: authenticate with AP 00:1c:df:00:71:db (try 1)
[   49.958016] wlan0: authenticated
[   49.958076] wlan0: associate with AP 00:1c:df:00:71:db (try 1)
[   49.959953] wlan0: RX AssocResp from 00:1c:df:00:71:db (capab=0x411 status=0 aid=1)
[   49.959961] wlan0: associated
[   49.961768] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.668040] wlan0: no IPv6 routers present
[ 5385.064633] __ratelimit: 18 callbacks suppressed
[ 6095.098561] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 0
[ 6095.098575] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 6095.736840] xbmc.bin[5367]: segfault at e ip 05b468da sp bf97d35c error 4 in libc-2.11.1.so[5adb000+153000]
[ 6125.153060] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 0
[ 6125.153073] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 7043.148261] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 0
[ 7043.148274] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 7363.651389] [drm:r100_cs_track_texture_check] *ERROR* No texture bound to unit 0
[ 7363.651404] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
ron@laptop:~$ 

```

---

### Post by ronnielsen1 on 2011-04-17
No one out there with a radeon card?

---

### Post by Yellow Pasque on 2011-04-17
This is what I could find: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/533784](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/533784)

I suggest trying the newer, improved 3D driver (r300g) by using xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by ronnielsen1 on 2011-04-23
Thanks for the link. It helped me figure out what to do. It had a section that coincided with my problem

> Note: if you are getting "drmRadeonCmdBu
ffer: -22" this is another problem see [bug #557266]("https://bugs.launchpad.net/bugs/557266").


and gave me a link to a kernel patch I couldn't figure out but it did say 
> Note: this bug is fixed in kernel 2.6.36, but it's still not fixed in  the 2.6.35.x series (at least up to 2.6.35.10). To fix it in 2.6.35.x it  needs this kernel patch:

which led me to this page

> **Linux Kernel 2.6.36 installation guide for Ubuntu Linux**


[http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/](http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/)

which worked perfectly on getting me the new kernel and no more video problems. Thanks

---

