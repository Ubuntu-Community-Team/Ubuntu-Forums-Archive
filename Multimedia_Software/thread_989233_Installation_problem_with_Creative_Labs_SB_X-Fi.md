---
title: "Installation problem with: Creative Labs SB X-Fi"
date: 2008-11-21
forum: Multimedia Software
---

### Post by Linendail on 2008-11-21
Hi!

I updated my Kubuntu installation to 8.10, and can't seem to install my Creative Labs SB X-Fi Extreme Gamer soundcard. I've downloaded the OS drivers provided by Creative, and run the installer - but it fails.

I get an error code at the beginning of the installation saying:
*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

And the driver fails to compile. What do I need to do, for it to compile properly? Thanks in advance.


Here's my result for lspci, in case it's of any use.
```

00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
02:07.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
02:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
02:0a.0 Multimedia audio controller: Creative Labs SB X-Fi

```

---

### Post by boblemur on 2008-12-22
the reason why it dosent compile is because it is trying to use an outdated constant that is now not found in new c header files.


START COPY PASTE:

edit file LinuxSys.c: vi src/ossrv/LinuxSys.c
Goto line 648 and replace SA_SHIRQ with IRQF_SHARED (Kernel 2.6.22 has told us that it was going to deprecate it although still defines it, but in kernel 2.6.25 this SA_SHIRQ is now gone!)
Add the following line after line 33:

#include <linux/fs.h> // for definitions of filp_*
Add the following lines after line 37:

#include <asm-generic/fcntl.h> // otherwise, some MACROS are undefined


Compile with the following command: sudo make KBUILD_NOPEDANTIC=1 or modify (temporarily!) file /usr/src/linux/scripts/Makefile.build and comment out statements around line 46 as below:

#ifeq ($(KBUILD_NOPEDANTIC),)
#ifneq ("$(save-cflags)","$(CFLAGS)")
#$(error CFLAGS was changed in "$(kbuild-file)". Fix it to use EXTRA_CFLAGS)
#endif

Edit file in drivers/ctsound and change the order to:

drivers="ctossrv emupia ctsfman haxfi ctalsa ct20xut ctexfifx cthwiut"

#endif
Install it: sudo make install


END COPY PASTE

this lets the driver compile for me on hardy, so you shouldnt have an issue, however apparently you need to rebuild ur kernel with a few changes and then rebuild it for it to work well....its on the ubuntu forums somewhere...

---

