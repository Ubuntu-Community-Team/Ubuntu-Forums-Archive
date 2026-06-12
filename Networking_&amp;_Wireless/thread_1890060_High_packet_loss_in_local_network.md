---
title: "High packet loss in local network"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by arepisky on 2011-12-02
Hi,

I just installed Kubuntu 11.04 (64-bit) at work and realized Internet was a lot slower than in Windows. I ran ping to our router and the result was 46 % packet loss. In Windows it was 0 %.

Some printouts:

ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 50:e5:49:37:ad:7a  
          inet addr:195.178.71.129  Bcast:195.178.71.255  Mask:255.255.254.0
          inet6 addr: fe80::52e5:49ff:fe37:ad7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8176 errors:0 dropped:8216 overruns:0 frame:8176
          TX packets:4115 errors:0 dropped:11 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3958412 (3.9 MB)  TX bytes:801103 (801.1 KB)
          Interrupt:43 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2022 (2.0 KB)  TX bytes:2022 (2.0 KB)
```

By the way weird thing is, that the connection icon in the lower right corner (showing ethernet connector) is empty (cable unplugged), but network connection works (though poorly). I entered my TCP/IP settings during the install process (I used alternate CD).

lspci (only network adaper shown):
```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```

hwinfo --netcard:
```
> hal.1: read hal dataprocess 2010: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
35: PCI 300.0: 0200 Ethernet controller                         
  [Created at pci.318]
  Unique ID: rBUF.5rbhBgx50x4
  Parent ID: bSAa.8EaoC3U4NBD
  SysFS ID: /devices/pci0000:00/0000:00:0a.0/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8168 "RTL8111/8168B PCI Express Gigabit Ethernet controller"
  SubVendor: pci 0x1458 "Giga-byte Technology"
  SubDevice: pci 0xe000 "GA-EP45-DS5 Motherboard"
  Revision: 0x06
  Driver: "r8169"
  Driver Modules: "r8169"
  Device File: eth0
  I/O Ports: 0xce00-0xceff (rw)
  Memory Range: 0xfdfff000-0xfdffffff (ro,non-prefetchable)
  Memory Range: 0xfdff8000-0xfdffbfff (ro,non-prefetchable)
  IRQ: 43 (23592 events)
  HW Address: 50:e5:49:37:ad:7a
  Link detected: yes
  Module Alias: "pci:v000010ECd00008168sv00001458sd0000E000bc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #11 (PCI bridge)

```

Thanks a lot for any hints.

---

### Post by jonobr on 2011-12-02
Hello

It could be your MTU size,
your ifconfig shows your using MTU of 1500

try checking against windows, it may be 1492
If it is try changing that and see if it improves things
You cand do it temporarily by
```
sudo ifconfig eth0 mtu 1492
```

and see if things get slightly better

---

### Post by arepisky on 2011-12-03
Thanks. I'll try that as soon as I get to that computer, which will be on Monday.

---

