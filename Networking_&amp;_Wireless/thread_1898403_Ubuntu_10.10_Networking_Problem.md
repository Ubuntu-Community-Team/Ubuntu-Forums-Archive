---
title: "Ubuntu 10.10 Networking Problem"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by neel_basu on 2011-12-21
even few days go it was working perfectly. suddenly There is no internet. I can't even reach `192.168.0.1` . I've a dual boot with window. with which I can reach to internet.

`lspci` says :

    ```

    00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
    00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
    00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
    00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
    00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
    00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
    00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
    00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
    00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
    00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
    00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 04)
    00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
    ** 01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10) 
```

`lshw -class network` says I am using `r1869` driver:

```

    *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth0
       version: 10
       serial: 00:13:d4:07:43:2f
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:a000(size=256) memory:d1000000-d10000ff memory:28000000-2801ffff

```
and that `r8169` module also appears in `lsmod`:
```

    r8169                  36841  0
    mii                     4425  1 r8169


```But there is no internet. What Can I do ?

---

### Post by neel_basu on 2011-12-22
bump

---

### Post by jonobr on 2011-12-22
try posting 

```
ifconfig 
``` results 
and
```
cat /etc/network/interfaces
```

also 

```
/etc/resolv.conf
```

---

