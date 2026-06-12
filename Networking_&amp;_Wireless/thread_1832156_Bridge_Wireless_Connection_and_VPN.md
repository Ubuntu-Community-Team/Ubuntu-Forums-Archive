---
title: "Bridge Wireless Connection and VPN"
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by robalrr on 2011-08-24
Hi, I have a problem I am trying to mount a openvpn for playing with my friends that live far away.

I mounted the vpn and it works ok with my laptop-server, but using a wired connection in the server. The problem is that my server uses normally a wireless connection, it is not possible to keeps the wired connection.

The problem comes because I can not configure the bridge for the wireless. 

The configuration that works was:

```
auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
        bridge_ports wlan0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

iface eth0 inet manual
  up ip link set $IFACE up promisc on
  down ip link set $IFACE down promisc off
```

Then I replaced the eth0 by the wireless interface and it did not work.

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet manual
        wpa-driver wext
        wpa-conf managed
        wpa-ssid WLAN_xxx
        wpa-ap-scan 2
        wpa-proto WPA
        wpa-pairwise TKIP
        wpa-group TKIP
        wpa-key-mgmt WPA-PSK
        wpa-psk 12345678901234567890

auto br0
iface br0 inet dhcp
        bridge_ports wlan0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
```

With the above configuration I got this error:

```
user@Iroh:/etc/network#sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          ssh stop/waiting
ssh start/running, process 5610
can't add wlan0 to bridge br0: Operation not supported

Waiting for br0 to get ready (MAXWAIT is 20 seconds).

ssh stop/waiting
ssh start/running, process 5734
                                                                         [ OK ]
```

and the result for ```
ifconfig
``` is:

```
user@Iroh:/etc/network# ifconfig 
br0       Link encap:Ethernet  HWaddr 72:a3:3f:fa:4a:c3  
          inet6 addr: fe80::70a3:3fff:fefa:4ac3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:10072 (10.0 KB)

br0:avahi Link encap:Ethernet  HWaddr 72:a3:3f:fa:4a:c3  
          inet addr:169.254.10.7  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:564521 (564.5 KB)  TX bytes:564521 (564.5 KB)

tap0      Link encap:Ethernet  HWaddr e6:84:d7:7e:f8:e0  
          inet6 addr: fe80::e484:d7ff:fe7e:f8e0/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2127893 errors:0 dropped:2117726 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:51850 (51.8 KB)  TX bytes:3214500623 (3.2 GB)

```

wlan0 did not start and br0 got a strange ip address through the avahi interface.

I just wanted to mount a VPN, that was able to go through the wlan0 interface. 

I read that is not possible create a bridge through a wireless interface because of the drivers. I tried using ```
iw dev wlan0 set 4addr on
``` but did not work.

My system info is: 

```
uname -a
Linux Iroh 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

lspci -vvnn | grep Network
01:01.0 Network controller [0280]: Ralink corp. RT2561/RT61 rev B 802.11g [1814:0302]
	Subsystem: Alpha Networks Inc. C54Ri v2 Wireless 11g PCI Adapter [1948:3c24]

lspci -k | grep Network --after-context 3
01:01.0 Network controller: Ralink corp. RT2561/RT61 rev B 802.11g
	Subsystem: Alpha Networks Inc. C54Ri v2 Wireless 11g PCI Adapter
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci
02:00.0 Ethernet controller: Atheros Communications L1 Gigabit Ethernet (rev b0)
```

Thank you for any suggestion, all info is useful.

---

