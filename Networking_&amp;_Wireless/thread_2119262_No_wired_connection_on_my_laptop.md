---
title: "No wired connection on my laptop"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by snalk on 2013-02-23
Hello all, I'm new on this community (this is my first post) and unfortunately my first post is about a problem. I have a problem with my wired network connection, I had read a lot of posts about this problem but I still didn't figure it out. The problem appears on my laptop(Asus k55vm).
Ifconfig command:
```

eth0      Link encap:Ethernet  HWaddr 10:bf:48:14:b1:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:182213 (182.2 KB)  TX bytes:182213 (182.2 KB)

wlan0     Link encap:Ethernet  HWaddr 44:6d:57:68:33:01  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::466d:57ff:fe68:3301/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219294 errors:0 dropped:0 overruns:0 frame:0
          TX packets:159936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:210990408 (210.9 MB)  TX bytes:167694681 (167.6 MB)

```lspci command:
```

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 7 Series Chipset Family 4-port SATA Controller [IDE mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.5 IDE interface: Intel Corporation 7 Series Chipset Family 2-port SATA Controller [IDE mode] (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 630M] (rev ff)
03:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)

```Thanks for help and sorry for my english (isn't my native language).

---

### Post by carl4926 on 2013-02-23
Can we see
```
lspci -nnk | grep -iA2 net
```

---

### Post by ali abry on 2013-02-23
sorry . my mistake. wrong post.

---

### Post by snalk on 2013-02-23
```

ady@ady-K55VM:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6627]
    Kernel driver in use: ath9k
--
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1447]
    Kernel driver in use: r8168


```

---

### Post by carl4926 on 2013-02-23
> **snalk said:**
> ```

ady@ady-K55VM:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6627]
    Kernel driver in use: ath9k
--
04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1447]
    Kernel driver in use: r8168


```

Drivers seem to be in place
Is there no connection when running the Live CD either?

---

### Post by snalk on 2013-02-23
Yes, I have the same problem with the Live CD, i don't have a wired connection. The cable works fine with a Windows laptop, maybe it's a hardware problem with the RJ-45 port (the laptop port).

---

### Post by carl4926 on 2013-02-23
I'm pretty sure it should just work
How is the wireless?

---

### Post by snalk on 2013-02-24
Thanks for the quick reply, I was able to solve the problem. It was a hardware problem, more exactly a bended wire (in the RJ-45 port) and when I was trying to connect the cable, the cable pins did not reach the port pins.
Thanks again.

---

