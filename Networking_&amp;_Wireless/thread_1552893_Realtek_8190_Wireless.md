---
title: "Realtek 8190 Wireless"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by gordysc on 2010-08-14
Okay, so I have a Gateway DX4300-15e, and have been spending the better portion of the last 3 days trying to get the wireless working on Ubuntu 10.04 LTS (Lucid Lynx).  I've checked out a lot of the threads on this forum (props to chilli btw for that great post), but feel I'm missing something stupidly small.  It's a Realtek 8190 pci wireless card, but from the forums, I believe it should be able to use the 8192se driver.  The machine uses an AMD64, and I tried ndiswrapper.  However, it freezes if I try to use the WinXP64 driver (and will continuously freeze on reboot until I remove it).  The Vista64 and and Win7 64 drivers show the hardward present, but I cannot see the network card in ifconfig/iwconfig (did depmod -a, modprobe ndiswrapper, yada yada).  I've tried building the driver using several different versions of the 8192se, but the interface still does not show up on iwconfig/ifconfig after I run modprobe.  Here is some of the information about the machine:

lshw -C network

  *-network
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 16
       serial: 90:fb:a6:29:fb:6e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.1.3 latency=0 multicast=yes
       resources: irq:29 memory:fe9fc000-fe9fffff ioport:d800(size=256) memory:fe9c0000-fe9dffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:05:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:e800(size=256) memory:febff000-febfffff


lspci -nnk

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
	Kernel modules: shpchp
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] [1002:4390]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
	Kernel driver in use: ohci_hcd
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
	Kernel driver in use: ohci_hcd
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
	Kernel driver in use: ehci_hcd
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
	Kernel driver in use: ohci_hcd
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
	Kernel driver in use: ohci_hcd
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
	Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
	Kernel driver in use: ohci_hcd
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
	Kernel modules: amd64_edac_mod
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3200 Graphics [1002:9610]
	Kernel driver in use: radeon
	Kernel modules: radeon
01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Juniper [Radeon HD 5700 Series] [1002:68b8]
02:00.1 Audio device [0403]: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series] [1002:aa58]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 16)
	Kernel driver in use: sky2
	Kernel modules: sky2
04:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380]
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394
05:05.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8190]

(just curious, shouldn't the driver show up here under Realtek? Like the kernel driver/module...)


modinfo r8192se_pci

filename:       /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/r8192se_pci.ko
license:        GPL
version:        V 1.1
author:         Copyright(c) 2008 - 2010 Realtek Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     E6BB9E3AF632F94D486286F
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)

What bothers me about this is I don't see the Realtek 8190 listed as an alias, but I'm assuming from the description "Linux driver for Realtek RTL819x WiFi cards", that I should be okay with this.

uname -r
2.6.32-21-generic

ifconfig wlan0
wlan0: error fetching interface information: Device not found


Any ideas or tips of things to try would be much appreciated. I refuse to give up on this.

---

### Post by gordysc on 2010-08-14
Just a follow up for 2 things.

If anyone was curious about chilli's solution (it's really really helpful), that can be found here:
[http://ubuntuforums.org/archive/index.php/t-1329254.html](http://ubuntuforums.org/archive/index.php/t-1329254.html)

I noticed the card is not supported in install system at:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek) (I'm assuming 819x instead of 8192...), however I've seen several others have success with x86 architectures...still investigating.

---

### Post by gordysc on 2010-08-14
Okay, trying the ndiswrapper trouble shooting guide.  At check #5 for if it's not working, I got for the Vista64 driver:

dmesg | grep -e ndis -e wlan


[ 6737.960177] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 6738.069733] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 6738.069753] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 6738.069781] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 6738.069796] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 6738.069815] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 6738.069853] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 6738.069887] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 6738.069902] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 6738.069916] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 6738.069930] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 6738.069951] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 6738.069973] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 6738.070045] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[ 6738.070065] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 6738.070085] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[ 6738.070105] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 6738.070125] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 6738.070145] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 6738.070164] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[ 6738.070184] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 6738.070204] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 6738.070223] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 6738.070241] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 6738.070260] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 6738.070287] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 6738.070306] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 6738.070332] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 6738.070347] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net819xp'
[ 6738.070989] ndiswrapper (load_wrap_driver:108): couldn't load driver net819xp; check system log for messages from 'loadndisdriver'
[ 6738.071119] usbcore: registered new interface driver ndiswrapper


So it looks like it doesn't like the current driver...although I'm really bothered by the "usbcore" if it's a pci card...

I tried the Win7 driver, rebooted, and now get:


dmesg | grep -e ndis -e wlan

[    8.239022] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[    8.501589] usbcore: registered new interface driver ndiswrapper


However, it is still unclaimed if I do lshw -C network:

*-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:05:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:e800(size=256) memory:febff000-febfffff


Running lsmod | grep ndis, I get
ndiswrapper           244768  0

Just to check, I ran ndiswrapper -v and got
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-21-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.32-21-generic SMP mod_unload modversions 


Will double check BIOS to make sure it's not disabled...after that, I have no ideas.  Anyone?

---

### Post by wep940 on 2011-05-18
I did find the following thread for making a 8192se work - and it appears it worked for people with a 8172 as well, so it may be worth a shot:
 
[http://ubuntuforums.org/archive/index.php/t-1329254.html](http://ubuntuforums.org/archive/index.php/t-1329254.html)
 
Note that the instructions there are dependant on knowing your kernel version.  If you need help with this post back and I'll see if I can't come with instructions based on your current kernel.

---

### Post by ammon on 2012-04-22
n

---

### Post by sffvba[e0rt on 2012-04-22
Old thread closed.


404

---

