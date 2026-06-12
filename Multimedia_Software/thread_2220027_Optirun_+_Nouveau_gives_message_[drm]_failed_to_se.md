---
title: "Optirun + Nouveau gives message: [drm] failed to set drm interface version."
date: 2014-04-26
forum: Multimedia Software
---

### Post by rothloup on 2014-04-26
I've been struggling to get my secondary GPU on my Dell XPS L702X to work.  This laptop has a GeForce GT 555M nvidia card and Intel i915 integrated graphics with optimus switching.  I have optirun installed and when I run "optirun -vv glxgears" I get the following output shown below.

Everything I've read about nouveau implies that it supports this card, but can anyone confirm it?  

What does the error message "[drm] failed to set drm interface version." mean?  I've googled it for 2 days now and I can't find anything that I can use.  Can someone help?

Also, I had tried the proprietary drivers, but I was getting random crashes in any program that I ran using optirun.  So I'm switching back to nouveau hoping that it will be more stable.

kubuntu 14.04

```
rothloup@Rons-Linux-DellXPS-Laptop:~$ optirun -vv glxgears
[ 1414.637301] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 1414.638481] [DEBUG]optirun version 3.2.1 starting...
[ 1414.638557] [DEBUG]Active configuration:
[ 1414.638615] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 1414.638670] [DEBUG] X display: :8
[ 1414.638725] [DEBUG] LD_LIBRARY_PATH: 
[ 1414.638782] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 1414.638838] [DEBUG] Accel/display bridge: auto
[ 1414.638895] [DEBUG] VGL Compression: proxy
[ 1414.638950] [DEBUG] VGLrun extra options: 
[ 1414.639002] [DEBUG] Primus LD Path: /usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
[ 1414.639154] [DEBUG]Using auto-detected bridge virtualgl
[ 1415.354396] [INFO]Response: No - error: [XORG] (EE) NOUVEAU(0): [drm] failed to set drm interface version.

[ 1415.354447] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NOUVEAU(0): [drm] failed to set drm interface version.

[ 1415.354462] [DEBUG]Socket closed.
[ 1415.354501] [ERROR]Aborting because fallback start is disabled.
[ 1415.354515] [DEBUG]Killing all remaining processes.
rothloup@Rons-Linux-DellXPS-Laptop:~$ 
```


```
rothloup@Rons-Linux-DellXPS-Laptop:~$ lspci -k
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
        Subsystem: Dell Device 04b8
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
        Kernel driver in use: pcieport
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
        Subsystem: Dell Device 04b8
        Kernel driver in use: i915
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
        Subsystem: Dell Device 04b8
        Kernel driver in use: mei_me
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
        Subsystem: Dell Device 04b8
        Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
        Subsystem: Dell Device 04b8
        Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
        Kernel driver in use: pcieport
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
        Kernel driver in use: pcieport
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
        Kernel driver in use: pcieport
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
        Kernel driver in use: pcieport
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
        Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
        Subsystem: Dell Device 04b8
        Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
        Subsystem: Dell Device 04b8
        Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
        Subsystem: Dell Device 04b8
        Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
        Subsystem: Dell Device 04b8
01:00.0 VGA compatible controller: NVIDIA Corporation GF106M [GeForce GT 555M] (rev a1)
        Subsystem: Dell Device 04b8
        Kernel driver in use: nouveau
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak] (rev 34)
        Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN
        Kernel driver in use: iwlwifi
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
        Subsystem: Dell Device 04b8
        Kernel driver in use: xhci_hcd
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
        Subsystem: Dell Device 04b8
        Kernel driver in use: r8169
rothloup@Rons-Linux-DellXPS-Laptop:~$ 
```

---

