---
title: "Intel 8255xER/82551IT Fast Ethernet Controller"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by autagi on 2009-10-19
Hi,
I have just installed  Ubuuntu server 8.04 2.6.24-24.
My system has Intel 8255xER/82551IT Fast Ethernet Controller, but I can't see this device with:
ifconfig -a
 can you help me?
thanks

---

### Post by chili555 on 2009-10-19
I think this is supported by the module *e100*. Please do:```
sudo modprobe e100
sudo ifconfig eth0 up
ifconfig
```Do you have an interface? Can you connect?

---

### Post by autagi on 2009-10-19
my system has 2 interfaces
the second one is Intel 82801DB PRO/100 seen as eth0.
The first one is Intel 8255xER/82551IT so I receive:
sudo ifconfig eth1
eth1: error fetching interface information: Device not found

---

### Post by chili555 on 2009-10-19
Please do:```
sudo modprobe e100
sudo lshw -C network
```Please post the results.

---

### Post by autagi on 2009-10-20
thanks for your help!

 lshw -C network
says:
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: AR5413 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=28 mingnt=10
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: 8255xER/82551IT Fast Ethernet Controller
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=56 mingnt=8
  *-network:2
       description: Ethernet interface
       product: 82801DB PRO/100 VE (CNR) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 82
       serial: 00:13:95:03:17:b5
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=10.16.44.133 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

---

### Post by chili555 on 2009-10-20
So, are you saying that you are trying to get ***both*** interfaces going? *eth0* has an IP address and seems to be working correctly.

---

### Post by autagi on 2009-10-20
Yes, eth0 (82801DB PRO/100 VE (CNR) Ethernet Controller) works fine,
the other one no

---

### Post by chili555 on 2009-10-20
Please let us see:```
dmesg | grep e100
```Thanks.

---

### Post by autagi on 2009-10-20
```
root@VMC:~# dmesg | grep e100
[   51.796127] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   51.796133] e100: Copyright(c) 1999-2006 Intel Corporation
[   52.145530] e100: 0000:01:05.0: e100_eeprom_load: EEPROM corrupted
[   52.145598] e100: probe of 0000:01:05.0 failed with error -11
[   52.168360] e100: eth0: e100_probe: addr 0xff7ff000, irq 5, MAC addr 00:13:95:03:17:b5
[   64.064631] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex

```
but I think it is refered to working ethernet interface

---

### Post by chili555 on 2009-10-20
> but I think it is refered to working ethernet interfaceI do not:> *-network:1 UNCLAIMED
description: Ethernet controller
product: 8255xER/82551IT Fast Ethernet Controller
vendor: Intel Corporation
physical id: 5
bus info: pci@[COLOR="Red"]0000:01:05.0[/COLOR]> [COLOR="Red"]0000:01:05.0[/COLOR]: e100_eeprom_load: EEPROM corrupted
Please try this:```
sudo rmmod -f e100
sudo modprobe e100 eeprom_bad_csum_allow=1
ifconfig
```Does eth1 now appear? If so, we can make this change permanent.

---

### Post by autagi on 2009-10-21
modprobe reports this error message
```
[FONT=Arial][SIZE=2][COLOR=#ff0000][COLOR=Black]
[ 1750.520980] e100: 0000:01:05.0:  e100_eeprom_load: EEPROM corrupted
[ 1750.522710] e100: 0000:01:05.0:  e100_probe: Invalid MAC address from EEPROM, you MUST configure one.[/COLOR]
[/COLOR][/SIZE][/FONT]
```and ifconfig eth0
```

[FONT=Arial][SIZE=2][COLOR=Black]eth0      Link encap:Ethernet  HWaddr  00:00:00:00:00:00
          BROADCAST MULTICAST  MTU:1500   Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0  frame:0
          TX packets:0 errors:0 dropped:0 overruns:0  carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0  B)  TX bytes:0 (0.0 B)[/COLOR][/SIZE][/FONT]


```

---

### Post by chili555 on 2009-10-21
This looks like it is from *dmesg*. Was there an error or warning at the terminal when you did the commands? You might also try:```
sudo rmmod -f e100
sudo modprobe eepro100
ifconfig
```I'd like to see the entire *ifconfig*, not just eth0. Thanks.

---

### Post by autagi on 2009-10-26
It seems to be an eeprom problem...so I'll try to resolve it.
thanks

---

### Post by inox84 on 2009-10-31
> **autagi said:**
> It seems to be an eeprom problem...so I'll try to resolve it.
thanks

Run eepro100-diag (nictools-pci package) to examine your EEPROM content.
If everything is fine

$ modprobe -r e100
$ modprobe e100 eeprom_bad_csum_allow=1

should make things just fine :)

---

