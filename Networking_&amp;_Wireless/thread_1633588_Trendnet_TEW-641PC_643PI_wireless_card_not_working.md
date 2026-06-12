---
title: "Trendnet TEW-641PC_643PI wireless card not working with ubuntu"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by TheTaoOfBill on 2010-11-29
I installed the driver using Ndiswrapper and it says that it installed correctly and that the hardware is present, but it still is not letting me connect to wireless.  Network manager does not show any available wireless networks, just as if there were no wireless card installed at all.  The wireless card works in windows.

I'm running Ubuntu 10.04 LTS.

this is what I get for iwconfig
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


as you can see, it does not recognize any wireless installed, even though Ndiswrapper says that there is a successfully installed driver with the hardware present.

I have no idea what to do, I've tried everything I can think of, but I'm a little new to Ubuntu so I'm totally lost.  Any advice is appreciated.  Let me know if you need more info.

---

### Post by Kernelingus on 2010-11-29
In terminal, run

```
lspci
```

And post your results here.

---

### Post by TheTaoOfBill on 2010-11-29
lspci
00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403 (rev 01)
04:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
05:05.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190

---

### Post by TheTaoOfBill on 2010-11-29
Anyone have any ideas? This is killing me as I need this working for school!

---

### Post by TheTaoOfBill on 2010-11-30
Still looking for help...

---

### Post by berserkpi on 2011-05-17
Same problem here I'm on Ubuntu 11.04. The TEW-643PI is by no means working.

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
03:02.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

```

ndiswrapper says everything is ok...

```
net819xp : driver installed
	device (10EC:8190) present
```

ifconfig doesn't show a wlan:


```
eth0      Link encap:Ethernet  HWaddr e0:69:95:58:1f:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92497 (92.4 KB)  TX bytes:92497 (92.4 KB)
```

Thanks for your help.

---

### Post by chili555 on 2011-05-17
Let's see if there are any informative messages. Please run and post:```
dmesg | grep ndis
lsmod | grep ndis
```Thanks.

---

### Post by rcgtrash on 2011-10-07
Hi,

I'm having a similar problem as described above.  I believe the only difference is that I'm using Kubuntu 11.04

I downloaded the rtldriver and installed it using ndiswrapper:
kori@Kori-Central:~$ ndiswrapper -l
net819xp : driver installed
        device (10EC:8190) present

When searching for wlan0 I get:

kori@Kori-Central:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:30:1b:ad:65:62 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.137/24 brd 192.168.1.255 scope global eth0
    inet6 2002:478e:4364:0:230:1bff:fead:6562/64 scope global dynamic 
       valid_lft 29sec preferred_lft 19sec
    inet6 fe80::230:1bff:fead:6562/64 scope link 
       valid_lft forever preferred_lft forever
kori@Kori-Central:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
kori@Kori-Central:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:30:1b:ad:65:62 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.137/24 brd 192.168.1.255 scope global eth0
    inet6 2002:478e:4364:0:230:1bff:fead:6562/64 scope global dynamic 
       valid_lft 29sec preferred_lft 19sec
    inet6 fe80::230:1bff:fead:6562/64 scope link 
       valid_lft forever preferred_lft forever
kori@Kori-Central:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


 Here is my output:  

kori@Kori-Central:~$ dmesg | grep ndis
[   13.694622] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   13.943732] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   13.943756] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   13.943771] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   13.943784] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   13.943797] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   13.943811] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   13.943828] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   13.943843] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   13.943858] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   13.943873] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   13.943888] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   13.943903] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   13.943918] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   13.943932] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   13.943946] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   13.944080] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   13.944096] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   13.944110] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   13.944130] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   13.944147] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   13.944167] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   13.944181] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   13.944195] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   13.944226] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   13.944240] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   13.944257] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   13.944271] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   13.944285] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   13.944300] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   13.944325] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   13.944335] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net819xp'
[   13.946057] ndiswrapper (load_wrap_driver:108): couldn't load driver net819xp; check system log for messages from 'loadndisdriver'
[   14.003610] usbcore: registered new interface driver ndiswrapper
[ 1338.411279] usbcore: deregistering interface driver ndiswrapper
[ 1338.413068] ndiswrapper (ntoskernel_exit:2677): object f4329a20(2) was not freed, freeing it now
[ 1338.433275] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 1338.463241] ndiswrapper (check_nt_hdr:147): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
[ 1338.463249] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net819xp'
[ 1338.464251] ndiswrapper (load_wrap_driver:108): couldn't load driver net819xp; check system log for messages from 'loadndisdriver'
[ 1338.464355] usbcore: registered new interface driver ndiswrapper



kori@Kori-Central:~$ lsmod | grep ndis
ndiswrapper           192828  0

I did note that when I typed in sudo modprobe ndiswrapper nothing appeared to happen

Lost n' Confused in Linux Land

---

### Post by chili555 on 2011-10-08
> couldn't load driver net819xp; check system log for messages from 'loadndisdriver'Let's do just that. Please run and post:```
sudo cat /var/log/syslog | grep ndis | tail -n20
```Sometimes, this error appears because the Windows Vista or 7 .inf file was used. Ndiswrapper is designed to use the Windows **XP** .inf and .sys files. Which is yours?

---

### Post by zepolmot on 2011-10-26
Any progress on either of these, can't get my TEW-643PI recognized  either, only getting "UNCLAIMED" from lshw -C network after trying ndiswrapper telling me everything went smoothly.  Have tried the XP drivers and the 7 drivers with no luck

---

### Post by zepolmot on 2011-10-26
bump

---

### Post by Barbelyth on 2012-04-03
I'm always unsure as to whether start a new thread or just add my impetus to an already moving one. I'm guessing it might be more useful to just post my problem here since so many have expressed the exact problem I have. 

I recently installed Ubuntu and have been enjoying the new OS except that I am forced to used a wired connection since the wireless is not working at all. I also have a TEW-641PC_643PI card.

I've followed all the steps in installing Ndiswrapper. I've located Windows XP drivers from my card manufacturers (Trendnet), from the Chipset manufacturers (Realtek) and from a third party repo (drivers.com or some such website) and they all spit at me the same error. 

Here is the result of 'sudo iwconfig'  & 'dmesg | grep -e ndis -e wlan'

> lo        no wireless extensions.

eth0      no wireless extensions.


> [   13.366801] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   18.544348] ndiswrapper (check_nt_hdr:147): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
[   18.544355] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net819xp'
[   18.544670] ndiswrapper (load_wrap_driver:108): couldn't load driver net819xp; check system log for messages from 'loadndisdriver'
[   18.544758] usbcore: registered new interface driver ndiswrapper


As per Chilli's request here is also the result of 'sudo cat /var/log/syslog | grep ndis | tail -n20'

> Apr  3 17:15:42 barbelith-P55M-UD2 kernel: [   13.450739] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Apr  3 17:15:46 barbelith-P55M-UD2 loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net819xp
Apr  3 17:15:46 barbelith-P55M-UD2 kernel: [   18.586849] ndiswrapper (check_nt_hdr:147): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
Apr  3 17:15:46 barbelith-P55M-UD2 kernel: [   18.586856] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net819xp'
Apr  3 17:15:46 barbelith-P55M-UD2 kernel: [   18.587134] ndiswrapper (load_wrap_driver:108): couldn't load driver net819xp; check system log for messages from 'loadndisdriver'
Apr  3 17:15:46 barbelith-P55M-UD2 kernel: [   18.587196] usbcore: registered new interface driver ndiswrapper
Apr  3 17:48:42 barbelith-P55M-UD2 kernel: [   13.366801] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Apr  3 17:48:46 barbelith-P55M-UD2 loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net819xp
Apr  3 17:48:46 barbelith-P55M-UD2 kernel: [   18.544348] ndiswrapper (check_nt_hdr:147): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
Apr  3 17:48:46 barbelith-P55M-UD2 kernel: [   18.544355] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net819xp'
Apr  3 17:48:46 barbelith-P55M-UD2 kernel: [   18.544670] ndiswrapper (load_wrap_driver:108): couldn't load driver net819xp; check system log for messages from 'loadndisdriver'
Apr  3 17:48:46 barbelith-P55M-UD2 kernel: [   18.544758] usbcore: registered new interface driver ndiswrapper


Much like everyone else on this board I'm stumped. The drivers are clearly 32-bit and as is my kernel. Why am getting 'bad magic'??

Any help would be greatly appreciated (not just by me as it seems).

---

### Post by chili555 on 2012-04-03
> The drivers are clearly 32-bit and as is my kernel. Why am getting 'bad magic'??Before we proceed, let's verify. Please post the first 10-12 lines of the net819xp.inf file so we can review it. Also, please run and post:```
arch
lspci -nn | grep 0280
```Was the .sys file or files in the same directory when you loaded the .inf? Is a copy now in /etc/ndiswrapper?

---

