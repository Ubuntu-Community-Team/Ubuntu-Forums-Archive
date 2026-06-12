---
title: "HDMI Output not working on second screen"
date: 2015-07-08
forum: Multimedia Software
---

### Post by pbrobyn on 2015-07-08
Hi Guys,
I'm hoping someone can help cause I've been going crazy trying to figure this out. I have 2 Dell Vostro laptops, they seem identical (they are the same model) however I think they have different display drivers. I have both running ubuntu 14.4, however the HDMI out is only working on one of them. The one that is using an integrated graphics controller works fine, the other seems to be using the integrated controller and an Nvidia controller, I've looked through the BIOS of both systems and system 1 states the video driver is the integrated driver and system 2 states it's an Nvidia driver. I have seen suggestions that this is a dual driver and it can be disabled in the BIOS however there is no option to do this on either system.
On the system where the HDMI output isn't working the second display is detected by Ubuntu but no picture appears on the TV, if I cycle through FN+F8 it changes the output settings of the laptop but still no picture on the TV. Cable and TV both work fine with one laptop so I can only assume it's something to do with the laptop/setup.

Below are the details is I use lspci -vnn | grep -i VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:044e]
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at fa400000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f080 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Dell Device [1028:0441]
    Flags: bus master, fast devsel, latency 0, IRQ 47
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218M [GeForce 310M] [10de:0a75] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:044e]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at fa000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

01:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be3] (rev a1)
    Subsystem: Dell Device [1028:044e]


If I use xrand I get the following;
LVDS1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected (normal left inverted right x axis y axis)
   1280x720       50.0 +   60.0     59.9  
   1920x1080      60.0     50.0     50.0     59.9  
   1920x1080i     60.1     50.0     60.0  
   1440x576i      50.1  
   1440x480i      60.1     60.1  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        60.0     59.9  
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

Not sure what other info would be needed as I have to admit I'm a bit of a noob and I really don't know what I'm doing so please keep this in mind when responding, any help would be really appreciated.

---

### Post by TheFu on 2015-07-09
I'd try **lxrandr**. Simple interface. Make certain the HDMI is enabled (checked).  For monitors, I've never had sync issues, but with some projectors, force the HDMI to be 60hz - nothing else.

---

### Post by pbrobyn on 2015-07-09
Tried lxrandr, it detects the HDMI out but still no output on the TV. HDMI was enabled and tried different resolutions and refresh settings still no picture.

---

### Post by TheFu on 2015-07-09
Could the HDMI plug be broke?

Last step is to compare the drivers and settings on both machines.
**sudo lshw -C video**

---

### Post by pbrobyn on 2015-07-10
I'm not sure how to test the HDMI plug, I haven't used it in quite a long time but it has worked previously when I had windows running - is there some way to test it?

Out put of **sudo lshw -C video **below;
**System 1 (HDMI working)**
*-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:fac00000-faffffff memory:c0000000-cfffffff ioport:f0e0(size=8)

**System 2 (HDMI not working)**
*-display               
       description: VGA compatible controller
       product: GT218M [GeForce 310M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f9000000-f9ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fa000000-fa07ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 18
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:fa400000-fa7fffff memory:b0000000-bfffffff ioport:f080(size=8)

---

### Post by dino99 on 2015-07-10
which nvidia driver is installed ?

---

### Post by pbrobyn on 2015-07-10
I had tried a few different drivers without luck so deleted all the previous drivers. I ran nvidia-current for this which according to additional drivers is **NVIDIA legacy binary driver - version 304.125 from nvidia-304 (open source)**

---

