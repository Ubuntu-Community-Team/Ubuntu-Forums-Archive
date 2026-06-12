---
title: "Netgear  WNDA3100"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by much on 2009-02-02
Second time I've tried ubuntu now and the last time ended because of problems with another wireless adapter, I'm determined to get it working this time :)

I'm using ubuntu 8.10 and I've installed ndiswrapper and copied over my driver files from windows vista 32 bit, these are the files I've copied over (I wasn't sure which ones to use so I copied all the files I could find that were mentioned in oem13.inf):
> arusb_lh.cat
arusb_lh.inf
arusb_lh.sys
oem13.inf
WNDA31v.sys
oem13.PNF
netevent.dll
neteven.dll.mui
I loaded oem13.inf up in ndiswrappper but nothing appeared in the network manager and the wireless adapters lights which usually flash when it's working in windows weren't on.

here are the results of the commands from the troubleshooting guide:

peter@peter-desktop:~$ ndiswrapper -l
> oem13 : driver installed
	device (0846:9010) present

peter@peter-desktop:~$ lshw -C Network
> WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:54:a9:e0:bd:97
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


peter@peter-desktop:~$ uname -m
> i686

peter@peter-desktop:~$ dmesg | grep -e ndis -e wlan
> [   14.458038] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   15.245407] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   15.245415] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   15.245421] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   15.245427] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   15.245434] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   15.245440] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   15.245456] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   15.245464] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   15.245470] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   15.245478] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   15.245489] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   15.245498] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   15.245505] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   15.245527] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   15.245533] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   15.245545] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   15.245551] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   15.245557] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   15.245564] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   15.245575] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   15.245581] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   15.245587] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   15.245594] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   15.245598] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   15.245603] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   15.245605] ndiswrapper (load_sys_files:206): couldn't prepare driver 'oem13'
[   15.246006] ndiswrapper (load_wrap_driver:108): couldn't load driver oem13; check system log for messages from 'loadndisdriver'
[   15.246042] usbcore: registered new interface driver ndiswrapper
[  261.723890] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  261.723902] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  261.723908] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[  261.723914] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[  261.723921] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[  261.723927] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  261.723943] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  261.723951] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  261.723957] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  261.723965] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  261.723976] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  261.723985] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  261.723992] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  261.724014] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  261.724020] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  261.724032] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  261.724038] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  261.724045] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  261.724051] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  261.724062] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[  261.724068] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[  261.724075] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  261.724081] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  261.724086] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  261.724091] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  261.724093] ndiswrapper (load_sys_files:206): couldn't prepare driver 'oem13'
[  261.738488] ndiswrapper (load_wrap_driver:108): couldn't load driver oem13; check system log for messages from 'loadndisdriver'


peter@peter-desktop:~$ lsusb
> Bus 002 Device 004: ID 05e3:0716 Genesys Logic, Inc. 
Bus 002 Device 002: ID 0846:9010 NetGear, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

please help :<

Edit - If someone who has got their WNDA3100 to work could send me the files they used that would be great so I could test if it's just my vista drivers that are messing it up (or if I'm missing files).

Edit2 - I'm on a dual boot with vista so I can get onto the internet from windows.

---

### Post by much on 2009-02-03
would realy like some help.

---

### Post by much on 2009-02-03
?

---

### Post by piccolinux on 2009-02-04
Hi, here are the files I used. My WNDA3100 is working but it looses the connection every now and then. I got to investigate a little bit.
By the way I would suggest to use Wicd instead of network manager I didn't manage to get it connected whit the latter.

---

### Post by piccolinux on 2009-02-04
Hi, here are the files I used. My WNDA3100 is working but it looses the connection every now and then. I got to investigate a little bit.
By the way I would suggest to use Wicd instead of network manager I didn't manage to get it connected whit the latter.

---

### Post by asdfasdfasdfads on 2009-10-04
WNDA3100.tar.gz driver worked for me... I have tried the other drivers in the past with no success, do you know if this has to do with the .inf files or the actual driver .sys files?

---

