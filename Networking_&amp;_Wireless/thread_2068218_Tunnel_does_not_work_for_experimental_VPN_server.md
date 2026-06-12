---
title: "Tunnel does not work for experimental VPN server"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by lonoami on 2012-10-08
I can not create a tunnel on 11.10 that works for:
[http://mirror.yongbok.net/linux/android/repository/development/samples/ToyVpn/server/linux/ToyVpnServer.cpp](http://mirror.yongbok.net/linux/android/repository/development/samples/ToyVpn/server/linux/ToyVpnServer.cpp)
This is what they suggest: 

```

# Enable IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward
# Pick a range of private addresses and perform NAT over eth0. 
iptables -t nat -A POSTROUTING -s 10.0.0.0/8 -o eth0 -j MASQUERADE 
# Create a TUN interface. 
ip tuntap add dev tun0 mode tun
 # Set the addresses and bring up the interface. 
ifconfig tun0 10.0.0.1 dstaddr 10.0.0.2 up

```My network interfaces:
```

ifconfig 
eth0      Link encap:Ethernet  HWaddr f0:de:f1:b9:13:54  
          inet addr:192.168.1.127  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:feb9:1354/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:238878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:371211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86061021 (86.0 MB)  TX bytes:440620273 (440.6 MB)
          Interrupt:20 Memory:f2500000-f2520000 

wlan0     Link encap:Ethernet  HWaddr 10:0b:a9:38:fb:c0  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::120b:a9ff:fe38:fbc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5123029 (5.1 MB)  TX bytes:748977 (748.9 KB)

```I have tried changing
10.0.0.0/8, 10.0.0.1, 10.0.0.2 to some other "reasonable" addresses. 


How can I check if the tunnel is working?

I know little about tunnels --Thank you for any help.

---

