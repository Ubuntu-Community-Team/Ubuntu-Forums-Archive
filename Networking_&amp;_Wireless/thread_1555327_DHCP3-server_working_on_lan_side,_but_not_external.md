---
title: "DHCP3-server working on lan side, but not external?"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by smithnc07 on 2010-08-17
I've setup a Ubuntu box for dhcp. The external connector is wlan0, a usb wireless adapter.   The server dhcp side seems to be working fine as I'm able to plug another computer in and get an appropriate ip address, but then that computer can't ping or anything else to the outside world.   As I did this working thru a guide([https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)), now I'm just at a loss. Any one have an idea why the eth0 connected computers wouldn't be able to connect thru the wlan0? (and how to fix it?)  Smith

---

### Post by nbkr on 2010-08-18
Is there a proper route set? Does the WLAN Access point know who to reach the computers on the LAN?

Please show the output of the following

On a client and the dhcp server:
```

/sbin/route -n 
/sbin/ifconfig

```

---

### Post by smithnc07 on 2010-08-18
@nbkr, For the client(lan side computer) computer:
```
/sbin/ifconfig
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
    inet6 ::1 prefixlen 128 
    inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
    inet 127.0.0.1 netmask 0xff000000 
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    ether 00:17:f2:c2:4b:4a 
    inet6 fe80::217:f2ff:fec2:4b4a%en0 prefixlen 64 scopeid 0x4 
    inet 192.168.8.10 netmask 0xffffff00 broadcast 192.168.8.255
    media: autoselect (100baseTX <full-duplex,flow-control>)
    status: active
fw0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 2030
    lladdr 00:17:f2:ff:fe:7f:7c:b8 
    media: autoselect <full-duplex>
    status: inactive
en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
    ether 00:17:f2:9c:a2:bd 
    media: <unknown subtype> (<unknown type>)
    status: inactive

```For the DHCP server:
```

/sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:02:49:2f:d8  
          inet addr:192.168.8.1  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fe49:2fd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17595476 (17.5 MB)  TX bytes:6835 (6.8 KB)
          Interrupt:21 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:0d:60:e7:35:72  
          inet6 addr: fe80::20d:60ff:fee7:3572/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3930 (3.9 KB)  TX bytes:1836 (1.8 KB)

eth2      Link encap:Ethernet  HWaddr 00:01:02:37:5a:dd  
          inet6 addr: fe80::201:2ff:fe37:5add/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2438 (2.4 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:22 Base address:0x2400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116958 (116.9 KB)  TX bytes:116958 (116.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:cc:fa:6f:15  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:ccff:fefa:6f15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2041281 (2.0 MB)  TX bytes:63721 (63.7 KB)


/sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.8.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0



```

---

### Post by Iowan on 2010-08-18
Ordinarily, having two gateways specified causes problems. I'm not sure what happens if they are for the same interface... I didn't read the guide closely, so I didn't see where the gateway setup takes place.

---

### Post by smithnc07 on 2010-08-18
@Iowan you comment about having two gate ways, is that about how I have setup or the fact that there is a gateway from the wireless router that I'm getting the wireless from?   Maybe if I explain a little about what I'm trying to do. In the house I'm living at, the modem and router is at one end of the house. Way on the other side is where I need multiple devices to be connect online. What I was hoping to do is to use my Ubuntu box with a wireless adapter to receive the wireless signal, and then server(dhcp) that out to a switch for the other devices to plug into. Getting wireless adapters for each of the devices is not financially possible or even possible due to the limit of mac filtered addressed in the main wireless router.   Is that something feasible or am I going about this all wrong?

---

### Post by Iowan on 2010-08-18
> /sbin/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.8.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
[COLOR="Red"]0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0[/COLOR]These are the two "gateways" I referenced. The only noticeable difference is the metric - but having it listed twice is ... curious.

---

### Post by nbkr on 2010-08-19
I agree, those two gateways can cause troubles, but I don't think that this is causing the current problems.

I'm guessing, but I believe the problem is to be solved on the WLAN Access Point. This machine probably doesn't know that it can reach the network 192.168.8.0/24 via the IP 192.168.1.104. There is probably a route missing.

---

