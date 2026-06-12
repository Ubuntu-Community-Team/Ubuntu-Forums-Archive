---
title: "Beginner question: OpenVPN connects but no internet?"
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by tichon on 2013-04-17
Hello all. I am trying to connect to an OpenVPN connection via .conf file. It actually appears to connect but as soon as it does I lose internet connectivity. Below is some information I am able gather:

```
openvpn openvpn-Swe.conf 
Wed Apr 17 11:01:43 2013 OpenVPN 2.1.0 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Enter Auth Username:blahblah
Enter Auth Password:
Wed Apr 17 11:01:51 2013 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Wed Apr 17 11:01:51 2013 LZO compression initialized
Wed Apr 17 11:01:52 2013 RESOLVE: NOTE: jenny.vpntunnel.se resolves to 5 addresses, choosing one by random
Wed Apr 17 11:01:52 2013 UDPv4 link local: [undef]
Wed Apr 17 11:01:52 2013 UDPv4 link remote: [AF_INET]178.73.212.244:7001
Wed Apr 17 11:01:52 2013 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Wed Apr 17 11:01:54 2013 [server] Peer Connection Initiated with [AF_INET]178.73.212.244:7001
Wed Apr 17 11:01:56 2013 TUN/TAP device tun0 opened
Wed Apr 17 11:01:56 2013 /sbin/ifconfig tun0 5.254.140.27 netmask 255.255.255.224 mtu 1500 broadcast 5.254.140.31
Wed Apr 17 11:01:56 2013 Initialization Sequence Completed
```

Once the above initialized it creates a tun0 device:

```
eth2      Link encap:Ethernet  HWaddr 08:00:27:9b:48:a4  
          inet addr:10.50.51.78  Bcast:10.50.51.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe9b:48a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:107194 errors:12 dropped:0 overruns:0 frame:0
          TX packets:25709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43251716 (43.2 MB)  TX bytes:3945830 (3.9 MB)
          Interrupt:19 Base address:0xd020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1407 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:383917 (383.9 KB)  TX bytes:383917 (383.9 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:5.254.140.27  P-t-P:5.254.140.27  Mask:255.255.255.224
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


Not sure if this is useful, but here are my routes:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         5.254.140.1     128.0.0.0       UG    0      0        0 tun0
default         10.50.51.1      0.0.0.0         UG    0      0        0 eth2
default         10.50.51.1      0.0.0.0         UG    100    0        0 eth2
5.254.140.0     *               255.255.255.224 U     0      0        0 tun0
10.50.51.0      *               255.255.255.0   U     1      0        0 eth2
128.0.0.0       5.254.140.1     128.0.0.0       UG    0      0        0 tun0
178.73.212.244  10.50.51.1      255.255.255.255 UGH   0      0        0 eth2
```




I guess I am stuck on the next steps I need to take to utilize the tun0 connection. When I go through network manager GUI I receive the same outcome. Here is the .conf I am using to connect:

```

float
client
dev tun
proto udp
nobind

; CERT
ca keys/ca1.crt
ns-cert-type server
cipher BF-CBC

; HOST
remote-random
remote jenny.vpntunnel.se 7001
remote jenny.vpntunnel.se 7002
remote jenny.vpntunnel.se 7003
remote jenny.vpntunnel.se 7004

resolv-retry infinite

; AUTH
auth-user-pass
persist-key
persist-tun

comp-lzo
verb 1
```

---

### Post by TheFu on 2013-04-17
Is the OpenVPN configured to allow "split tunneling?"  That is a security risk that many providers/corporate VPNs do not allow, so all traffic from the machine would be forced through the tunnel. This means that printing to a local network printer doesn't work.  I think only the server config controls whether split tunnels are allowed. It cannot be controlled on the ovpn client.

Just a thought, but I really don't know.

---

### Post by tichon on 2013-04-17
UPDATE still not fixed:

It appears the VPN was trying to add bad routes?

```
Wed Apr 17 15:46:05 2013 /sbin/route add -net 178.73.212.245 netmask 255.255.255.255 gw 10.50.51.1
Wed Apr 17 15:46:05 2013 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 5.254.141.97
Wed Apr 17 15:46:05 2013 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 5.254.141.97
```

So I went ahead and removed these two routes:

```
route del -net 0.0.0.0 netmask 128.0.0.0 gw 5.254.141.97
route del -net 128.0.0.0 netmask 128.0.0.0 gw 5.254.141.97
```

Now my routes look like the following:

```
default via 10.50.51.1 dev eth2  proto static 
default via 10.50.51.1 dev eth2  metric 100 
5.254.141.96/27 dev tun0  proto kernel  scope link  src 5.254.141.107 
10.50.51.0/24 dev eth2  proto kernel  scope link  src 10.50.51.78  metric 1 
178.73.212.245 via 10.50.51.1 dev eth2 
```

I can now browse the internet while being connected to the VPN, however it doesn't appear that I am actually utilizing the VPN.

---

### Post by ahallubuntu on 2013-04-17
~

---

### Post by tichon on 2013-04-17
So this is a paid for VPN service, the goal being I want a more secure internet connection. When I use the network manager I get the same result unfortunately (I've tried :(). I lose internet connectivity immediately after I connect.

---

