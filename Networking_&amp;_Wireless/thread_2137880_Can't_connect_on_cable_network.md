---
title: "Can't connect on cable network"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by rrrobles on 2013-04-22
I can't connect a cable network to my new notebook. I have made this many times on another computers, but this time I got something wrong.

My system is:

Dell Vostro 3460
Ubuntu 11.10

Result of lspci shows my ethernet controller as the last item:

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB Controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1d.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 0de9 (rev ff)
02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications Device 1091 (rev 10)

```

Result of ifconfig:

```
lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:549 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:549 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:44116 (44.1 KB) TX bytes:44116 (44.1 KB)

wlan0     Link encap:Ethernet  Endereço de HW e0:06:e6:de:6a:1f  
          inet end.: 10.0.0.101  Bcast:10.0.0.255  Masc:255.255.255.0
          endereço inet6: fe80::e206:e6ff:fede:6a1f/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:2435 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:2361 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:2114707 (2.1 MB) TX bytes:430225 (430.2 KB)
```

Result of ip addr:

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether e0:06:e6:de:6a:1f brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.101/24 brd 10.0.0.255 scope global wlan0
    inet6 fe80::e206:e6ff:fede:6a1f/64 scope link 
       valid_lft forever preferred_lft forever
```

Result of ls /sys/class/net:

```
lo  wlan0
```

I should not have an eth0 here?

---

### Post by Iowan on 2013-04-22
What does **sudo lshw -C network** reveal?

Is there an eth0 interface configured in Network Manager?

---

