---
title: "Dual head without X (Intel 945GM)?"
date: 2011-06-18
forum: Multimedia Software
---

### Post by jhatfiel on 2011-06-18
Hello,

I'm running Ubuntu 11.04 on my laptop with an external monitor. The two displays work great in X, but I've been trying to figure out whether there's a way to get multiple screens to work in the console. (As opposed to both displaying the same thing, which is what they've always done outside of X.)

My understanding is that the way to achieve what I want is with two framebuffers. Right now, I've got one (/dev/fb0), and it's working well -- I can set the resolution properly with the "video=" boot parameter or with fbset, and programs that use the framebuffer run fine. But I haven't figured out how to end up with two framebuffers, each associated with its own display.

I'm not entirely sure I'm even on the right track, since a lot of these things seem to have changed in the last few years and so some of the (limited) info on the Web is probably outdated.

I'd greatly appreciate any info on whether this is possible with this hardware or any suggestions on how to go about it.

Some potentially relevant outputs:

hwinfo --gfxcard
```
09: PCI 02.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27a2
  Unique ID: _Znp.AyhgUXFyk41
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel 945 GM"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27a2 "945 GM"
  SubVendor: pci 0x1179 "Toshiba America Info Systems"
  SubDevice: pci 0xff10 
  Revision: 0x03
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xf0a00000-0xf0a7ffff (rw,non-prefetchable)
  I/O Ports: 0x1800-0x1807 (rw)
  Memory Range: 0xd0000000-0xdfffffff (ro,non-prefetchable)
  Memory Range: 0xf0b00000-0xf0b3ffff (rw,non-prefetchable)
  IRQ: 16 (3980 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d000027A2sv00001179sd0000FF10bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: intel
  Driver Info #1:
    XFree86 v4 Server Module: intel
    3D Support: yes
    Extensions: dri
  Config Status: cfg=new, avail=yes, need=no, active=unknown

10: PCI 02.1: 0380 Display controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_27a6
  Unique ID: ruGf.EeuYq4vjbr7
  SysFS ID: /devices/pci0000:00/0000:00:02.1
  SysFS BusID: 0000:00:02.1
  Hardware Class: graphics card
  Model: "Intel Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x27a6 "Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller"
  SubVendor: pci 0x1179 "Toshiba America Info Systems"
  SubDevice: pci 0xff10 
  Revision: 0x03
  Memory Range: 0xf0a80000-0xf0afffff (rw,non-prefetchable)
  Module Alias: "pci:v00008086d000027A6sv00001179sd0000FF10bc03sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #9
```

fbset -i
```
mode "1280x800"
    geometry 1280 800 1280 800 32
    timings 0 0 0 0 0 0 0
    accel true
    rgba 8/16,8/8,8/0,0/0
endmode

Frame buffer device information:
    Name        : inteldrmfb
    Address     : 0xd0020000
    Size        : 4096000
    Type        : PACKED PIXELS
    Visual      : TRUECOLOR
    XPanStep    : 1
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 5120
    Accelerator : No

```
Thanks!

---

