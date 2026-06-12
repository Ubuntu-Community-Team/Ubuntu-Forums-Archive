---
title: "[SOLVED] ndiswrapper won't recognize intel pro/5100"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by out_of_time on 2008-12-14
I've been banging my head against the wall on this one for a good long time now - new ThinkPad with Intel Pro/Wireless 5100 card. Out of box, it wouldn't recognize any hot spots when doing a scan; after trying to install the iwlwifi-5000-1 microcode, I decided to try the ndiswrapper route. Neither the Vista version of the driver nor the XP version will load at boot, although both of them allow ndiswrapper to recognize the card. I'd appreciate any help in troubleshooting this - I'm just about out of ideas.

Output from uname -a:

```
Linux MatBuntuBook 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
```


Output from lspci -nnv | grep -A 9 Wireless:

```
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
	Subsystem: Intel Corporation Device [8086:1211]
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at fe1fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number 88-4b-cb-ff-ff-ea-16-00
	Kernel modules: iwlagn
```

Output from lshow -C Network:

```
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:2f:f2:7a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.107 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:fa:cd:70:78:cb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Output from ndiswrapper -l

```
netw5x32 : driver installed
	device (8086:4237) present (alternate driver: iwlagn)
```

Output from lsmod | grep ndis:

```
ndiswrapper           196380  0 
usbcore               148848  4 ndiswrapper,ehci_hcd,uhci_hcd
```

Output from dmesg | grep -e ndis -e wlan with **netw5x32 (XP)** driver:

```
[    9.391838] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[    9.439877] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[    9.440097] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netw5x32'
[    9.440893] ndiswrapper (load_wrap_driver:108): couldn't load driver netw5x32; check system log for messages from 'loadndisdriver'
[    9.444571] usbcore: registered new interface driver ndiswrapper
```

Output from dmesg | grep -e ndis -e wlan with **netw5v32 (Vista)** driver:

```
[    9.370049] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[    9.414575] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeBugCheck'
[    9.414654] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[    9.414662] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[    9.414669] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[    9.414677] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[    9.414687] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[    9.414695] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[    9.414711] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[    9.414733] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[    9.414741] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[    9.414749] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[    9.414789] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[    9.414797] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[    9.414804] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[    9.414812] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[    9.414820] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[    9.414828] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[    9.414836] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[    9.414843] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCopyFromNetBufferToNetBuffer'
[    9.414851] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[    9.414859] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[    9.414867] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[    9.414875] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[    9.414883] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[    9.414891] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[    9.414899] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[    9.414907] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[    9.414915] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[    9.414923] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[    9.414930] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[    9.414938] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[    9.414946] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[    9.414954] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[    9.414962] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[    9.414970] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[    9.414978] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[    9.414986] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[    9.414989] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netw5v32'
[    9.415732] ndiswrapper (load_wrap_driver:108): couldn't load driver netw5v32; check system log for messages from 'loadndisdriver'
[    9.419160] usbcore: registered new interface driver ndiswrapper
```

---

### Post by ieee488 on 2008-12-14
Suppose to work right out of the box with Ubuntu 8.10 per post at [http://www.connect-utb.com/index.php?option=com_content&view=article&id=46:get-intel-wireless-wifi-link-5100-working-on-ubuntu-804&catid=34:linux](http://www.connect-utb.com/index.php?option=com_content&view=article&id=46:get-intel-wireless-wifi-link-5100-working-on-ubuntu-804&catid=34:linux)

As far as I know ndiswrapper does not work with Vista drivers.

---

### Post by out_of_time on 2008-12-14
Thanks so much for the reply. The problem I started out with (before messing with ndiswrapper etc.) was similar to the last poster on that thread - the wireless card never reported any available hotspots. I tried troubleshooting that directly but wasn't able to get anywhere with it so I tried the ndiswrapper route. I can of course easily go back to the out of box drivers - can you point me anywhere that might be helpful for troubleshooting the issue of no hotspots appearing? Thanks!

---

### Post by ieee488 on 2008-12-14
How did you determine it couldn't find any hotspots?
I used the commandline > sudo iwlist scan that I learned about in these forums.

---

### Post by out_of_time on 2008-12-14
Yep, that's how I'm doing it as well. I've removed the XP driver from ndiswrapper and un-blacklisted the built-in driver; here's the situation now.

```
# lshw -C Network
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:cb:4b:88
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:2f:f2:7a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.107 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:2a:45:d4:a8:46
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

```
# dmesg | grep -e wlan
[  466.602451] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

```
# ifup wlan0
Ignoring unknown interface wlan0=wlan0.
```

```
# iwlist scan
wlan0     No scan results
```

Help!!

---

### Post by kevdog on 2008-12-14
If you are booting with the iwlagn driver (because that is the driver currently assigned to the card), what does dmesg show regarding this driver?  Is there more errors?

---

### Post by out_of_time on 2008-12-14
Here's the output of dmesg -e iwlagn -e wlan:

```
[    7.489811] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    7.489814] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[    7.501234] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.501244] iwlagn 0000:02:00.0: setting latency timer to 64
[    7.501265] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[    7.520412] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[    7.578486] iwlagn 0000:02:00.0: PCI INT A disabled
[   31.129633] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   31.129747] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   31.150584] iwlagn loaded firmware version 5.4.1.16
[   31.150794] iwlagn: Radio disabled by HW RF Kill switch
[  466.602451] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Thanks!

---

### Post by out_of_time on 2008-12-14
Something else I just came across - here's the output of nm-tool:

```

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:23:54:2F:F2:7A

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings

  IPv4 Settings:
    Address:         192.168.1.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             disconnected
  Default:           no
  HW Address:        00:16:EA:CB:4B:88

  Capabilities:
    Supported:       yes

  Wireless Settings
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
```

The "State: Disconnected" bit seems to be a problem. Is this just one of those "turn your wireless card on" situations? I have to admit I've been using Apple hardware pretty much exclusively until recently so I'm totally clueless about that sort of thing...

---

### Post by out_of_time on 2008-12-14
Just installed WICD per the recommendation of another forum post. It does seem more user friendly but I still don't see any wireless networks in the list.

---

### Post by kevdog on 2008-12-14
HW RF Kill switch

Is there a switch on the outside of your box to turn the card on?

noob12 (a different user) once posted a similar solution for this type of problem.  Its been awhile though and I don't remember the exact solution.  A search for noob12 and intel might yield results.

---

### Post by out_of_time on 2008-12-14
And we're solved. The wireless card wasn't switched on. I swear I'm not braindead.

Since this information doesn't seem to be anywhere else on Google, here's a fun fact for posterity:

The wireless switch for a Lenovo ThinkPad SL300 is on the front of the unit, to the left of the mouse pad. That's how you turn wireless on.

Thanks for all your help everyone!

---

### Post by kevdog on 2008-12-14
Glad you got everything straightened out! :)

---

### Post by cool_vip on 2009-04-08
Tried all the things that u have said above.
Still no hope for my Dv5t laptop having same Intel PRO/Wireless 5100 AGN wifi card ..
Dmesg shows  "Radio disabled by HW RF Kill switch"
But there is no hw switch on my laptop just a touch button..I guess driver are not installed for the touch button but LEDs glows Red when it is down.
If I do "ifconfig wlan0 down" the LED glows Amber
and on "ifconfig wlan0 up" the LED glows blue..

I don't know what to do now..
could someone help

---

