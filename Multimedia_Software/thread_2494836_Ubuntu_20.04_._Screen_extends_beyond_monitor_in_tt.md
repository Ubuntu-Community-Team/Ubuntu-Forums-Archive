---
title: "Ubuntu 20.04 . Screen extends beyond monitor in tty/console mode"
date: 2024-01-28
forum: Multimedia Software
---

### Post by eugenedr on 2024-01-28
Adter upgrading to 20.04 the default resolution of 1920x1080 makes screen window extend beyond my monitor
I can switch to a lower resolution in the graphic mode (1680x1050 works fine for me) but cannot figure out how to change the resolution or screen size in tty (or console) mode as well as recovery console . 
I tried to set in /etc/default/grub with
```
*GRUB_GFXMODE=1280x1024*
```
line but even with the lower resoltion the console window extends beyond monitor in both horizontal and vertical directions.
I don't observe the problem when connect to another smaller monitor.
Attempt to change font through  sudo dpkg-reconfigure console-setup , couldn't resolve the problem either.
Any suggestions on what else I should look into?


It is a bit oldish desktop box which nevertheless performs fine for the tasks it is used for. Video cars is Intel. Connection to the monitor over HDMI


output of lshw command for graphics




```

sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:33 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff

```

output of hwinfo command for graphics


```

sudo hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.459]
  Unique ID: rdCR.QgFYtsmQZBC
  Hardware Class: framebuffer
  Model: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  SubVendor: "Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 255 MB + 960 kB
  Memory Range: 0x00000000-0x0ffeffff (rw)
  Mode 0x033c: 1920x1440 (+1920), 8 bits
  Mode 0x034d: 1920x1440 (+3840), 16 bits
  Mode 0x035c: 1920x1440 (+7680), 24 bits
  Mode 0x033a: 1600x1200 (+1600), 8 bits
  Mode 0x034b: 1600x1200 (+3200), 16 bits
  Mode 0x035a: 1600x1200 (+6400), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x037d: 0x0 (+0), 8 bits
  Mode 0x037e: 0x0 (+0), 16 bits
  Mode 0x037f: 0x0 (+0), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by eugenedr on 2024-01-28
got it solved with the answer here
[https://askubuntu.com/questions/1501626/ubuntu-20-04-screen-extends-beyond-monitor-in-tty-console-mode#comment2631990_1501626](https://askubuntu.com/questions/1501626/ubuntu-20-04-screen-extends-beyond-monitor-in-tty-console-mode#comment2631990_1501626)
sorry for crossposting

---

