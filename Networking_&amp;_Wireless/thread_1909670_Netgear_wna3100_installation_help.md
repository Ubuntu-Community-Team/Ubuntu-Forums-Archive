---
title: "Netgear wna3100 installation help"
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by Ipcipher on 2012-01-15
New to ubuntu and I am trying to install a netgear wna3100 usb wireless card. I have followed many of the threads and have been able to install the driver bcmwlhigh6 using ndisgtk. I still cannot use the wireless device it doesn't show up as a network device. Below is a list of commands with the output to help with the troubleshooting process. Any help is greatly appreciated.  

manny@manny-desktop:~$ ndiswrapper -l
bcmwlhigh6 : driver installed
    device (0846:9020) present
manny@manny-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 002 Device 003: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
manny@manny-desktop:~$ uname -m
x86_64
manny@manny-desktop:~$ 
root@manny-desktop:~# lsmod | grep ndis
ndiswrapper           254773  0 
root@manny-desktop:~# dmesg | grep -e ndis -e wlan
[   15.774101] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   17.696546] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[   17.696562] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoRegisterPlugPlayNotification'
[   17.696580] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   17.696585] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   17.696590] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   17.696597] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   17.696603] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   17.696608] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   17.696613] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   17.696619] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   17.696624] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   17.696631] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   17.696639] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   17.696644] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   17.696650] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   17.696655] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   17.696660] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   17.696665] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   17.696670] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   17.696675] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   17.696680] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   17.696685] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   17.696692] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   17.696697] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   17.696702] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   17.696711] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   17.696716] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   17.696722] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   17.696727] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   17.696735] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   17.696748] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   17.696752] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   17.696756] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   17.696761] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   17.696765] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   17.696768] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh6'
[   17.697267] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
[   17.697313] usbcore: registered new interface driver ndiswrapper
[  478.564530] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[  478.564571] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoRegisterPlugPlayNotification'
[  478.564616] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  478.564629] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  478.564643] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  478.564662] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  478.564676] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[  478.564689] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  478.564703] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  478.564717] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  478.564731] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  478.564751] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[  478.564770] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  478.564784] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMFreePort'
[  478.564798] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  478.564812] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[  478.564826] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  478.564839] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  478.564852] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[  478.564865] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  478.564878] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[  478.564891] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[  478.564908] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[  478.564921] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  478.564935] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  478.564960] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  478.564973] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  478.564986] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  478.565000] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  478.565022] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  478.565054] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  478.565065] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  478.565076] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[  478.565087] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[  478.565099] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  478.565105] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh6'
[  478.566179] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
[  502.553168] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[  502.553209] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoRegisterPlugPlayNotification'
[  502.553254] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  502.553268] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  502.553282] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  502.553301] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  502.553315] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[  502.553328] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  502.553342] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  502.553356] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  502.553370] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  502.553390] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[  502.553409] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  502.553423] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMFreePort'
[  502.553437] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  502.553451] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[  502.553465] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  502.553478] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  502.553491] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[  502.553504] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  502.553517] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[  502.553530] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[  502.553547] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[  502.553561] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  502.553574] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  502.553599] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  502.553612] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  502.553626] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  502.553639] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  502.553662] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  502.553693] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  502.553704] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  502.553716] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[  502.553727] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[  502.553738] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  502.553744] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh6'
[  502.554709] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'

---

### Post by praseodym on 2012-01-16
Hi,

try to compile the latest stable version 1.57 from ndiswrapper by hand. See here:

[http://ubuntuforums.org/showpost.php?p=11612708&postcount=1113](http://ubuntuforums.org/showpost.php?p=11612708&postcount=1113)

---

### Post by shmoobies on 2012-04-03
Hi Ipcipher.  This is what I did for Ubuntu 10.04.  I have wine, winetricks, and windows wireless drivers installed.  
1)Downloaded and installed(so to speak) Netgears driver from [here]("http://support.netgear.com/app/answers/detail/a_id/19878/%7E/wna3100-software-version-2.0") with wine.
2) Copied the drivers from  my .wine/drive_c/Program Files/NETGEAR/WNA3100/Driver/WinXP2000.  I copied the .inf and both .sys files to a folder /home/<your home folder>/Netgear.
3)Started  System->Admininstation->Windows Wireless Drivers, clicked the 'Install New Drivers' tab, browsed to the .inf file at /home/<your home folder>/Netgear, loaded it and it started right up.

Hope this works for you

---

