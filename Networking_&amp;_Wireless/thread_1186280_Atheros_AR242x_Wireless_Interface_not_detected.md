---
title: "Atheros AR242x Wireless Interface not detected"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by cupabj on 2009-06-13
Hi,

I have a Dell Vostro laptop with built-in Atheros AR242x wireless adapter. This laptop came installed with Ubuntu 8.04, with kernel version 2.6.19. Wireless does not work on this laptop while running in Ubuntu mode. Wireless works fine with Windowx-XP. I upgraded the kernel to 2.6.24 but it didn't help. While *lspci* does indicate that the wireless adapter is detected, *ifconfig* does not show the interface. BTW, this system has proprietary drivers for Atheros HAL and wireless already installed and enabled. I'll greatly appreciate any help resolving this problem. Here's some data that may prove useful:

```

$ lspci
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
0c:00.0 Network controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

$ lshw -C network
rk UNCLAIMED
       description: Network controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:22:19:e8:c2:44
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.100 latency=0 module=r8169 multicast=yes

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:19:e8:c2:44
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fee8:c244/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9259 errors:0 dropped:1308328571 overruns:0 frame:0
          TX packets:6261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12556706 (11.9 MB)  TX bytes:669469 (653.7 KB)
          Interrupt:220

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:82100 (80.1 KB)  TX bytes:82100 (80.1 KB)

$ dmesg|grep ath
[   26.177318] ath_hal: module license 'Proprietary' taints kernel.
[   26.213032] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   26.961474] ath_pci: 0.9.4

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by cupabj on 2009-06-17
I was able to get the internal wireless to work on this Dell laptop with the following procedure:

Install components essential for build:
```

sudo apt-get install build-essential

```

Ubuntu on my system has kernel ver 2.6.24. The following procedure is supposed to work for versions 2.6.22, 23, 24, 25, and 26:

Download compat-wireless-old.tar.bz2 from [http://wireless.kernel.org](http://wireless.kernel.org). For kernel verion 27 and above, download compat-wireless-2.6.tar.bz2:

```

wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2

sudo tar -jxvf compat-wireless-old.tar.bz2

```

change directory to the one created after extraction of the downloaded archive and build the code:

```

cd compat-wireless-2.6-old

sudo make

sudo make install

```

Unload the existing drivers:
```

sudo make unload

```

Now reboot the system. On reboot, the newly installed drivers should be loaded.

All the best!

---

