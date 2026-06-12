---
title: "OpenVPN Bridging Setup"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by hugetivofan on 2010-11-09
Hi, trying to get openvpn working with bridging on  ubuntu (which I am new to).  My setup is actually mac to mac using ubuntu in virtual machines (vmware).  The virtual machines are setup to get a direct bridged connection to the router at each lan, so I think that should not be an issue.

After setup, I have an active vpn connection between  server and client, client successfully gets ip assigned from server (192.168.3.170).   but can't ping server or anything on server-side lan from the client  side.

i followed all basic openvpn directions.  was able to get  this to work with windows server and client (also via virtual machines) but now cant get it to work  on ubuntu.  my goal is to have client-side lan devices talk to  server-side lan devices, including broadcast traffic (so devices think  it is all a single lan).

[http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html](http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html)

The one thing extra I did apart from the  basic config stuff is I tried to bridge eth0 and tap0 on the client  side.  it doesnt really discuss this anywhere but it seemed logical to  achieve my objective above.  regardless, the connection was active but i  couldnt ping even before i set up this client-side bridge.

My  config files and client log file below (cant currently access server log file) - any thoughts on what i am doing  wrong?  Please let me know if I can provide any other useful info.   Thanks!

client1.ovpn:
dev tap0
proto udp
remote [server ip] 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client1.crt
key client1.key
verb 3

server.ovpn:
port 1194
proto udp
dev tap0
ca ca.crt
cert server.crt
key server.key 
dh dh1024.pem
server-bridge 192.168.3.118 255.255.255.0 192.168.3.170 192.168.3.254
ifconfig-pool-persist ipp.txt
keepalive 10 120
persist-key
persist-tun
status openvpn-status.log
verb 3

client log file:
Sun Nov  7 22:48:33 2010 OpenVPN 2.2-beta3 i686-pc-linux-gnu [SSL] [LZO2] [EPOLL] [eurephia] built on Nov  7 2010
Sun Nov  7 22:48:33 2010 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Sun Nov  7 22:48:33 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sun Nov  7 22:48:33 2010 WARNING: file 'client1.key' is group or others accessible
Sun Nov  7 22:48:33 2010 Control Channel MTU parms [ L:1573 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sun Nov  7 22:48:33 2010 Socket Buffers: R=[114688->131072] S=[114688->131072]
Sun Nov  7 22:48:33 2010 Data Channel MTU parms [ L:1573 D:1450 EF:41 EB:4 ET:32 EL:0 ]
Sun Nov  7 22:48:33 2010 Local Options hash (VER=V4): '2c50bd2c'
Sun Nov  7 22:48:33 2010 Expected Remote Options hash (VER=V4): '0ddbb6e3'
Sun Nov  7 22:48:33 2010 UDPv4 link local: [undef]
Sun Nov  7 22:48:33 2010 UDPv4 link remote: [server ip]:1194
Sun Nov  7 22:48:33 2010 TLS: Initial packet from [server ip]:1194, sid=9abbd86b a43f3b2c
Sun Nov  7 22:48:33 2010 VERIFY OK: depth=1, /C=US/ST=NY/L=XXXXX/O=XXXXX/CN=XXXXX/emailAddress=XXXXX
Sun Nov  7 22:48:33 2010 VERIFY OK: depth=0, /C=US/ST=NY/O=XXXXX/CN=server/emailAddress=XXXXX
Sun Nov  7 22:48:33 2010 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sun Nov  7 22:48:33 2010 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Nov  7 22:48:33 2010 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sun Nov  7 22:48:33 2010 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Nov  7 22:48:33 2010 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Sun Nov  7 22:48:33 2010 [server] Peer Connection Initiated with [server ip]:1194
Sun Nov  7 22:48:35 2010 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Sun  Nov  7 22:48:35 2010 PUSH: Received control message:  'PUSH_REPLY,route-gateway 192.168.3.118,ping 10,ping-restart  120,ifconfig 192.168.3.170 255.255.255.0'
Sun Nov  7 22:48:35 2010 OPTIONS IMPORT: timers and/or timeouts modified
Sun Nov  7 22:48:35 2010 OPTIONS IMPORT: --ifconfig/up options modified
Sun Nov  7 22:48:35 2010 OPTIONS IMPORT: route-related options modified
Sun  Nov  7 22:48:35 2010 WARNING: potential TUN/TAP adapter subnet conflict  between local LAN [192.168.3.0/255.255.255.0] and remote VPN  [192.168.3.0/255.255.255.0]
Sun Nov  7 22:48:35 2010 TUN/TAP device tap0 opened
Sun Nov  7 22:48:35 2010 TUN/TAP TX queue length set to 100
Sun Nov  7 22:48:35 2010 /sbin/ifconfig tap0 192.168.3.170 netmask 255.255.255.0 mtu 1500 broadcast 192.168.3.255
Sun Nov  7 22:48:35 2010 Initialization Sequence Completed

---

