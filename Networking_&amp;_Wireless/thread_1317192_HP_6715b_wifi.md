---
title: "HP 6715b wifi"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by dt_matthews on 2009-11-06
Hi

I have just installed 64bit koala within windows to give it a go. All is impressive so far with exception of getting wifi working.

I *have* gone thru' the stickies to try and resolve the problem but no dice. I am a linux noob so humbly appreciate any guidance.

I have installed the 64bit driver (as output below) but no hardware is detected in any of the output (that I can determine anyway!)

Output from my system are below.

TIA, dan

--------------

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:5e:9c:32
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.09 ip=192.168.1.67 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:d0000000-d000ffff


-----------------

sudo ndiswrapper -l
bcmwl6 : driver installed

----------------

lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:04.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:7914]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
02:04.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b6)
02:04.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 02)
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
devuser@ubuntu:~$

---

### Post by t0mppa on 2009-11-06
Like you noticed, the system isn't detecting your card at all. Installing drivers won't help much, before you can get the interface to show up. Are you sure you simply haven't killed it through the hardware switch (usually a button or then a key combination, often FN + F5)?

---

### Post by dt_matthews on 2009-11-06
no, its activve (and is working fine in Win7).

I have however just tried a different driver, the ndiswrapper now detects a device (it gives an id) along with the driver installed, but the network manager still shows nothing for wireless. 

when i run

sudo ndiswrapper -l

i now get a message along lines ' each config file must have a .conf file'

I'll try and post the actual output in a bit but i'm in win7 at mo!

any thoughts?!

cheers,
dan

---

