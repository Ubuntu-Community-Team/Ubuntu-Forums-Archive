---
title: "Wifi card not working"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by -Oz- on 2009-10-11
I cant get my Wifi card to work...please take a look at the outputs of commands and suggest something...

Wifi card "Tp-link Wn721n"

ndiswrapper -l

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netathur : driver installed
device (0CF3:9271) present


lsusb

Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



dmesg | grep -e ndis -e wlan

[ 10.633164] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 11.567962] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'RtlIsServicePackVersionInstalled'
[ 11.567997] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[ 11.568059] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[ 11.568073] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[ 11.568233] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 11.568250] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[ 11.568267] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[ 11.568284] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 11.568322] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 11.568339] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 11.568362] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 11.568380] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[ 11.568397] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 11.568415] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 11.568433] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 11.568451] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 11.568469] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[ 11.568486] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 11.568503] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[ 11.568521] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[ 11.568538] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[ 11.568556] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 11.568594] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 11.568621] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 11.568648] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 11.568666] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 11.568689] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 11.568707] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 11.568741] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 11.568817] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 11.568834] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 11.568852] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 11.568870] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 11.568895] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 11.568913] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 11.568930] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 11.568948] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[ 11.568965] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 11.568977] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[ 11.568990] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[ 11.568995] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathur'
[ 11.569866] ndiswrapper (load_wrap_driver:10: couldn't load driver netathur; check system log for messages from 'loadndisdriver'
[ 11.569942] usbcore: registered new interface driver ndiswrapper
[ 880.584269] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'RtlIsServicePackVersionInstalled'
[ 880.584346] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[ 880.584379] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[ 880.584411] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[ 880.584784] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 880.584824] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[ 880.584863] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[ 880.584902] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 880.584988] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 880.585028] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[ 880.585079] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 880.585119] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[ 880.585159] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[ 880.585200] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 880.585240] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 880.585281] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 880.585321] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[ 880.585360] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 880.585400] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[ 880.585440] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[ 880.585479] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[ 880.585518] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 880.585605] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 880.585667] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 880.585730] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 880.585771] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 880.585823] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 880.585863] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 880.585941] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 880.586117] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 880.586156] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 880.586197] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 880.586237] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 880.586295] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 880.586335] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 880.586374] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 880.586414] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[ 880.586453] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 880.586483] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[ 880.586512] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[ 880.586521] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathur'
[ 880.604232] ndiswrapper (load_wrap_driver:10: couldn't load driver netathur; check system log for messages from 'loadndisdriver'

---

### Post by coffeeaddict22 on 2009-10-11
Hi,
ndiswrapper is a driver for Linux.  It works by "wrapping" a windows driver, and essentially hiding its messy details from the Linux system.  As such, it's a kludge, albeit a pretty effective one.  However, over the last year a lot of the wireless drivers have made it into the kernel, so you download them automatically, and ndiswrapper tends to mess things up.

To get a bit more info on your card, can you post back the output of the following two separate commands:
```
lshw -C network
ifconfig
```and we'll go from there.

---

### Post by -Oz- on 2009-10-11
Sudo lshw - C network

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:bc:01:d7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:73:19:d0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.0.220 latency=128 link=yes maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 66:df:60:76:6d:cd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


ifconfig

eth0      Link encap:Ethernet  HWaddr 00:02:3f:bc:01:d7  
          inet6 addr: fe80::202:3fff:febc:1d7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:2 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:258 (258.0 B)  TX bytes:2576 (2.5 KB)
          Interrupt:10 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:04:23:73:19:d0  
          inet addr:192.168.0.220  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:23ff:fe73:19d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25081 errors:7 dropped:0 overruns:0 frame:0
          TX packets:23039 errors:0 dropped:29 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23557151 (23.5 MB)  TX bytes:3204617 (3.2 MB)
          Interrupt:10 Base address:0x2000 Memory:e0000000-e0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)

The device isnt even listed here...but when i run the following command with device plugged ... it recognizes the device...but it doesnt makes it functional

 ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netathur : driver installed
	device (0CF3:9271) present

---

### Post by Bucky Ball on 2009-10-11
You shouldn't need to use ndiswrapper for this card. Most TP-Link gear works out of the box. Catch 22 is you need to plug in a cable to get the restricted drivers. 

If you haven't done it already plug in an ethernet cable. Ndiswrapper is *definitely* a last resort. Very clumsy and superseded for a lot of cards now. Atheros cards (which is the chipset your USB wireless dongle uses by the looks) is generally covered by the madwifi drivers and should be your first port of call rather than ndiswrapper. The appropriate drivers will probably get installed if you plug in an ethernet cable and get online then plug in your dongle.

---

### Post by coffeeaddict22 on 2009-10-11
To quote your post: 
[I]description: Wireless interface
product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:01:02.0
logical name: eth1
version: 04
serial: 00:04:23:73:19:d0
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes **driver=ipw2100** driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.0.220 latency=128 link=yes maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
[/I]

What's important here is that you've got a driver, it's the native Linux driver (and not ndiswrapper).  You need to get rid of ndiswrapper now; there's a post [here]("http://ubuntuforums.org/showthread.php?t=222184") that has details on that.  Once you've done that, have a shot at connecting.  Post back the output of ```
nm-tool
``` if it doesn't work.

---

### Post by -Oz- on 2009-10-12
> **Bucky Ball said:**
> You shouldn't need to use ndiswrapper for this card. Most TP-Link gear works out of the box. Catch 22 is you need to plug in a cable to get the restricted drivers. 

If you haven't done it already plug in an ethernet cable. Ndiswrapper is *definitely* a last resort. Very clumsy and superseded for a lot of cards now. Atheros cards (which is the chipset your USB wireless dongle uses by the looks) is generally covered by the madwifi drivers and should be your first port of call rather than ndiswrapper. The appropriate drivers will probably get installed if you plug in an ethernet cable and get online then plug in your dongle.


I tried that....it doesn't works....

lsusb 
Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

 ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:02:3f:bc:01:d7  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:febc:1d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:781281 (781.2 KB)  TX bytes:111749 (111.7 KB)
          Interrupt:10 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:04:23:73:19:d0  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x8000 Memory:e0000000-e0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by -Oz- on 2009-10-12
> **coffeeaddict22 said:**
> To quote your post: 
[I]description: Wireless interface
product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:01:02.0
logical name: eth1
version: 04
serial: 00:04:23:73:19:d0
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes **driver=ipw2100** driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.0.220 latency=128 link=yes maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
[/I]

What's important here is that you've got a driver, it's the native Linux driver (and not ndiswrapper).  You need to get rid of ndiswrapper now; there's a post [here]("http://ubuntuforums.org/showthread.php?t=222184") that has details on that.  Once you've done that, have a shot at connecting.  Post back the output of ```
nm-tool
``` if it doesn't work.


I have an external device (TP-Link TL-WN721N) that i need to use as wifi adapter...the one you mentioned is a built-in wifi card...and that works perfectly fine.

```
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:02:3F:BC:01:D7

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2100
  State:             unavailable
  Default:           no
  HW Address:        00:04:23:73:19:D0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```

---

### Post by -Oz- on 2009-10-12
I installed the new version ndiswrapper 1.55 and reinstalled the drivers....the dongle still doesnt works...but when i plugout and plugin again...dmesg shows the following output (last few lines)

```
[   56.008032] eth0: no IPv6 routers present
[  100.161225] usb 1-3: USB disconnect, address 2
[  102.500175] usb 1-3: new high speed USB device using ehci_hcd and address 3
[  102.649268] usb 1-3: configuration #1 chosen from 1 choice
[  102.812183] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[  103.073451] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'RtlIsServicePackVersionInstalled'
[  103.073526] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[  103.073559] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[  103.073592] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[  103.073970] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  103.074008] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[  103.074049] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[  103.074089] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  103.074177] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  103.074218] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[  103.074271] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  103.074312] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[  103.074353] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[  103.074394] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[  103.074435] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  103.074477] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  103.074518] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[  103.074558] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  103.074598] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[  103.074639] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[  103.074679] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[  103.074719] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  103.074809] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  103.074873] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[  103.074938] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  103.074980] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  103.075033] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  103.075074] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  103.075190] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  103.075373] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  103.075413] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  103.075455] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[  103.075496] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  103.075556] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  103.075596] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  103.075636] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  103.075677] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[  103.075717] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  103.075747] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  103.075776] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  103.075785] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathur'
[  103.098452] ndiswrapper (load_wrap_driver:108): couldn't load driver netathur; check system log for messages from 'loadndisdriver'

```

---

### Post by coffeeaddict22 on 2009-10-12
OK.  So you've got an onboard wireless card, but you don't want to use that, and a wireless USB dongle that you do want to use?  Am I correct?  And if you don't mind us asking, why?  Are you upgrading to wireless n?

---

### Post by -Oz- on 2009-10-12
> **coffeeaddict22 said:**
> OK.  So you've got an onboard wireless card, but you don't want to use that, and a wireless USB dongle that you do want to use?  Am I correct?  And if you don't mind us asking, why?  Are you upgrading to wireless n?

Two reasons...

1. Problem with the range of the internal wifi card...doesnt works beyond couple of feets...and its 802.11b

2. Yes i want to upgrade to n.

---

### Post by -Oz- on 2009-10-12
Please have a look at the following link....there are drivers available on this site (i think) , but i dont know how to use them

[http://linuxwireless.org/en/users/Drivers/ath_hif_usb#ar9271_hw_support](http://linuxwireless.org/en/users/Drivers/ath_hif_usb#ar9271_hw_support)


I really appreciate for your time...thanks a lot.

---

### Post by coffeeaddict22 on 2009-10-12
Have you looked in System/Hardware drivers?  There might be a restricted driver that you can enable.

---

### Post by Bucky Ball on 2009-10-13
> **coffeeaddict22 said:**
> Have you looked in System/Hardware drivers?  There might be a restricted driver that you can enable.

... but if there are they will not work with ndiswrapper installed.

---

### Post by -Oz- on 2009-10-14
Nope it doesn't works....

Please tell me how to use the drivers listed here...

[http://linuxwireless.org/en/users/Dr...271_hw_support](http://linuxwireless.org/en/users/Dr...271_hw_support)

How to use the filename.c or filename.h...for drivers.

---

### Post by coffeeaddict22 on 2009-10-14
Um.  Sorry.  Looking at [this page]("http://www.pubbs.net/kernel/200909/72025/") there aren't any wireless drivers in Linux for your card.  I'm guessing, but I suspect you'll find there isn't a ndiswrapper project for these either; most effort with wireless these days is going into native drivers.  
It would be worth nagging the manufacturer; if they don't recognise the demand for a Linux driver, they don't bother putting any effort into it.

your options now: buy a new card or wait for the driver.

---

### Post by Bucky Ball on 2009-10-14
I suggest plugging in and ethernet cable, re-install Ubuntu, restart, plug in your wireless dongle, sit and wait and get the updates and restricted drivers you are offered. Once you started with ndiswrapper you seriously slimmed your chances of getting any native drivers to work. First thing when you install is to plug in a cable and get your updates.

As I said posts ago, it is a catch 22; if a driver does exist for your wireless device it is generally restricted in some way and therefore can not be included in Ubuntu. BUT, if you plug in a cable and get the updates before you kick of with your new install, if there is a driver for you wireless it will be offered. It is a matter of you agreeing that is at the crux of the rigamarole.

Very hard to get wireless online without getting online first. As I also said, TP-Link generally works out of the box, although this looks like a newer device.

ndiswrapper is not where you should be looking but you seem to ignore that. Good luck with it.

---

### Post by -Oz- on 2009-10-14
Well reinstalling the whole OS is certainly not a feasible solution....
Please tell me how to notuse ndiswrapper...i am "still" a n00b at linux.

Also please provide me with a link where i can learn how to compile .c and .h files as a driver...

---

### Post by flash63 on 2010-03-02
Hello,
new answer here:
[http://ubuntuforums.org/showthread.php?p=8906043#post8906043]("http://ubuntuforums.org/showthread.php?p=8906043#post8906043")

---

