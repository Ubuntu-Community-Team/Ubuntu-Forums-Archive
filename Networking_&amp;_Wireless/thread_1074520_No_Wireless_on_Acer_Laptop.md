---
title: "No Wireless on Acer Laptop"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by sportscraz1 on 2009-02-19
Hi Everyone, 

I am new to ubuntu and just recently installed it, I have a Acer Laptop. The installation went somewhat good but the end result was no wireless. How do I fix this?

Would appreciate some feedback. 

John

---

### Post by insineratehymn on 2009-02-19
USB or onboard wireless?

---

### Post by binbash on 2009-02-19
paste the output of : 

sudo lshw

---

### Post by sportscraz1 on 2009-02-19
no expert here, hook up wirelessly (no usb), currently at work will reply later with results using that cmd.

---

### Post by sportscraz1 on 2009-02-19
description: Notebook
    product: Aspire 5520
    vendor: Acer
    version: V1.10
    serial: LXAJA0X0597461B5011601
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 uuid=66303861-3562-3131-6635-001B386CE607
  *-core
       description: Motherboard
       product: Fuquene
       vendor: Acer
       physical id: 0
       version: N/A
       serial: LXAJA0X0597461B5011601
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.10 (10/29/2007)
          size: 105KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot
     *-cpu:0
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-58
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.8.1
          slot: Socket A
          size: 1600MHz
          capacity: 1900MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-through
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: S1
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: S2
             size: 2GiB
             width: 64 bits
     *-cpu:1
          physical id: 5
          bus info: cpu@1
          version: 15.8.1
          size: 1600MHz
          capacity: 1600MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB

---

### Post by Ketara on 2009-02-19
I'm not seeing a wireless card there at all. Did you paste the entire thing?

Is the keyboard wireless on-off switch set to on?

---

### Post by Crafty Kisses on 2009-02-19
Post the results of these commands:
```
sudo lshw -C network
lspci
```

---

### Post by sportscraz1 on 2009-02-19
yes all was posted... the laptop is a dual boot machine (xp and ubuntu).. I am able to log on wireless with xp but not with ubuntu.. I will post those results of commands shortly. 

Thanks everyone for helping me.. I am definitely novice at linux.. practically just started with it.

---

### Post by sportscraz1 on 2009-02-19
carm@carm-laptop:~$ sudo lshw -c network
[sudo] password for carm: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:6c:e6:07
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:fe:b6:e3:e6:38
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by sportscraz1 on 2009-02-19
carm@carm-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
carm@carm-laptop:~$

---

### Post by Crafty Kisses on 2009-02-19
So this is the wireless card you have:
```
AR242x 802.11abg Wireless PCI Express Adapter
```
So let's see if we can't get it up and running. Here's what you want to do, you want to install ndiswrapper, you can install ndiswrapper by running the following:
```
sudo apt-get install ndiswrapper-common
```
Once you have that package you need to grab the XP driver, which you can get right [here.]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz") Once you have the XP driver, extract it and look for the .inf file, once you have found the .inf file, it should be called something like AR24x.inf, I'm just guessing, but running the following command, and remember to substitute the actual driver name:
```
sudo ndiswrapper -i AR24x.inf
```
Once you have done that, the driver should be installed, to make sure, you can run the following:
```
sudo ndiswrapper -l
```
If the drivers are installed correctly, you should get results similar to this:
```
Installed ndis drivers
driver present, hardware present
```
You're almost done, what you want to do now is load the ndiswrapper module, so run the following:
```
sudo modprobe ndiswrapper
```
So once the module is loaded, you want to make sure that module loads at every start up, so you can run the following:
```
sudo ndiswrapper -m
```
So there you have it, you have the modules, and the drivers. The last thing you need to do is blacklist any existing drivers, so there's no conflicts, so run the following:
```
sudo nano /etc/modprobe.d/blacklist
```
A text-file should pop up, once you see it, scroll down to the bottom and add these lines:
```
blacklist ath_pci
blacklist ath_hal
```
Then restart your computer by running the following:
```
sudo shutdown -r now
```
Once you're back into Ubuntu your wireless should be working.

---

### Post by rickyroger0907 on 2009-02-20
Hi, I think I pretty much have the same problem. I could and already install ndiswrapper, but the XP driver I got from the given link, after I extracted it, all I have is net5211.inf and ar5211.sys 
I'm really desperate. I mean, I went through a lot of posts showing different ways to get the wireless to work. Still, mine does do anything. By the way, I have a Aspire 4720Z, running Ubuntu 8.10 together with XP. Those commands that you showed, I can't get my computer to work with those. I tried to download packages (.deb) to install, it says wrong architecture (even though I got the i386). I hope you guys don't mind helping me out. 
Any needed info, I'll reply asap. Thanks in advance regardless of the result, appreciate the effort.

---

### Post by ellis rowell on 2009-03-23
I have the same problem. I have an Acer 5101AWLMi, the internal wireless network worked OK with Hardy but since installing Intrepid it does not work and I have to use an Asus USB adapter.

The output I get is:-

root@ellisrowell-laptop:/home/ellisrowell# lshw -c network
Framebuffer devices       
  *-network:0      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:a8:fe:68
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:11:2f:82:7e:8e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.2 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:19:7d:36:dd:db
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:2 DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: pan0
       serial: 36:1f:7b:6c:e6:3f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@ellisrowell-laptop:/home/ellisrowell#

---

