---
title: "openvpn from fedora use on ubuntu 9.04"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by moos3 on 2009-08-29
I have for openvpn that works on fedora but I need to make it work on ubuntu. Can anyone help me ?
openvpnConfig
```

client
remote vpn.blah.com 1195
ca /media/vpn/symp/blah_CA.crt
dev tap0
remote-cert-tls server
up /media/vpn/symp/blah_tapup
down /media/vpn/symp/blah_tapdown
script-security 3 system
route-delay 30
proto udp
resolv-retry infinite
nobind
persist-key
persist-tun
auth-user-pass
comp-lzo
verb 3

```
blah_tapup
```

ifconfig tap0 up
/media/vpn/symp/blah_taproute &

```
blah_taproute
```

sleep 5
/sbin/dhclient3 -1 -q -R subnet-mask,broadcast-address,time-offset,domain-name,domain-name-servers -lf /var/lib/dhcp3/dhclient/dhclient-tap0.leases -pf /var/run/dhclient-tap0.pid tap0 2>/dev/null &

```
blah_tapdown
```

/sbin/dhclient3 -r -lf /var/lib/dhcp3/dhclient/dhclient-tap0.leases -pf /var/run/dhclient-tap0.pid tap0 >/dev/null 2>&1

```

I have modified it to point to the right spots but i'm getting this in the console

```

rgenthner@castine:/media/vpn/symp$ sudo openvpn /media/vpn/symp/symplicity_vpn.ovpn
[sudo] password for rgenthner: 
Sat Aug 29 15:41:42 2009 OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Mar  9 2009
Enter Auth Username:rgenthner
Enter Auth Password:
Sat Aug 29 15:41:47 2009 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Sat Aug 29 15:41:47 2009 WARNING: the current --script-security setting may allow passwords to be passed to scripts via environmental variables
Sat Aug 29 15:41:47 2009 LZO compression initialized
Sat Aug 29 15:41:47 2009 Control Channel MTU parms [ L:1574 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sat Aug 29 15:41:47 2009 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Sat Aug 29 15:41:47 2009 Local Options hash (VER=V4): 'd79ca330'
Sat Aug 29 15:41:47 2009 Expected Remote Options hash (VER=V4): 'f7df56b8'
Sat Aug 29 15:41:47 2009 Socket Buffers: R=[112640->131072] S=[112640->131072]
Sat Aug 29 15:41:47 2009 UDPv4 link local: [undef]
Sat Aug 29 15:41:47 2009 UDPv4 link remote: 216.52.121.66:1195
Sat Aug 29 15:41:47 2009 TLS: Initial packet from 216.52.121.66:1195, sid=72c6905f 9764dc05
Sat Aug 29 15:41:47 2009 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Sat Aug 29 15:41:48 2009 VERIFY OK: depth=1, /C=US/ST=ME/L=Portland/O=Blah_Corp/CN=Blah_Corp_CA/emailAddress=sa@blah.com
Sat Aug 29 15:41:48 2009 Validating certificate key usage
Sat Aug 29 15:41:48 2009 ++ Certificate has key usage  00a0, expects 00a0
Sat Aug 29 15:41:48 2009 VERIFY KU OK
Sat Aug 29 15:41:48 2009 Validating certificate extended key usage
Sat Aug 29 15:41:48 2009 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Sat Aug 29 15:41:48 2009 VERIFY EKU OK
Sat Aug 29 15:41:48 2009 VERIFY OK: depth=0, /C=US/ST=ME/L=portland/O=Blah_Corp/CN=server/emailAddress=sa@blah.com
Sat Aug 29 15:41:48 2009 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sat Aug 29 15:41:48 2009 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sat Aug 29 15:41:48 2009 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sat Aug 29 15:41:48 2009 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sat Aug 29 15:41:48 2009 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Sat Aug 29 15:41:48 2009 [server] Peer Connection Initiated with 216.52.121.66:1195
Sat Aug 29 15:41:49 2009 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Sat Aug 29 15:41:49 2009 PUSH: Received control message: 'PUSH_REPLY,route 66.151.109.0 255.255.255.0 10.120.100.1,route 172.16.1.0 255.255.255.0 10.120.100.1,route 172.16.2.0 255.255.255.0 10.120.100.1,route 10.50.50.0 255.255.255.0 10.120.100.1,dhcp-option DNS 10.120.100.86,ping 10,ping-restart 600'
Sat Aug 29 15:41:49 2009 OPTIONS IMPORT: timers and/or timeouts modified
Sat Aug 29 15:41:49 2009 OPTIONS IMPORT: route options modified
Sat Aug 29 15:41:49 2009 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Sat Aug 29 15:41:49 2009 ROUTE default_gateway=192.168.1.1
Sat Aug 29 15:41:49 2009 TUN/TAP device tap0 opened
Sat Aug 29 15:41:49 2009 TUN/TAP TX queue length set to 100
Sat Aug 29 15:41:49 2009 /media/vpn/symp/blah_tapup tap0 1500 1574   init
Sat Aug 29 15:41:49 2009 script failed: could not execute external program
Sat Aug 29 15:41:49 2009 Exiting


```
what am I doing wrong? I haven't made the tap device. Is this the issue?

---

