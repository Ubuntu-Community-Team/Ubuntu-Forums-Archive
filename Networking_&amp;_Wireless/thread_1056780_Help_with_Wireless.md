---
title: "Help with Wireless"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by plinders on 2009-02-01
Hi,

I'm new here, but I'm not new with linux. I have used OpenSuSE 11.0 KDE 4 for quite some time, but for some reason it just died, and then I switched to Ubuntu Intrepid Ibex. In OpenSuSE I have managed to install my wireless dongle (Thomson SpeedTouch 121g)(USB interface), but in Ubuntu I haven't. My computer specs:

AMD Athlon XP 2500+ Processor
NVIDIA 6200 A-LE Videocard (drivers are installed)
250GB WD IDE Hard disk
1.75GB DDR Ram

I can get my drivers installed, and with various commands (ndiswrapper -l, lshw -C Network, lsusb, uname -m, uname -r, lsmod | grep ndis, dmesg | tail) I get the following:

```
Ndiswrapper -l:

bt4501g : driver installed 
	device (06B9:0121) present 

lshw -C Network:

PCI (sysfs)   
  *-network                
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 74 
       serial: 00:0c:6e:e2:73:f0 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 46:88:13:78:2a:ed 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 

lsusb:

Bus 007 Device 004: ID 06b9:0121 Alcatel Telecom SpeedTouch 121g Wireless Dongle 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 004: ID 045e:009d Microsoft Corp.  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 



uname -m:
i686

uname -r:
2.6.27-7-generic

lsmod | grep ndis:
ndiswrapper           196380  0  
usbcore               148848  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd 

dmesg | tail:
[  203.872047] usb 7-1: reset high speed USB device using ehci_hcd and address 4 
[  214.216314] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138A, count: 3, return_address: f9043fac 
[  214.216327] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xc0000001 
[  214.216331] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x6d695442 
[  214.216334] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x37 
[  224.316182] ndiswrapper (mp_init:219): couldn't initialize device: C0010006 
[  224.316199] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001) 
[  224.316218] ndiswrapper (mp_halt:262): device f5d4c480 is not initialized - not halting 
[  224.316223] ndiswrapper: device eth%d removed 
[  224.324111] ndiswrapper: probe of 7-1:1.0 failed with error -22 

```

I have used the comprehensive ndiswrapper guide on this forum ([http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)), but it didn't work for me

Can anyone help me?
Thanks in advance.
Plinders

---

