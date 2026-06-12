---
title: "Dual monitor issues"
date: 2011-08-30
forum: Multimedia Software
---

### Post by beaversharkey on 2011-08-30
I am trying to connect a secondary monitor to my desktop, however is does not respond. I have tried 'detecting monitors' in monitor preferences but it is not detecting my (secondary) monitor. I am new to Linux (running 10.04 lucid) so it would be appreciated that if there are any technical steps they be written as in one of those "Linux for Dummies" books. Did a little resarch and both monitors are installed. Please let me know of any additional info you might need!



Looking through other forums I thought this information might help 

beaversharky@beaversharky-desktop:~$ hwinfo --gfxcard
20: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4153
  Unique ID: VCu0.XZKoWlkzw1D
  Parent ID: vSkL.X0yl1qhFqsB
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "ATI RV350 AS"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4153 "RV350 AS"
  SubVendor: pci 0x174b "PC Partner Limited"
  SubDevice: pci 0x0200 
  Driver: "radeon"
  Driver Modules: "drm"
  Memory Range: 0xe0000000-0xefffffff (rw,prefetchable)
  I/O Ports: 0xc800-0xc8ff (rw)
  Memory Range: 0xff8f0000-0xff8fffff (rw,non-prefetchable)
  Memory Range: 0xff8c0000-0xff8dffff (ro,prefetchable,disabled)
  IRQ: 16 (71408 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00004153sv0000174Bsd00000200bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: radeon
  Driver Info #1:
    XFree86 v4 Server Module: radeon
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

21: PCI 100.1: 0380 Display controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4173
  Unique ID: NXNs.YTY4Q11vPj0
  Parent ID: vSkL.X0yl1qhFqsB
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: graphics card
  Model: "ATI RV350 AS [Radeon 9550] (Secondary)"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4173 "RV350 AS [Radeon 9550] (Secondary)"
  SubVendor: pci 0x174b "PC Partner Limited"
  SubDevice: pci 0x0201 
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  Memory Range: 0xff8e0000-0xff8effff (rw,non-prefetchable)
  Module Alias: "pci:v00001002d00004173sv0000174Bsd00000201bc03sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

Primary display adapter: #20


Thanks!

---

### Post by LFA2711 on 2011-08-30
Are you hooking the monitor up when the primary computer is already running? This will not work, even if you press detect monitors. However there are other options.

1) Turn on and connect the monitor at startup

2) (a little trick that works for me) Start playing a video with Movie Player (should come with Ubuntu) and go into fullscreen.

---

