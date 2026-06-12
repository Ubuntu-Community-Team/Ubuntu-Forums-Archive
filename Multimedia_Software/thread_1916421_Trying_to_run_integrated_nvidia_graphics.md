---
title: "Trying to run integrated nvidia graphics"
date: 2012-01-28
forum: Multimedia Software
---

### Post by Shifty99 on 2012-01-28
Hello all,

I am trying to configure my machine to run off of the integrated nvidia graphics card instead of the pci-e card I have plugged in. I don't play games on the machine and was hoping to use my 8800 GTS for some small scale CUDA work.

My details:
Gateway GT5654 w/ GeForce 6150SE nForce 430 (integrated)
Running Ubuntu 11.10
Discrete Graphics Card: GeForce 8800 GTS 512/PCI/SSE2

My progress: It doesn't seem that Ubuntu can find the integrated graphics. Evidence below...

mike@mike-desktop:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: G92 [GeForce 8800 GTS 512]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:e0000000-efffffff memory:f8000000-f9ffffff ioport:ac00(size=128) memory:fb000000-fb01ffff

mike@mike-desktop:~$ sudo lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GTS 512] (rev a2)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)

mike@mike-desktop:~$ sudo su root
root@mike-desktop:/home/mike# cat /proc/apci/wakeup
cat: /proc/apci/wakeup: No such file or directory
root@mike-desktop:/home/mike# cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
HUB0	  S5	*disabled  pci:0000:00:04.0
XVR0	  S5	*disabled  pci:0000:00:09.0
XVR1	  S5	*disabled  pci:0000:00:0b.0
XVR2	  S5	*disabled  pci:0000:00:0c.0
UAR1	  S5	*disabled  pnp:00:08
USB0	  S3	*disabled  pci:0000:00:02.0
USB2	  S3	*disabled  pci:0000:00:02.1
AZAD	  S5	*disabled  pci:0000:00:05.0
MMAC	  S5	*disabled  

It doesn't seem to be anywhere. I checked the BIOS settings as well. I did initially have the option set to boot the PCIEx video  first, but I have since disabled that, to no avail. If I can find/detect it, I would then try to modify the xorg.conf if I couldn't just adjust the graphics via nvidia-settings.

Any guidance would be much appreciated. Thanks!

---

