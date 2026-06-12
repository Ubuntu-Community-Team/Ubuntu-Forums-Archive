---
title: "D-Link WUA-2340 Wireless USB Adapter (Atheros chipset) 64 bit, ndiswrapper"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by Mark20 on 2011-09-14
Hi all,

I'm running Ubuntu 9.10 karmic (64 bit) and I'm having trouble getting my D-Link WUA-2340 wireless USB adapter to work.  The USB adapter uses an Atheros AR5523 chipset, lsusb output below:
```

Bus 002 Device 003: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 002 Device 002: ID 046d:c316 Logitech, Inc. HID-Compliant Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 004: ID 07d1:3a08 D-Link System predator Bootloader Download**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I've tried both the stock version of ndiswrapper, as well as the latest experimental version (1.57rc1).  

Of the 4 windows driver releases on the D-Link website only the two most recent zip files contained (Vista) 64 bit drivers, I've tried both 64 bit drivers, neither work.

In all cases I see the output below from dmesg:
```

[ 2704.001566] ndiswrapper version 1.57rc1 loaded (smp=yes, preempt=no)
[ 2704.130023] usb 1-3: reset high speed USB device using ehci_hcd and address 5
[ 2704.283993] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[ 2704.284000] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[ 2704.284006] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[ 2704.284030] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 2704.284036] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 2704.284048] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 2704.284054] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[ 2704.284061] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 2704.284066] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[ 2704.284072] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 2704.284078] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[ 2704.284085] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 2704.284098] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 2704.284104] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 2704.284110] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 2704.284118] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 2704.284124] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 2704.284129] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 2704.284152] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 2704.284160] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 2704.284170] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 2704.284176] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 2704.284182] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 2704.284188] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 2704.284193] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 2704.284199] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[ 2704.284205] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 2704.284211] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 2704.284217] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 2704.284222] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[ 2704.284228] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 2704.284234] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[ 2704.284240] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 2704.284246] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[ 2704.284252] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 2704.284261] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[ 2704.284266] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[ 2704.284269] ndiswrapper (load_sys_files:206): couldn't prepare driver 'agux64'
[ 2704.284748] ndiswrapper (load_wrap_driver:108): couldn't load driver agux64; check system log for messages from 'loadndisdriver'
[ 2704.284828] usbcore: registered new interface driver ndiswrapper

```

The dmesg output when using the latest stable version of ndiswrapper (1.56) is the same, lots of symbol errors.

Has anyone had any luck getting this wireless USB dongle to work?  Any suggestions regarding debugging this?

Thanks,
Mark

---

