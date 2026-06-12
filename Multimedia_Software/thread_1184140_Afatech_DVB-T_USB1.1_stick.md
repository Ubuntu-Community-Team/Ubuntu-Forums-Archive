---
title: "Afatech DVB-T USB1.1 stick"
date: 2009-06-10
forum: Multimedia Software
---

### Post by DisasterEC on 2009-06-10
Hi,
I have a DVB USB dongle I am trying to get working with Mythbuntu, As you can see from the below dmesg it is not picking up the firmware. I have been google everywhere to see if anyone has a process for installing this device. Any help would be appriciate on the steps i need to take to get it to work. Also This is my first attempt on using ubuntu.

[    6.093383] dvb-usb: found a 'Afatech DVB-T USB1.1 stick' in cold state, will try to load a firmware
[    6.093387] usb 4-1: firmware: requesting af9005.fw
[    6.109460] dvb-usb: did not find the firmware file. (af9005.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)
[    6.109471] dvb_usb_af9005: probe of 4-1:1.0 failed with error -2
[    6.109493] usbcore: registered new interface driver dvb_usb_af9005

Also should advise I am running the below amd 64 bit hardware as you can see the dongle not being picked up

00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)
01:00.1 Display controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) (Secondary)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

Thanks

---

