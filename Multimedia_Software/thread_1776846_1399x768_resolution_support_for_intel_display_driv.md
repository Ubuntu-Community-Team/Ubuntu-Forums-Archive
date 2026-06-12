---
title: "1399x768 resolution support for intel display driver"
date: 2011-06-06
forum: Multimedia Software
---

### Post by abdulrehman.ansari on 2011-06-06
i need to adjust my screen resolution to 1399x768, here are some details from my system:

rehman@army:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9 

the near option for me is 1024x768 but still it is very ugly on my screen.


rehman@army:~$ lspci | grep -i "vga"
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)


rehman@army:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:fd800000-fdbfffff memory:d0000000-dfffffff ioport:ff00(size=8)



rehman@army:/etc$ cat lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

(actually i am using kubuntu, but still it is showing ubuntu)


rehman@army:/etc$ uname -r
2.6.38-8-generic

let me know if any other information that i can give.

---

