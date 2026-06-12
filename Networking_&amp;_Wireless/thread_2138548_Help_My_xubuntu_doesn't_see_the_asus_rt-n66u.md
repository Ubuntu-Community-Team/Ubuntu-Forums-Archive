---
title: "Help: My xubuntu doesn't see the asus rt-n66u"
date: 2013-04-24
forum: Networking &amp; Wireless
---

### Post by ubunlilluz on 2013-04-24
Hi,
i've just bought my first router, the asus rt-n66u. I procede connecting the cable fron lan gate of the routher to the one of my pc. The first problem i see is that the led of the gate is orange but maybe is due to not configured connection. Now if digit the ip of router 192.168.1.1 it tells me
```
 	  	
Connection time out
192.168.1.1 server is taking too long to respond.
The site may be unavailable or overload. Try again in a few moments.
If you are unable to load any pages, check your computer's network connection.
If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the web.
```

so i disabled the firewall by
```
sudo gufw disable
```

and i've set "no proxy" on Firefox net card configuration. Still i can't reach the router.

it seems that the pc doesn't see the router, then if a digit

```
drlillux@drlillux-P55A-UD4:~$ ifconfig
eth0      Link encap:Ethernet  addressHW 6c:f0:49:54:c9:2c 
          address inet6: fe80::6ef0:49ff:fe54:c92c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32333 errors:0 dropped:57 overruns:0 frame:0
          TX packets:7425 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000
          Byte RX:8164072 (8.1 MB)  Byte TX:1109505 (1.1 MB)

lo        Link encap:Loopback local 
          address inet:127.0.0.1  Mask:255.0.0.0
          address inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8094 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0
          Byte RX:586191 (586.1 KB)  Byte TX:586191 (586.1 KB)

drlillux@drlillux-P55A-UD4:~$ 
```

then

```
drlillux@drlillux-P55A-UD4:~$  lspci | grep -i ethernet
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
drlillux@drlillux-P55A-UD4:~$ 
```

```
drlillux@drlillux-P55A-UD4:~$ dmesg | grep eth0
[    0.902010] r8169 0000:06:00.0: eth0: RTL8168d/8111d at 0xffffc90000672000, 6c:f0:49:54:c9:2c, XID 083000c0 IRQ 54
[    0.902013] r8169 0000:06:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   12.590211] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.711734] r8169 0000:06:00.0: eth0: link down
[   14.711753] r8169 0000:06:00.0: eth0: link down
[   14.712039] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.712269] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.603661] r8169 0000:06:00.0: eth0: link up
[   16.603927] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  568.322625] r8169 0000:06:00.0: eth0: link down
[  572.619451] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  612.471760] r8169 0000:06:00.0: eth0: link up
[  612.472469] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  622.603382] r8169 0000:06:00.0: eth0: link down
[  625.399123] r8169 0000:06:00.0: eth0: link up
[  898.604290] r8169 0000:06:00.0: eth0: link down
[  905.851823] r8169 0000:06:00.0: eth0: link up
drlillux@drlillux-P55A-UD4:~$ 
```

moreover my /etc/network/interface contains?

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

i'm working with xubuntu 12.10
Somebody can help me please

---

### Post by ubunlilluz on 2013-04-24
i've tried with my laptop with win xp and it works so i exclude hardware problem to router and cables

---

