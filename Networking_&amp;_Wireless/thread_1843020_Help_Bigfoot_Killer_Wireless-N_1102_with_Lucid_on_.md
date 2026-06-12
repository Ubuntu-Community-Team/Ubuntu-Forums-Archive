---
title: "Help: Bigfoot Killer Wireless-N 1102 with Lucid on AVADirect Compal PBL20/"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by hughh on 2011-09-12
I have been unable to make any progress in getting wireless networking up on my new notebook.  I suspect the main thing I need to do is find the right driver to load with ndiswrapper, which I'm not finding anywhere, but I'm not even sure I'm on the right track.  Any help would be appreciated!

• CUSTOM NOTEBOOK, Compal PBL20 Core™ i7 Value Notebook, 15.6" HD Glossy LED LCD, Intel® GMA HD Graphics
• BIGFOOT NETWORKS, Killer Wireless-N 1102 Wireless Card, IEEE 802.11a/b/g/n, Internal PCIe Half Mini Card

Here's some information I gathered that I think might be relevant:
```
$ uname -a
Linux hugh-laptop 2.6.32-33-generic-pae #72-Ubuntu SMP Fri Jul 29 22:06:29 UTC 2011 i686 GNU/Linux

$ lsb_release -d
Description:    Ubuntu 10.04.3 LTS

$ lspci | grep -i net
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: Atheros Communications Inc. Device 0030 (rev 01)

$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:70:f4:72:f6:f0  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ba70:f4ff:fe72:f6f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53659667 (53.6 MB)  TX bytes:4296839 (4.2 MB)
          Interrupt:28 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1120 (1.1 KB)  TX bytes:1120 (1.1 KB)

$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

$ lsmod | grep ath
ath_pci               194061  0 
wlan                  222926  1 ath_pci
ath_hal               398604  1 ath_pci
$ dmesg | grep -Ei '(2:00.0|ndis)'
[    0.663670] pci 0000:02:00.0: reg 10 64bit mmio: [0xc2500000-0xc251ffff]
[    0.663761] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xffff0000-0xffffffff]
[    0.663827] pci 0000:02:00.0: supports D1
[    0.663828] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.663838] pci 0000:02:00.0: PME# disabled
[    0.770781] pci 0000:02:00.0: BAR 6: no parent found for of device [0xffff0000-0xffffffff]
[ 1033.840796] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 1033.858205] usbcore: registered new interface driver ndiswrapper
[ 1045.868833] usbcore: deregistering interface driver ndiswrapper
[ 1045.893570] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 1045.906366] usbcore: registered new interface driver ndiswrapper
[ 1063.751356] usbcore: deregistering interface driver ndiswrapper
[ 1063.775866] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 1063.787437] usbcore: registered new interface driver ndiswrapper

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: b8:70:f4:72:f6:f0
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.5 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:28 ioport:3000(size=256) memory:c0404000-c0404fff(prefetchable) memory:c0400000-c0403fff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c2500000-c251ffff memory:c2700000-c270ffff(prefetchable)

$ iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.


```

---

### Post by hughh on 2011-09-13
I solved this&#8212;as well as some other problems most likely due to device recognition&#8212;by installing Natty Narwhal (11.04).  I'd have rather stayed with Lucid Lynx (10.04) since it's an LTS release and because I'm not thrilled about having to learn the new Unity interface right at the moment, but it's better than not having my wireless and monitor go unrecognized and therefore unfilterable.

---

### Post by pdc on 2011-09-14
It would be valuable to learn what the results of your data were now:

with 11.04...........

......if you are still out there, can  you repeat the data and we can see what the atheros has been configured to .......

---

