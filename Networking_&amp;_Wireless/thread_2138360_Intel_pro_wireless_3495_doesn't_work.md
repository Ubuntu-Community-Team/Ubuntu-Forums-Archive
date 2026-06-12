---
title: "Intel pro wireless 3495 doesn't work"
date: 2013-04-23
forum: Networking &amp; Wireless
---

### Post by badruk on 2013-04-23
As seen in other topics i found my wireless card having problems with Ubuntu. I already tried everything I saw and nothing changed... I hope to find an way to fix it soon :)

I'm actually using an acer5610z with ubuntu 32bit 12,10 :)

Here's my iwconfig and some others asked lines:

```
badruk@badruk-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

```

```
badruk@badruk-laptop:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
badruk@badruk-laptop:~$ dmesg | grep iwl
[ 3000.094804] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 3000.094815] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[ 3643.280844] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 3643.280851] iwl3945: Copyright(c) 2003-2011 Intel Corporation

```

Any ideas?

---

### Post by chili555 on 2013-04-23
How about showing us:```
lspci -nn | grep 0280
sudo lshw -C network
```Thanks.

---

### Post by badruk on 2013-04-23
Here they are. I'd also like to try lubuntu soon, will the fix be the same over that distro as well ( but this is OT )

I'm actually connected via ethernet :)

```
badruk@badruk-laptop:~$ lspci -nn | grep 0280
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
badruk@badruk-laptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:d0000000-d0003fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth1
       version: 02
       serial: 00:1b:38:72:67:18
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.3 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:d0100000-d0101fff


```

---

### Post by chili555 on 2013-04-23
The fix is the same. You wireless card is not an Intel 3945. It is:> Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311]With the ethernet connected temporarily, please do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```Your wireless should now be working.

---

### Post by badruk on 2013-04-23
> **chili555 said:**
> The fix is the same. You wireless card is not an Intel 3945. It is:With the ethernet connected temporarily, please do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
```Your wireless should now be working.

Thank you a lot. Actually i thought my card was that 'due to linlaptop :(

Will this work on lubuntu as well? :)

I'll edit with "resolved"

---

### Post by chili555 on 2013-04-23
> Will this work on lubuntu as well?Yes, and on any other *buntu as well. The windowing manager, in the case of lubuntu being LXDE, has no bearing on the Broadcom wireless.

---

