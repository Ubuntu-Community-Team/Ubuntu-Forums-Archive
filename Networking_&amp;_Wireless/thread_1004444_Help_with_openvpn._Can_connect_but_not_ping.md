---
title: "Help with openvpn. Can connect but not ping"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by eriksson25 on 2008-12-07
Hi, Need help with my openvpn setup. I can conect but cant ping or usa any protocol like ftp or samba.

I am trying to conect from a windows client to a ubuntu server. No firewalls on both sides. My server local adres is 192.168.0.1 and openvpn is 192.168.10.x

Please can anyone help me or point me at the right direction.

This is my config files
Xp client
```

client
dev tun
proto tcp
remote ***(min servers publica ip) 523
resolv-retry infinite
nobind
persist-key
persist-tun
ca "C:\\Program Files\\OpenVPN\\ubuntu\\ca.crt"
cert "C:\\Program Files\\OpenVPN\\ubuntu\\windowsklient.crt"
key "C:\\Program Files\\OpenVPN\\ubuntu\\windowsklient.key"
ns-cert-type server
tls-auth "C:\\Program Files\\OpenVPN\\ubuntu\\ta.key_1"
cipher BF-CBC
comp-lzo
verb 3

```
Server config
```

port 524
proto tcp
dev tun
ca /etc/openvpn/ca.crt
cert /etc/openvpn/eriksson25.crt
key /etc/openvpn/eriksson25.key
dh /etc/openvpn/dh1024.pem
server 192.168.10.0 255.255.255.0
ifconfig-pool-persist ipp.txt
keepalive 10 120
tls-auth ta.key_0
cipher BF-CBC
comp-lzo
persist-key
persist-tun
status openvpn-status.log
log openvpn.log
verb 3

```

Client log
```

Sun Dec 07 00:59:12 2008 OpenVPN 2.1_rc15 i686-pc-mingw32 [SSL] [LZO2] [PKCS11] built on Nov 19 2008
Sun Dec 07 00:59:12 2008 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sun Dec 07 00:59:12 2008 Control Channel Authentication: using 'C:\Program Files\OpenVPN\ubuntu\ta.key_1' as a OpenVPN static key file
Sun Dec 07 00:59:12 2008 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Dec 07 00:59:12 2008 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Dec 07 00:59:12 2008 LZO compression initialized
Sun Dec 07 00:59:12 2008 Control Channel MTU parms [ L:1544 D:168 EF:68 EB:0 ET:0 EL:0 ]
Sun Dec 07 00:59:12 2008 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Sun Dec 07 00:59:12 2008 Local Options hash (VER=V4): '863ad621'
Sun Dec 07 00:59:12 2008 Expected Remote Options hash (VER=V4): '64e96fc1'
Sun Dec 07 00:59:12 2008 Attempting to establish TCP connection with *****************:523
Sun Dec 07 00:59:12 2008 TCP connection established with ***************:523
Sun Dec 07 00:59:12 2008 Socket Buffers: R=[8192->8192] S=[8192->8192]
Sun Dec 07 00:59:12 2008 TCPv4_CLIENT link local: [undef]
Sun Dec 07 00:59:12 2008 TCPv4_CLIENT link remote: *******************:523
Sun Dec 07 00:59:12 2008 TLS: Initial packet from *****************:523, sid=d1446f51 840db072
Sun Dec 07 00:59:13 2008 VERIFY OK: depth=1, /C=SE/ST=Jonkoping/L=Jonkoping/O=eriksson25/CN=erikisson25/emailAddress=************@hotmail.com
Sun Dec 07 00:59:13 2008 VERIFY OK: nsCertType=SERVER
Sun Dec 07 00:59:13 2008 VERIFY OK: depth=0, /C=SE/ST=Jonkoping/L=Jonkoping/O=eriksson25/CN=eriksson25/emailAddress=**************@hotmail.com
Sun Dec 07 00:59:14 2008 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sun Dec 07 00:59:14 2008 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Dec 07 00:59:14 2008 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sun Dec 07 00:59:14 2008 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Dec 07 00:59:14 2008 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Sun Dec 07 00:59:14 2008 [eriksson25] Peer Connection Initiated with ***************:523
Sun Dec 07 00:59:15 2008 SENT CONTROL [eriksson25]: 'PUSH_REQUEST' (status=1)
Sun Dec 07 00:59:15 2008 PUSH: Received control message: 'PUSH_REPLY,route 192.168.10.1,topology net30,ping 10,ping-restart 120,ifconfig 192.168.10.6 192.168.10.5'
Sun Dec 07 00:59:15 2008 OPTIONS IMPORT: timers and/or timeouts modified
Sun Dec 07 00:59:15 2008 OPTIONS IMPORT: --ifconfig/up options modified
Sun Dec 07 00:59:15 2008 OPTIONS IMPORT: route options modified
Sun Dec 07 00:59:15 2008 ROUTE default_gateway=192.168.2.3
Sun Dec 07 00:59:15 2008 TAP-WIN32 device [Local Area Connection 3] opened: \\.\Global\{E798B781-F521-47E7-A044-9CBC3AF5DBF6}.tap
Sun Dec 07 00:59:15 2008 TAP-Win32 Driver Version 9.4 
Sun Dec 07 00:59:15 2008 TAP-Win32 MTU=1500
Sun Dec 07 00:59:15 2008 Notified TAP-Win32 driver to set a DHCP IP/netmask of 192.168.10.6/255.255.255.252 on interface {E798B781-F521-47E7-A044-9CBC3AF5DBF6} [DHCP-serv: 192.168.10.5, lease-time: 31536000]
Sun Dec 07 00:59:15 2008 Successful ARP Flush on interface [3] {E798B781-F521-47E7-A044-9CBC3AF5DBF6}
Sun Dec 07 00:59:20 2008 TEST ROUTES: 1/1 succeeded len=1 ret=1 a=0 u/d=up
Sun Dec 07 00:59:20 2008 C:\WINDOWS\system32\route.exe ADD 192.168.10.1 MASK 255.255.255.255 192.168.10.5
Sun Dec 07 00:59:20 2008 Route addition via IPAPI succeeded [adaptive]
Sun Dec 07 00:59:20 2008 Initialization Sequence Completed

```

---

### Post by jmoorse on 2008-12-07
Have you tried connections via direct IP and not DNS names?

Can you post:
1. ifconfig -a
2. arp -a
3. tracepath (other ends IP)

---

### Post by eriksson25 on 2008-12-10
> **jmoorse said:**
> Have you tried connections via direct IP and not DNS names?

Can you post:
1. ifconfig -a
2. arp -a
3. tracepath (other ends IP)

Oki, Here it comes

Ifconfig -a
```

eth2      Link encap:Ethernet  HWaddr 00:18:f3:9e:2a:4f
          inet addr:193.11.106.***  Bcast:193.11.107.255  Mask:255.255.254.0
          inet6 addr: 2002:c10b:6e02:8:218:f3ff:fe9e:2a4f/64 Scope:Global
          inet6 addr: fec0::8:218:f3ff:fe9e:2a4f/64 Scope:Site
          inet6 addr: 2002:c10b:6b20:8:218:f3ff:fe9e:2a4f/64 Scope:Global
          inet6 addr: fe80::218:f3ff:fe9e:2a4f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1087309589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1730584598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:530109073 (530.1 MB)  TX bytes:411666579 (411.6 MB)
          Interrupt:19

eth3      Link encap:Ethernet  HWaddr 00:18:f3:9e:55:47
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe9e:5547/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14654288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9131353 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3283383717 (3.2 GB)  TX bytes:2507811529 (2.5 GB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4126907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4126907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1971157217 (1.9 GB)  TX bytes:1971157217 (1.9 GB)

pan0      Link encap:Ethernet  HWaddr 3a:ee:e9:a8:17:bd
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:660 (660.0 B)  TX bytes:0 (0.0 B)

```

arp-a
```
host107-72.junet.se (193.11.107.72) at 00:1b:63:b1:c5:5c [ether] on eth2
jsix-gw3.junet.se (193.11.106.1) at 00:13:c3:0b:df:42 [ether] on eth2
host106-92.junet.se (193.11.106.92) at 00:19:e3:3d:86:f4 [ether] on eth2
host107-198.junet.se (193.11.107.198) at 00:19:e3:3e:7a:de [ether] on eth2
host106-221.junet.se (193.11.106.221) at 00:1b:63:ae:44:9b [ether] on eth2
host107-188.junet.se (193.11.107.188) at 00:1e:c2:16:8c:57 [ether] on eth2
host106-83.junet.se (193.11.106.83) at 00:1e:c2:0d:1a:59 [ether] on eth2
host107-5.junet.se (193.11.107.5) at 00:1e:c2:0c:35:97 [ether] on eth2
host107-179.junet.se (193.11.107.179) at 00:1f:5b:f6:f9:90 [ether] on eth2
host107-104.junet.se (193.11.107.104) at 00:1f:5b:f6:68:c2 [ether] on eth2
? (192.168.0.2) at 00:22:15:80:99:49 [ether] on eth3
host106-98.junet.se (193.11.106.98) at 00:23:32:b3:67:b4 [ether] on eth2
host107-194.junet.se (193.11.107.194) at 00:1f:f3:5a:ad:5b [ether] on eth2

```

tracepath on vpn ip
```

1:  send failed
     Resume: pmtu 65535

```

tracepath client real ip
```
1:  host106-168.junet.se (193.11.106.***)                  0.133ms pmtu 1500
 1:  jsix-gw4.junet.se (193.11.108.1)                       2.281ms
 1:  jsix-gw4.junet.se (193.11.108.1)                       2.329ms
 2:  c2sth-ge-4-3-8.sunet.se (193.11.20.149)                6.380ms asymm  3
 3:  fre-peer1-geth11-2.se.telia.net (195.67.220.149)       6.390ms
 4:  hy-c5-link.se.telia.net (81.228.75.146)               10.833ms
 5:  vs-b-c5-link.se.telia.net (81.228.72.46)               9.706ms
 6:  vs-b-td2-link.se.telia.net (81.228.73.67)             25.393ms
 7:  nt-a11-link.se.telia.net (81.228.74.51)               10.642ms
 8:  no reply
*
*
and so on

```

Hope it was what you needed.

---

### Post by jmoorse on 2008-12-11
Please run:

lspci | grep Ethernet

---

