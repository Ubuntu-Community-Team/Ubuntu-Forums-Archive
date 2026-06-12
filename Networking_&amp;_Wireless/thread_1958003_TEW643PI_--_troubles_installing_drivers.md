---
title: "TEW643PI -- troubles installing drivers"
date: 2012-04-13
forum: Networking &amp; Wireless
---

### Post by kajong0007 on 2012-04-13
I know this card just seems to work with other people, but I have had no such luck. Ndiswrapper has done nothing helpful so far, and I am nearing my wit's end. Here is some terminal output:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 54:04:a6:bf:cf:a2  
          inet addr:10.100.69.123  Bcast:10.100.69.255  Mask:255.255.255.0
          inet6 addr: fe80::5604:a6ff:febf:cfa2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2957 errors:0 dropped:2957 overruns:0 frame:2957
          TX packets:2530 errors:0 dropped:46 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3404313 (3.4 MB)  TX bytes:400673 (400.6 KB)
          Interrupt:52 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4240 (4.2 KB)  TX bytes:4240 (4.2 KB)
``````
$ dmesg | grep -e ndis -e wlan
[  532.271157] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  532.291942] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  532.291951] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  532.291958] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  532.291965] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[  532.291976] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  532.291982] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  532.291988] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[  532.292006] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  532.292013] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  532.292019] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  532.292034] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  532.292044] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[  532.292050] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[  532.292057] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[  532.292066] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  532.292080] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  532.292087] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  532.292093] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  532.292102] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[  532.292108] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  532.292115] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[  532.292124] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  532.292130] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  532.292142] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[  532.292148] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[  532.292155] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[  532.292161] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  532.292167] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  532.292174] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  532.292180] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[  532.292183] ndiswrapper (load_sys_files:199): couldn't prepare driver 'net819xp'
[  532.292533] ndiswrapper (load_wrap_driver:102): couldn't load driver net819xp; check system log for messages from 'loadndisdriver'
[  532.292583] usbcore: registered new interface driver ndiswrapper
```I have tried the drivers for Windows 7 64-bit, Windows 2000, Windows XP 64-bit and the 32-bit variants of the mentioned systems. The 32-bit ones are unrecognized (as expected; I'm on 64-bit Ubuntu), Windows XP 64-bit crashes my system, Windows 7 64-bit claims to work but I suspect it made the error messages above...

Might as well add this too:

```
$ ndiswrapper -l
net819xp : driver installed
    device (10EC:8190) present
```

---

### Post by praseodym on 2012-04-13
Try this:

```
sudo cp /etc/modules.conf /etc/modprobe.d/ndiswrapper.conf
```
Tried to setup the driver via terminal?

```
sudo ndiswrapper -i /path/to/driver.INF
```
Do you have a driver CD with a Win driver on it?

---

### Post by kajong0007 on 2012-04-13
Yeah, I installed the drivers "correctly" after copying them from the CD. I copied over "Windows 7/x64/net819xp.inf" and "rtl819xp.sys". These appear to install correctly:

```
$ndiswrapper -l
net819xp : driver installed
device (10EC:8190) present
```

And now ubuntu won't start unity or gnome or whatever it is nowadays... I can still use the command line, but I still have much to learn before I am quite command-line savvy.

Might as well add this output:

```
$lshw -C Network
*-network UNCLAIMED
    description: Network controller
    product: Realtek Semiconductor Co., Ltd.
    vendor: Realtek Semiconductor Co., Ltd.
    physical id: 1
    bus info: pci@0000:09:01.0
    version: 00
    width: 32 bits
    clock:  33MHz
    capabilities: pm bus_master cap_list
    configuration: latency=32 maxlatency=64 mingnt=32
    resources: ioport:c000(size=256) memory:fa100000-fa100fff
```

---

### Post by kajong0007 on 2012-04-14
I'm throwing in the towel and just buying a different card or USB dongle.

---

