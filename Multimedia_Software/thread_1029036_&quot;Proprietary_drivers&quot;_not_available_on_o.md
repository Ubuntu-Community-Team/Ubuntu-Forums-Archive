---
title: "&quot;Proprietary drivers&quot; not available on one of two matching laptops and Hardy installs"
date: 2009-01-03
forum: Multimedia Software
---

### Post by bdk on 2009-01-03
Greets.... I've got two laptops, both are nearly identical HP dv6700s. Both have GeForce 8400M GS video cards:

My lshw:
```
 *-display
     description: VGA compatible controller
     product: GeForce 8400M GS
     vendor: nVidia Corporation
     physical id: 0
     bus info: pci@0000:01:00.0
     version: a1
     width: 64 bits
     clock: 33MHz
     capabilities: pm msi pciexpress vga_controller bus_master cap_list
     configuration: driver=nvidia latency=0 module=nvidia
```

The Wifes lshw:
```
 *-display UNCLAIMED
     description: VGA compatible controller
     product: GeForce 8400M GS
     vendor: nVidia Corporation
     physical id: 0
     bus info: pci@0000:01:00.0
     version: a1
     width: 64 bits
     clock: 33MHz
     capabilities: pm msi pciexpress vga_controller bus_master cap_list
     configuration: latency=0
```

My lspci | grep -i nvidia:
```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
```

The Wife's lspci | grep -i nvidia:
```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
```

My lsmod | grep -i nvidia:
```
nvidia               8860260  26 
i2c_core               29440  1 nvidia
```

The Wife's lsmod | grep -i nvidia:
```
(Nothing)
```

I can tell that I need to load/install the modules on my Wife's laptop, but I'm not sure which ones and why my her 'Proprietary Drivers' window is blank unlike mine which lists "NVIDIA accelerated graphics driver (latest cards)" as enabled.

How do I get Ubuntu to recognize that there is a piece of hardware that it can get a proprietary driver for or rediscover the hardware?

Both are running Hardy Heron x64 with the 2.6.24-22-rt Kernel on Intel Core2Duo's. All packages are up to date. I'd like to find the Ubuntu fix and not use the driver from Nvidia (Unless that was the one that was installed for me when I told it to), I'd rather not have her learn to recompile the video drivers each time she gets a kernel update. 

*-bdk*

---

