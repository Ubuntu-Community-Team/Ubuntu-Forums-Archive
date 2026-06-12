---
title: "upgraded to 8.10 - can't reach internet now"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by MountainX on 2009-02-21
How do I further diagnose this problem?

I was running Hardy (64bit) and just upgraded this computer to 8.10 (64bit). Now this computer cannot reach the internet, but the strange thing is that it is fully connected to the LAN. The router is a DHCP server and this computer gets an IP address (and of course it can ping the router and any other computer on the LAN). I can SSH into this computer from other computers on the LAN too.

Other computers can browse the Internet. Only this one can't. 

Here is ping output for LAN - succeeds:
```
myuser@UbuntuServer:~$ ping 10.10.99.251
PING 10.10.99.251 (10.10.99.251) 56(84) bytes of data.
64 bytes from 10.10.99.251: icmp_seq=1 ttl=64 time=5.47 ms
--- 10.10.99.251 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3031ms
rtt min/avg/max/mdev = 1.269/2.392/5.471/1.780 ms
```

Here is ping for WAN - fails:
```
myuser@UbuntuServer:~$ ping yahoo.com
PING yahoo.com (68.180.206.184) 56(84) bytes of data.
--- yahoo.com ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5015ms

myuser@UbuntuServer:~$ ping 68.180.206.184
PING 68.180.206.184 (68.180.206.184) 56(84) bytes of data.
--- 68.180.206.184 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4014ms

myuser@UbuntuServer:~$ ping 76.96.54.13
PING 76.96.54.13 (76.96.54.13) 56(84) bytes of data.
--- 76.96.54.13 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 8999ms
```

Here is ifconfig output (all addresses have been changed)
```
myuser@UbuntuServer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:xx:xx:zz  
          inet addr:10.10.99.5  Bcast:10.10.99.255  Mask:255.255.255.0
          inet6 addr: 8880::000:e9ff:3333:1111/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:529378 (529.3 KB)  TX bytes:651749 (651.7 KB)

eth1      Link encap:Ethernet  HWaddr aa:00:00:xx:xx:yy  
          inet addr:10.10.99.6  Bcast:10.10.99.255  Mask:255.255.255.0
          inet6 addr: 8880::000:e9ff:3333:1112/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87361 (87.3 KB)  TX bytes:11316 (11.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:952 (952.0 B)  TX bytes:952 (952.0 B)
```

Here is some of dmesg output:
```
[  355.071888] eth1: no IPv6 routers present
[  355.101886] eth0: no IPv6 routers present
[  359.556002] Bluetooth: Core ver 2.13
[  359.557291] NET: Registered protocol family 31
[  360.984636] mtrr: type mismatch for fd000000,800000 old: write-back new: write-combining
[  361.011783] mtrr: no MTRR for fd000000,800000 found
[  361.013359] mtrr: type mismatch for fd000000,800000 old: write-back new: write-combining
[ 3474.431779] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3474.541784] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3477.270380] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[ 3477.275927] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3477.560375] e1000: eth1: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[ 3477.565975] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 3487.990011] eth1: no IPv6 routers present
[ 3488.130011] eth0: no IPv6 routers present
```


Here is ping for _other computer_ on same LAN (same router too):
```
otheruser@OtherUbuntu:~$ ping comcast.net
PING comcast.net (76.96.54.13) 56(84) bytes of data.
64 bytes from www4.comcast.net (76.96.54.13): icmp_seq=1 ttl=50 time=56.1 ms
64 bytes from www4.comcast.net (76.96.54.13): icmp_seq=2 ttl=50 time=52.2 ms

--- comcast.net ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 52.259/54.216/56.173/1.957 ms
otheruser@OtherUbuntu:~$ 
```

---

### Post by Iowan on 2009-02-21
Two ethernet interfaces in the same subnet might be causing a problem.

---

### Post by MountainX on 2009-02-21
> **Iowan said:**
> Two ethernet interfaces in the same subnet might be causing a problem.
I don't think that's it. I have both Windows and Linux servers with two NICs like this. They all work. And this computer worked until I upgraded to 8.10 today.

---

### Post by MountainX on 2009-02-21
It fixed itself! Sounds crazy. I didn't touch it. I came back after a couple hours and I was going to try a few things, but before I tried anything I did a ping -- and it succeeded. 

I have no idea why or how this issue resolved itself, but it did.

UPDATE: it stopped working again. No changes were made. I think it is time to just reinstall clean. (Hardy never did this.)

---

