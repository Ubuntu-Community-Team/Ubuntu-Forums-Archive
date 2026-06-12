---
title: "Connect to VPN using OpenVPN, no remote IP assigned"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by EndingPop on 2009-11-25
After some work, I am able to connect to my work's VPN using OpenVPN. However, I do not get a remote IP, and I cannot ping any of the computers on the remote network. 

Here is my ovpn file:
```
tls-client
dev tap
proto udp
remote xxx.xxx.xxx.xxx 443
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client2.crt
key client2.key
ns-cert-type server
comp-lzo
verb 4
float
```

Here is the output I get:
```
$ sudo openvpn --config configfile.ovpn
Wed Nov 25 12:25:41 2009 OpenVPN 2.1_rc19 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Wed Nov 25 12:25:41 2009 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Wed Nov 25 12:25:41 2009 WARNING: file 'client2.key' is group or others accessible
Wed Nov 25 12:25:41 2009 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Wed Nov 25 12:25:41 2009 LZO compression initialized
Wed Nov 25 12:25:41 2009 Control Channel MTU parms [ L:1574 D:138 EF:38 EB:0 ET:0 EL:0 ]
Wed Nov 25 12:25:41 2009 TUN/TAP device tap0 opened
Wed Nov 25 12:25:41 2009 TUN/TAP TX queue length set to 100
Wed Nov 25 12:25:41 2009 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Wed Nov 25 12:25:41 2009 Local Options hash (VER=V4): 'd79ca330'
Wed Nov 25 12:25:41 2009 Expected Remote Options hash (VER=V4): 'f7df56b8'
Wed Nov 25 12:25:41 2009 Socket Buffers: R=[129024->131072] S=[129024->131072]
Wed Nov 25 12:25:41 2009 UDPv4 link local: [undef]
Wed Nov 25 12:25:41 2009 UDPv4 link remote: 75.14.51.229:443
Wed Nov 25 12:25:42 2009 TLS: Initial packet from 75.14.51.229:443, sid=33b55456 cbb13f13
Wed Nov 25 12:25:44 2009 VERIFY OK: depth=1, /C=US/ST=XX/L=XXXXXX/O=XXXXX/CN=vpn.xxxxxx.xxx/emailAddress=xxxx@xxxxxx.xxx
Wed Nov 25 12:25:44 2009 VERIFY OK: nsCertType=SERVER
Wed Nov 25 12:25:44 2009 VERIFY OK: depth=0, /C=US/ST=XXXX/O=XXXXXX/CN=vpn.XXXXXX.XXX/emailAddress=xxx@xxxxxx.xxx
Wed Nov 25 12:25:45 2009 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Nov 25 12:25:45 2009 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Nov 25 12:25:45 2009 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Nov 25 12:25:45 2009 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Nov 25 12:25:45 2009 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Wed Nov 25 12:25:45 2009 [vpn.xxxx.xxx] Peer Connection Initiated with 75.14.51.229:443
Wed Nov 25 12:25:47 2009 Initialization Sequence Completed

```

Here's the output of ifconfig tap0:
```
tap0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:180 (180.0 B)  TX bytes:0 (0.0 B)

```

Anyone know what I have to do to get an IP address on the remote LAN? It has a DHCP server, and I can connect to it using this ovpn file with the OpenVPN GUI on Windows.

---

### Post by EndingPop on 2009-12-11
Bumpity?

---

### Post by EndingPop on 2009-12-14
I've tried this using both the OpenVPN manager and Kvpn. I get slightly different results in each case, but I can't get it to get an IP on the remote network.

This works with no issues on Windows and the OpenVPN GUI program.

---

