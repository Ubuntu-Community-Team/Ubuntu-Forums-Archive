---
title: "server 12.04 remote access OpenVPN configuration"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by blakdeth77 on 2012-06-26
Would like to configure remote access to a business network. I keep getting "target machine actively refused connection" error 10061 . The client machine is Win7 with OpenVPN client in use. Have created keys for server and all users individually but client software doesn't give any place in the GUI to install or specify them?

Here is server config info. It's not what the final network / subnets will be, this is my test environment info. 

```

#server.conf
port 1194
proto udp
dev tun
ca ca.crt
cert ubuntu.crt
key ubuntu.key
dh dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
keepalive 10 120
comp-lzo
max-clients 10
persist-key
persist-tun
status openvpn-status.log
log  openvpn.log
verb 4

#if I use command "service openvpn status" ..
#"VPN server is running" is returned

#ipconfig shows...

eth0
Link encap:Ethernet  HWaddr c8:60:00:97:04:e5
inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
inet6 addr: fe80::ca60:ff:fe97:4e5/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:26284 errors:0 dropped:1494 overruns:0 frame:0
TX packets:10032 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:22269074 (22.2 MB)  TX bytes:951053 (951.0 KB)
Interrupt:41 Base address:0xe000

lo        Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:232 errors:0 dropped:0 overruns:0 frame:0
TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:13920 (13.9 KB)  TX bytes:13920 (13.9 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

#Showing the routes at the server...

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
10.8.0.0        10.8.0.2        255.255.255.0   UG        0 0          0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0

```

---

