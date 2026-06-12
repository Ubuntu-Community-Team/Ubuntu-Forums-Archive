---
title: "Hdmi"
date: 2012-12-14
forum: Multimedia Software
---

### Post by kianoushkarbasi on 2012-12-14
Hi, my monitor is not working with hdmi details:

Samsung -  S24B350H

Lenovo T430 0 

NVIDIA NVS 5400M Graphics with Optimus Technology, 1GB DDR3 Memory

  *-display               
       description: VGA compatible controller
       product: GF108 [Quadro NVS 5400M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:5000(size=128) memory:f1000000-f107ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:6000(size=64)


Screen 0: minimum 320 x 200, current 3046 x 1050, maximum 8192 x 8192
LVDS2 connected 1366x768+0+282 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA2 connected 1680x1050+1366+0 (normal left inverted right x axis y axis) 459mm x 296mm
   1680x1050      59.9*+
   1680x945       60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1280x768       74.9     59.9  
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1

---

### Post by dannyboy79 on 2012-12-14
which nvidia driver are you using? have you looked at /var/log/Xorg.0.log for errors?

---

