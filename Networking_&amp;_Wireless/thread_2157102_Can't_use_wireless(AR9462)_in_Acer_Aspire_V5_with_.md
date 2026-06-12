---
title: "Can't use wireless(AR9462) in Acer Aspire V5 with Ubuntu 10.04"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by Maxyao on 2013-06-24
My wifi card is minipcie.
below is that I run "lspci -nn"
```
04:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0034] (rev 01)
```


And I run lshw -C network,
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:03:00.2
       logical name: eth0
       version: 0a
       serial: 20:6a:8a:8c:c1:33
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.35.141.48 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:28 ioport:2000(size=256) memory:f3804000-f3804fff(prefetchable) memory:f3800000-f3803fff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f3900000-f397ffff memory:cfa00000-cfa0ffff(prefetchable)

```

I run "iwconfig" and get:
```
lo        no wireless extensions.

eth0      no wireless extensions.


pan0      no wireless extensions.



```
My kernel version is 2.6.32-38-generic. (run uname -r)
Could anyone teach me how to enable wireless in Ubuntu 10.04?

Thanks.

---

### Post by Maxyao on 2013-06-24
I use ndiswrapper to install driver.
> netathrx : driver installed
    device (168C:0034) present
But it show some error message
> [    9.793478] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   10.299308] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoCreateSynchronizationEvent'
[   10.299323] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   10.299327] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   10.299331] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   10.299334] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoRegisterPlugPlayNotification'
[   10.299341] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[   10.299350] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'DbgPrintEx'
[   10.299358] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   10.299364] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   10.299368] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   10.299372] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   10.299376] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   10.299381] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   10.299385] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   10.299389] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   10.299393] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   10.299400] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   10.299405] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   10.299409] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   10.299413] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   10.299417] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   10.299421] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   10.299425] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   10.299429] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   10.299433] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   10.299437] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   10.299441] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   10.299445] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   10.299451] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   10.299455] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   10.299459] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   10.299463] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   10.299467] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   10.299473] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   10.299477] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   10.299481] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   10.299485] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   10.299489] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   10.299493] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   10.299497] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   10.299504] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   10.299508] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetDeviceReservedExtension'
[   10.299512] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[   10.299516] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[   10.299520] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   10.299531] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   10.299535] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   10.299539] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   10.299549] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   10.299555] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   10.299559] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   10.299563] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   10.299567] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   10.299569] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathrx'
[   10.300025] ndiswrapper (load_wrap_driver:108): couldn't load driver netathrx; check system log for messages from 'loadndisdriver'
[   10.300082] usbcore: registered new interface driver ndiswrapper

Thanks.

---

### Post by mörgæs on 2013-06-25
Hi, welcome to the fora.

10.04 is out of support. As a first step I would recommend a fresh install of 12.04.2 or 13.04.

After that is done please wait a moment before installing ndiswrapper.

---

