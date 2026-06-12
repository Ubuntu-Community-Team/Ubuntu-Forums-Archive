---
title: "GA511 (RTL-8169) no link detected on Ubuntu Server 12.04 LTS fresh install"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by Jasps on 2013-05-10
Hello all,

I recently managed to get an old acer travelmate 2420  laptop which I'm using as a server. As it only has an internal 100Mbit  Ethernet connection I bought an Netgear GA511 PC card which supports gigabit  ethernet (it has an RTL8169 chip). I however cannot get it to work. 

So what is the problem?
ethtool eth0 returns Link detected: no (cable is plugged in)

I have read allot about bugs with the r8169 driver. So what have i tried:

- Installed the r8168 driver; Device remained unclaimed (lshw -C network command)
- Installed the latest driver from Realtek; link detected: no.
- Apply: [http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem;](http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem;) problem remains
- rmmod r8169; modprobe r8169;problem remains
And some more stuff I already forgot.


ethtool -i eth0

driver: r8169
version: 6.017.00-NAPI
bus-info: 0000:07:00.0


lspci -v returns:

Ethernet Controller: Realtek Semi....  RTL-8169 Gigabit Ethernet (rev 10)
..
Kernel driver in use: r8169
Kernel modules: r8169

So at the moment I'm running driver version 6.017.00 (r8169). Link is not detected. 

I'm hoping you can help me out, if you need more info let me know! 

Thanks!
Jasper

---

### Post by praseodym on 2013-05-10
Please show:
```

uname -a
cat /etc/network/interfaces
dmesg | grep r8
lsmod
ifconfig -a
cat /etc/resolv.conf
```

---

### Post by Jasps on 2013-05-10
Thanks for your quick response!

uname -a:
```

Linux Klootzak 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux

```

cat /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

```
Comment: also used static ip address but same problem. Eth1 is onboard

dmesg | grep r8:
```

[15.424470] r8169 Gigabit Ethernet driver 6.017.00-NAPI loaded
[15.424504] r8169 0000:07:00.0: enabling device (0000 -> 0003)
[15.424547] r8169 0000:07:00.0: setting latency timer to 64
[15.425363] r8169: This product is covered by one or more of the following patents: xxxxx
[15.484390] r8169: eth0: link down

```

lsmod
```

Module                  Size  Used by
joydev                 17394  0
r8169                  31947  0
acer_wmi               27975  0
sparse_keymap          13659  1 acer_wmi
microcode              18396  0
pcmcia                 39855  0
psmouse                91022  0
serio_raw              13032  0
yenta_socket           27465  0
pcmcia_rsrc            18368  1 yenta_socket
snd_intel8x0           33463  0
i915                  470823  1
pcmcia_core            21512  3 pcmcia,yenta_socket,pcmcia_rsrc
ext2                   67991  1
snd_ac97_codec        106118  1 snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
lpc_ich                16993  0
snd_pcm                81124  2 snd_intel8x0,snd_ac97_codec
drm_kms_helper         47459  1 i915
snd_timer              28932  1 snd_pcm
snd                    62675  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore              14636  1 snd
wmi                    18745  1 acer_wmi
snd_page_alloc         14109  2 snd_intel8x0,snd_pcm
mac_hid                13078  0
drm                   240232  2 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
video                  19070  2 acer_wmi,i915
lp                     17456  0
parport                40931  1 lp
8139too                23312  0
8139cp                 26760  0

```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:1e:2a:bd:cf:2d
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:0a:e4:f3:9a:fa
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 KB)  TX bytes:240 (240.0 KB)

```

There is nothing in /etc/resolv.conf

---

### Post by praseodym on 2013-05-10
Any other LAN devices? There are two more drivers loaded, 8139cp and 8139too. Are they for eth1?
```
lspci -nnk | grep -iA2 net
cat /etc/udev/rules.d/70-persistent-net.rules
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
```

---

### Post by Jasps on 2013-05-11
There is indeed an onboard LAN chip, eth1 which uses 8139too. This one works when I plug in a cable, but it's only 100Mbit. 


lspci -nnk | grep -iA2 net
```

06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
Subsystem: Acer Incorporated pALI] Device [1025:006a]
Kernel driver is use: 8139too
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 [10ec:8169] (rev 10)
Subsystem: Netgear Device [1385:5200]
Kerner driver in use: r8169
Kernel modules: r8169

```

```


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:06:07.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0a:e4:f3:9a:fa", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:06:09.0/0000:07:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:2a:bd:cf:2d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```

Still linked detected no

---

### Post by praseodym on 2013-05-11
There are 3 drivers loaded:
```

sudo modprobe -rfv 8139too
sudo modprobe -rfv 8139cp
sudo modprobe -rfv r8169
sudo modprobe -v r8169
sudo modprobe -v 8139too
echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Check:
```

dmesg | egrep '813|r8|eth'
ifconfig -a
```

---

### Post by Jasps on 2013-05-12
dmesg | egrep '813|r8|eth'
```

pci 0000:06:07.0: [10ec:8139] type 00 class 0x020000
8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22,2004)
8139cp 0000:06:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
8139too: 8139too Fast Ethernet driver 0.9.28
8139too 000:06:07.0 eth0: RealTek RTL8139 at 0x00013000, 00:0a:e4:f3:9a:fa, IRQ 20
IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
8139too 0000:06:07.0: eth1: link down
IPv6 ADDRCONF(NETDEV_UP) eth1: link is not ready
r8169 Gigabit Ethernet driver 6.017.00-NAPI loaded
r8169 0000:07:00.0: enabling device (0000 -> 0003)
r8169 0000:07:00.0: setting latency timer to 64
r8169: This product is covered by one or more of the following patents: xxxx
eth0: RTL8169SB/8110SB at 0xf8512000, 00:1e:2a:bd:cf:2d, IRQ 22
r8169: eth0: link down
IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
r8169 Gigabit Ethernet driver 6.017.00-NAPI loaded
r8169: This product covered by one or more of the following patents: xxx
eth0: RTL8169SB/8110SB at 0xf8428000, 00:1e:2a:bd:cf:2d, IRQ 22
r8169: eth0: link down
IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
8139too: 8139too Fast Ethernet driver 0.9.28
8139too 0000:06:07.0: eth1: RealTek RTL8139 at 0x00013000, 00:0a:e4:f3:9a:fa, IRQ 20
8139too 0000:06:07.0: eth1: link down
IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready

```

```

eth0      Link encap:Ethernet  HWaddr 00:1e:2a:bd:cf:2d
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:22 Base address:0xe000

  eth1      Link encap:Ethernet  HWaddr 00:0a:e4:f3:9a:fa
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

 lo        Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:95 errors:0 dropped:0 overruns:0 frame:0
           TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:7088 (7.0 KB)  TX bytes:7088 (7.0 KB)

```

Note: I only have a cable plugged in the r8169 card, not the onboard card. Ethernet via the onboard card still works after plugging in the cable and restarting the networking service.

---

### Post by praseodym on 2013-05-12
Please install ethtool and show:
```

sudo apt-get install ethtool
sudo ethtool eth0
```

---

### Post by Jasps on 2013-05-12
```

Settings for eth0:
Supported ports: [TP]
Supported link modes: 10baseT/Half 10baseT/Full
                               100baseT/Half 100baseT/Full
                               1000baseT/Full
Supported pause frame use: No
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
                               100baseT/Half 100baseT/Full
                               1000baseT/Full
Advertised pause frame use: No
Advertised auto-negotiation: Yes
Speed: 100Mb/s
Duplex: Half
Port: Twisted Pair
PHYAD: 0
Transceiver: internal
Auto-negotiation: on
MDI-X: Unknown
Supports Wake-on: pumbg
Wake-on: g
Current message level: 0x00000033 (51)
                                drv probe ifdown ifup
Link detected: no


```

---

### Post by praseodym on 2013-05-12
Try these steps each for itself:
[LIST]
[*]```

sudo ethtool -s eth0 speed 100 duplex full
sudo ethtool eth0
```
[*]```

sudo ethtool -s eth0 speed 1000 duplex full
sudo ethtool eth0
```
[*]```

sudo ethtool -s speed 1000 autoneg off
sudo ethtool eth0
```
[/LIST]

---

### Post by Jasps on 2013-05-12
First one works! Problem solved!

Thanks a lot for your time and effort!

---

