---
title: "OpenVpn - centos server and linux client - teething problems"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by thegeezer3 on 2009-09-13
Hi ive tried setting up a server client openvpn configuration and whilst i can ping my centos remote server from my linux ubuntu desktop i have a few errors showing up that i want to iron out. 

First - When i start the openvpn service on my centos server this error message pops up

[root@www openvpn]# service openvpn start
Starting openvpn: FATAL: Could not load /lib/modules/2.6.18-128.2.1.el5.028stab064.4/modules.dep: No such file or directory
                                                           [  OK  ]

But i can still ping the server...what is this? Ive asked my host to enable tun.

Second in my clients logs i see this error

Sun Sep 13 14:14:14 2009 ERROR: Linux route add command failed: external program exited with error status: 7

What do these errors mean and should i 
be concerned.

Here is my server config file
```

port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
server 10.1.1.0  255.255.255.128
ifconfig-pool-persist ipp.txt
keepalive 10 120
comp-lzo
persist-key
persist-tun
status /etc/openvpn/openvpn-status.log
log  /etc/openvpn/openvpn.log
verb 6
```and client

```

client
dev tun
proto udp
remote "not putting my real ip here" 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client1.crt
key client1.key
ns-cert-type server
cipher BF-CBC
comp-lzo
status /etc/openvpn/openvpn-status.log
log /etc/openvpn/openvpn.log
verb 3

```client log (i took out my ip address - am i just being paranoid - im new to all this)
```
Sun Sep 13 14:26:22 2009 OpenVPN 2.1_rc11 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Mar  9 2009
Sun Sep 13 14:26:22 2009 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Sun Sep 13 14:26:22 2009 LZO compression initialized
Sun Sep 13 14:26:22 2009 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sun Sep 13 14:26:22 2009 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Sun Sep 13 14:26:22 2009 Local Options hash (VER=V4): '41690919'
Sun Sep 13 14:26:22 2009 Expected Remote Options hash (VER=V4): '530fdded'
Sun Sep 13 14:26:22 2009 Socket Buffers: R=[124928->131072] S=[124928->131072]
Sun Sep 13 14:26:22 2009 UDPv4 link local: [undef]
Sun Sep 13 14:26:22 2009 UDPv4 link remote: "not putting my real ip address here":1194
Sun Sep 13 14:26:22 2009 TLS: Initial packet from "not putting my real ip addres ehre":1194, sid=94f7606b 49b4c2a3
Sun Sep 13 14:26:24 2009 VERIFY OK: depth=1, /C=UK/ST=GM/L=Manchester/O=YoFelix/CN=YoFelix_CA/emailAddress=adam@ca.com
Sun Sep 13 14:26:24 2009 VERIFY OK: nsCertType=SERVER
Sun Sep 13 14:26:24 2009 VERIFY OK: depth=0, /C=UK/ST=GM/L=Manchester/O=YoFelix/CN=server/emailAddress=adam@ca.com
Sun Sep 13 14:26:26 2009 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sun Sep 13 14:26:26 2009 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Sep 13 14:26:26 2009 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sun Sep 13 14:26:26 2009 Sun Sep 13 14:26:26 2009 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Sep 13 14:26:26 2009 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Sun Sep 13 14:26:26 2009 [server] Peer Connection Initiated with "not putting my real ip address here":1194
Sun Sep 13 14:26:27 2009 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Sun Sep 13 14:26:28 2009 PUSH: Received control message: 'PUSH_REPLY,route 10.1.1.1,ping 10,ping-restart 120,ifconfig 10.1.1.6 10.1.1.5'
Sun Sep 13 14:26:28 2009 OPTIONS IMPORT: timers and/or timeouts modified
Sun Sep 13 14:26:28 2009 OPTIONS IMPORT: --ifconfig/up options modified
Sun Sep 13 14:26:28 2009 OPTIONS IMPORT: route options modified
Sun Sep 13 14:26:28 2009 ROUTE default_gateway=192.168.11.1
Sun Sep 13 14:26:28 2009 TUN/TAP device tun1 opened
Sun Sep 13 14:26:28 2009 TUN/TAP TX queue length set to 100
Sun Sep 13 14:26:28 2009 /sbin/ifconfig tun1 10.1.1.6 pointopoint 10.1.1.5 mtu 1500
Sun Sep 13 14:26:28 2009 /sbin/route add -net 10.1.1.1 netmask 255.255.255.255 gw 10.1.1.5
SIOCADDRT: File exists
Sun Sep 13 14:26:28 2009 ERROR: Linux route add command failed: external program exited with error status: 7
Sun Sep 13 14:26:28 2009 Initialization Sequence Completed
Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Sep 13 14:26:26 2009 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA


```Can anyone help?

---

