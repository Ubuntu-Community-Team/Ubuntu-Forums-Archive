---
title: "Dynex Wireless G USB Dongle - NDISWrapper Issues"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by Dragnerok X on 2010-12-10
I'm trying my to get my 3-year-old Dynex wireless dongle to work in Ubuntu 10.04 (64-bit).

Borrowing a similar linksys adapter from another computer running Ubuntu, I was able to install NDISGTK and transfer the same drivers that work in my 64-bit Windows 7 installation into my home folder. 

Despite the fact that the dongle does not appear at all using lshw -C Network, ndiswrapper -l indicates that the driver is installed and the device is present.

I think I found something interesting, though, when I tried this command:

```
  [FONT=&quot]jimmy@ubuntu:~$ dmesg | grep -e ndis -e wlan[/FONT]
  [FONT=&quot][    9.321323] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)[/FONT]
  [FONT=&quot][   10.021542] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'[/FONT]
  [FONT=&quot][   10.021549] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'[/FONT]
  [FONT=&quot][   10.021554] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'[/FONT]
  [FONT=&quot][   10.021558] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'[/FONT]
  [FONT=&quot][   10.021562] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'[/FONT]
  [FONT=&quot][   10.021567] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'[/FONT]
  [FONT=&quot][   10.021571] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'[/FONT]
  [FONT=&quot][   10.021575] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'[/FONT]
  [FONT=&quot][   10.021580] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'[/FONT]
  [FONT=&quot][   10.021585] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'[/FONT]
  [FONT=&quot][   10.021602] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'[/FONT]
  [FONT=&quot][   10.021607] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'[/FONT]
  [FONT=&quot][   10.021611] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'[/FONT]
  [FONT=&quot][   10.021622] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'[/FONT]
  [FONT=&quot][   10.021626] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'[/FONT]
  [FONT=&quot][   10.021630] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'[/FONT]
  [FONT=&quot][   10.021637] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'[/FONT]
  [FONT=&quot][   10.021643] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'[/FONT]
  [FONT=&quot][   10.021648] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'[/FONT]
  [FONT=&quot][   10.021652] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'[/FONT]
  [FONT=&quot][   10.021657] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'[/FONT]
  [FONT=&quot][   10.021664] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'[/FONT]
  [FONT=&quot][   10.021668] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'[/FONT]
  [FONT=&quot][   10.021670] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmusbdhd'[/FONT]
  [FONT=&quot][   10.022017] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmusbdhd; check system log for messages from 'loadndisdriver'[/FONT]
  [FONT=&quot][   10.022065] usbcore: registered new interface driver ndiswrapper[/FONT]
  
```What do you think?

---

### Post by walt.smith1960 on 2010-12-11
Any idea what chipset your Dynex uses? In a terminal type LSUSB.   Did you try just booting with the device installed without NDISwrapper?  Chipsets that have been around for a while often have decent native support.

---

### Post by bkratz on 2010-12-11
You may have very little luck, ndiswrapper really only works well with XP drivers.

---

### Post by Dragnerok X on 2010-12-11
> **walt.smith1960 said:**
> Any idea what chipset your Dynex uses? In a terminal type LSUSB.   Did you try just booting with the device installed without NDISwrapper?  Chipsets that have been around for a while often have decent native support.

```
  [FONT=&quot]jimmy@ubuntu:~$ lsusb[/FONT]
  [FONT=&quot]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  [FONT=&quot]Bus 004 Device 003: ID 046d:c313 Logitech, Inc. [/FONT]
  [FONT=&quot]Bus 004 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse[/FONT]
  [FONT=&quot]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  [FONT=&quot]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  [FONT=&quot]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  [FONT=&quot]Bus 001 Device 004: ID 4317:0721[/FONT]
  [FONT=&quot]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
```
I did boot into Ubuntu once or twice prior to installing NDISwrapper, but all that Ubuntu ever natively detected was my motherboard's built-in ethernet connection.

---

### Post by walt.smith1960 on 2010-12-12
googling the device I.D. doesn't show what chip set the Dynex device uses which makes it tough.  I faced a problem similar to yours; I bought an Engenius USB device from Amazon because it was advertised to "work with Linux".  Well, not really.  The device used a ralink 3572(?) chip.  it was supposed to work with Linux by downloading and compiling the driver.   Chili555 gave me some advice but I ran out of patience.  Never could get it to work, either using the native driver or NDISwrapper.   I bought a NetGear WNA1100 which uses an Atheros 9K chipset.  It was not recognized immediately but with an installer from SourceForge, the Netgear works great with minimal fussing.  I also got a RealTek 8192SU chipset-based device (TrendNet TEW-649UB) to work with minimal fussing--just download & copy a firmware file to a specific location. The TrendNet  is nice for laptops--only sticks out about 1"(25mm).   Both devices are recognized out-of-box by 11.04 alpha1. If you search under my user name back a few months you can find the file names & procedure required for 10.04 & 10.10.

I've learned to do a little research before buying hardware for Linux machines.  If I find hardware that's interesting but doesn't have Linux support from the manufacturer, I write and tell that manufacturer why I bought their competitors' product.  If enough people do this maybe there will be better Linux hardware support.  Sorry I don't have a solution for the Dynex device.

---

