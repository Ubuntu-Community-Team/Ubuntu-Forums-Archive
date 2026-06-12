---
title: "How pack TP_Link tl_wn322G+ in the Linux  V2.0 version USB driving of wireless net ca"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by empc on 2009-08-07
Excuse me, How pack TP_Link tl_wn322G+ in the Linux  V2.0 version USB driving of wireless net card?
 
The tl_wn 322G+2.0 versions wireless net card adoptions are Atheros AR9271s project, I tried to use ndiswrapper-1.55 while installing Windows of that wireless net card to drive under the linux, installing a driving of windows version and used ndiswrapper-l and showed for the driving of mistake and used ndiswrapper-i the order installed Vista under of drive, hint to come amiss while showing to install to drive, but using modproe ndiswrapper a start, can not drive.
Want to invite a friend who have the same equipments to experiment together bottom, see how let the 322 Gs of TP-LINK tl_wn+2.0 versions wireless net cards get rid of to move in the linux bottom.
 
execution lsusb
Show
 
Bus 001 Device 002:ID 0cf3:1006 Atheros Communications, Inc.
Bus 001 Device 001:ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001:ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001:ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001:ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001:ID 1d6b:0001 Linux Foundation 1.1 root hub
 
Two, can install the 322 Gs of TP_Link tl_wn+ VISTA of 2.0 wireless net cards drive
Circulate ndiswrapper-l
Show
netathur :driver installed
device (0CF3:1006) present
 
If install windowsXP to drive
execution ndiswrapper – l
Show
netathuw :invalid driver!
Three, circulate following instructions all infallibility hint
diswrapper -m
ndiswrapper -ma
ndiswrapper -mi
execution the instruction of modprobe ndiswrapper
Show
WARNING:All config files need .conf:|etc|modprobe.d|ndiswrapper, it will be ignored in a future release.
 
execution vi|etc|modprobe.d|ndiswrapper
Run as follow:
install usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip* |sbin|modprobe ndiswrapper
install usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip* |sbin|modprobe ndiswrapper
install usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip* |sbin|modprobe ndiswrapper
 
execution lsmod
Show
ModuleSize Used by
ndiswrapper1933080
This is at buntu the gearing circumstance of the 9.04 times
 
execution dmesg| the instruction of grep ndiswrapper
Show
[6.464520] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[7.327820] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'RtlIsServicePackVersionInstalled'
[7.327832] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeInitializeGuardedMutex'
[7.327837] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeReleaseGuardedMutex'
[7.327842] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeAcquireGuardedMutex'
[7.327890] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateMdl'
[7.327896] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisRetreatNetBufferDataStart'
[7.327901] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[7.327907] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeMdl'
[7.327918] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisOpenConfigurationEx'
[7.327924] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSetBusData'
[7.327931] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[7.327937] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMAllocateNetBufferSGList'
[7.327942] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMFreeNetBufferSGList'
[7.327948] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[7.327954] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[7.327960] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferListPool'
[7.327965] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferPool'
[7.327971] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferListPool'
[7.327976] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferPool'
[7.327982] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBuffer'
[7.327987] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBuffer'
[7.327993] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMGetBusData'
[7.328017] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSendNetBufferListsComplete'
[7.328025] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[7.328034] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMRegisterMiniportDriver'
[7.328040] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[7.328047] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeIoWorkItem'
[7.328052] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateIoWorkItem'
[7.328063] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMResetComplete'
[7.328086] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterMiniportDriver'
[7.328092] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisQueueIoWorkItem'
[7.328097] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterInterruptEx'
[7.328103] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSetMiniportAttributes'
[7.328111] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMIndicateStatusEx'
[7.328117] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMOidRequestComplete'
[7.328122] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisGetSystemUpTimeEx'
[7.328128] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferList'
[7.328133] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferList'
[7.328138] ndiswrapper (import:242):unknown symbol:WDFLDR.SYS:'WdfVersionUnbind'
[7.328142] ndiswrapper (import:242):unknown symbol:WDFLDR.SYS:'WdfVersionBind'
[7.328144] ndiswrapper (load_sys_files:206):couldn't prepare driver 'netathur'
[7.328527] ndiswrapper (load_wrap_driver:108):couldn't load driver netathur;check system log for messages from 'loadndisdriver'
[7.328563] usbcore:registered new interface driver ndiswrapper
[ 420.085862] usbcore:deregistering interface driver ndiswrapper
[ 420.085930] ndiswrapper (ntoskernel_exit:2677):object f6692920(2) was not freed, freeing it now
[ 438.244205] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 438.515640] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'RtlIsServicePackVersionInstalled'
[ 438.515659] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeInitializeGuardedMutex'
[ 438.515667] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeReleaseGuardedMutex'
[ 438.515675] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeAcquireGuardedMutex'
[ 438.515756] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateMdl'
[ 438.515765] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisRetreatNetBufferDataStart'
[ 438.515774] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[ 438.515784] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeMdl'
[ 438.515803] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisOpenConfigurationEx'
[ 438.515812] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSetBusData'
[ 438.515824] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 438.515833] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMAllocateNetBufferSGList'
[ 438.515843] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 438.515852] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 438.515862] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 438.515871] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 438.515881] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferPool'
[ 438.515890] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferListPool'
[ 438.515900] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferPool'
[ 438.515909] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBuffer'
[ 438.515918] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBuffer'
[ 438.515927] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMGetBusData'
[ 438.515947] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 438.515961] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 438.515976] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 438.515985] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 438.516030] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeIoWorkItem'
[ 438.516040] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateIoWorkItem'
[ 438.516057] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMResetComplete'
[ 438.516096] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 438.516105] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisQueueIoWorkItem'
[ 438.516114] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 438.516124] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSetMiniportAttributes'
[ 438.516137] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMIndicateStatusEx'
[ 438.516146] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMOidRequestComplete'
[ 438.516155] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 438.516165] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferList'
[ 438.516174] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferList'
[ 438.516181] ndiswrapper (import:242):unknown symbol:WDFLDR.SYS:'WdfVersionUnbind'
[ 438.516188] ndiswrapper (import:242):unknown symbol:WDFLDR.SYS:'WdfVersionBind'
[ 438.516191] ndiswrapper (load_sys_files:206):couldn't prepare driver 'netathur'
[ 438.521082] ndiswrapper (load_wrap_driver:108):couldn't load driver netathur;check system log for messages from 'loadndisdriver'
[ 438.521123] usbcore:registered new interface driver ndiswrapper
[ 447.301421] usbcore:deregistering interface driver ndiswrapper
[ 447.301487] ndiswrapper (ntoskernel_exit:2677):object f6692520(2) was not freed, freeing it now
[ 975.118704] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 975.387543] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'RtlIsServicePackVersionInstalled'
[ 975.387562] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeInitializeGuardedMutex'
[ 975.387570] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeReleaseGuardedMutex'
[ 975.387578] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeAcquireGuardedMutex'
[ 975.387659] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateMdl'
[ 975.387668] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisRetreatNetBufferDataStart'
[ 975.387677] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[ 975.387687] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeMdl'
[ 975.387706] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisOpenConfigurationEx'
[ 975.387715] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSetBusData'
[ 975.387727] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 975.387736] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMAllocateNetBufferSGList'
[ 975.387746] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 975.387756] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 975.387765] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 975.387775] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 975.387784] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferPool'
[ 975.387794] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferListPool'
[ 975.387803] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferPool'
[ 975.387812] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBuffer'
[ 975.387821] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBuffer'
[ 975.387831] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMGetBusData'
[ 975.387850] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 975.387865] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 975.387879] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 975.387889] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 975.387901] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeIoWorkItem'
[ 975.387910] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateIoWorkItem'
[ 975.387927] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMResetComplete'
[ 975.387966] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 975.387976] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisQueueIoWorkItem'
[ 975.387985] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 975.388031] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSetMiniportAttributes'
[ 975.388045] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMIndicateStatusEx'
[ 975.388054] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMOidRequestComplete'
[ 975.388064] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 975.388073] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferList'
[ 975.388082] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferList'
[ 975.388089] ndiswrapper (import:242):unknown symbol:WDFLDR.SYS:'WdfVersionUnbind'
[ 975.388096] ndiswrapper (import:242):unknown symbol:WDFLDR.SYS:'WdfVersionBind'
[ 975.388099] ndiswrapper (load_sys_files:206):couldn't prepare driver 'netathur'
[ 975.392998] ndiswrapper (load_wrap_driver:108):couldn't load driver netathur;check system log for messages from 'loadndisdriver'
[ 975.393040] usbcore:registered new interface driver ndiswrapper
[ 1149.886130] usbcore:deregistering interface driver ndiswrapper
[ 1149.886200] ndiswrapper (ntoskernel_exit:2677):object f6692920(2) was not freed, freeing it now
[ 1179.057813] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 1179.323728] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'RtlIsServicePackVersionInstalled'
[ 1179.323746] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeInitializeGuardedMutex'
[ 1179.323755] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeReleaseGuardedMutex'
[ 1179.323762] ndiswrapper (import:242):unknown symbol:ntoskrnl.exe:'KeAcquireGuardedMutex'
[ 1179.323843] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateMdl'
[ 1179.323853] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisRetreatNetBufferDataStart'
[ 1179.323862] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[ 1179.323871] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeMdl'
[ 1179.323890] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisOpenConfigurationEx'
[ 1179.323899] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSetBusData'
[ 1179.323911] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 1179.323921] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMAllocateNetBufferSGList'
[ 1179.323930] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 1179.323940] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 1179.323949] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 1179.323959] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 1179.323969] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferPool'
[ 1179.323978] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferListPool'
[ 1179.323987] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferPool'
[ 1179.324036] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBuffer'
[ 1179.324045] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBuffer'
[ 1179.324055] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMGetBusData'
[ 1179.324076] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 1179.324092] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 1179.324108] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 1179.324119] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 1179.324132] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeIoWorkItem'
[ 1179.324143] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateIoWorkItem'
[ 1179.324162] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMResetComplete'
[ 1179.324202] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 1179.324212] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisQueueIoWorkItem'
[ 1179.324223] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 1179.324234] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMSetMiniportAttributes'
[ 1179.324249] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMIndicateStatusEx'
[ 1179.324260] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisMOidRequestComplete'
[ 1179.324270] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 1179.324281] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisAllocateNetBufferList'
[ 1179.324292] ndiswrapper (import:242):unknown symbol:NDIS.SYS:'NdisFreeNetBufferList'
[ 1179.324300] ndiswrapper (import:242):unknown symbol:WDFLDR.SYS:'WdfVersionUnbind'
[ 1179.324309] ndiswrapper (import:242):unknown symbol:WDFLDR.SYS:'WdfVersionBind'
[ 1179.324313] ndiswrapper (load_sys_files:206):couldn't prepare driver 'netathur'
[ 1179.324915] ndiswrapper (load_wrap_driver:108):couldn't load driver netathur;check system log for messages from 'loadndisdriver'
[ 1179.324956] usbcore:registered new interface driver ndiswrapper

---

