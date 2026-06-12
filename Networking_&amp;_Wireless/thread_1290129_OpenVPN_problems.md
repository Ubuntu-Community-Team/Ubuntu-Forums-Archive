---
title: "OpenVPN problems"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by de12261 on 2009-10-13
Hello to everyone.

I have to setup openvpn on ubuntu server (8.04.3) and some windows clients.
I want to see the Lan of the server from my client.

I read many openvpn howto, but I have problems to connect to server/problems
to see other Lan computers.

These are my conf files.

----client.ovpn:
remote X.X.X.X
dev tap
proto tcp-client
rport 1194
ifconfig 10.0.0.2 255.255.255.0
route 192.168.200.0 255.255.255.0 10.0.0.1 
cipher AES-128-CBC
secret ta.key
verb 3
no-replay
persist-tun
comp-lzo

----server.conf:
dev tap
proto tcp-server
lport 1194
ifconfig 10.0.0.1 255.255.255.0
route 10.0.0.0 255.255.255.0 192.168.200.254
cipher AES-128-CBC
secret /etc/openvpn/ta.key
verb 9
no-replay
persist-tun
comp-lzo
log openvpn
status /var/log/openvpn-status.log


The server is with 2 ethernet card, eth0 connected to internet
and eth1 (192.168.200.253) connected to internal lan (192.168.200.0).

The client get 10.0.0.2 ip address, the server have to get 10.0.0.1 ip address
but i can't ping it.

This is the status from client:
Tue Oct 13 18:46:58 2009 OpenVPN 2.0.9 Win32-MinGW [SSL] [LZO] built on Oct  1 2006
Tue Oct 13 18:46:58 2009 WARNING: You have disabled Replay Protection (--no-replay) which may make OpenVPN less secure
Tue Oct 13 18:46:58 2009 Static Encrypt: Cipher 'AES-128-CBC' initialized with 128 bit key
Tue Oct 13 18:46:58 2009 Static Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue Oct 13 18:46:58 2009 Static Decrypt: Cipher 'AES-128-CBC' initialized with 128 bit key
Tue Oct 13 18:46:58 2009 Static Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue Oct 13 18:46:58 2009 LZO compression initialized
Tue Oct 13 18:46:58 2009 TAP-WIN32 device [Connessione alla rete locale (LAN) 3] opened: \\.\Global\{45960E66-2E8E-4B27-8A6A-D14E4A3F6453}.tap
Tue Oct 13 18:46:58 2009 TAP-Win32 Driver Version 8.4 
Tue Oct 13 18:46:58 2009 TAP-Win32 MTU=1500
Tue Oct 13 18:46:58 2009 Notified TAP-Win32 driver to set a DHCP IP/netmask of 10.0.0.2/255.255.255.0 on interface {45960E66-2E8E-4B27-8A6A-D14E4A3F6453} [DHCP-serv: 10.0.0.0, lease-time: 31536000]
Tue Oct 13 18:46:58 2009 Successful ARP Flush on interface [4] {45960E66-2E8E-4B27-8A6A-D14E4A3F6453}
Tue Oct 13 18:46:58 2009 Data Channel MTU parms [ L:1587 D:1450 EF:55 EB:135 ET:32 EL:0 AF:3/1 ]
Tue Oct 13 18:46:58 2009 Local Options hash (VER=V4): '31222a6a'
Tue Oct 13 18:46:58 2009 Expected Remote Options hash (VER=V4): '23601ecb'
Tue Oct 13 18:46:58 2009 Attempting to establish TCP connection with X.X.X.X:1194
Tue Oct 13 18:46:58 2009 TCP connection established with X.X.X.X:1194
Tue Oct 13 18:46:58 2009 TCPv4_CLIENT link local: [undef]
Tue Oct 13 18:46:58 2009 TCPv4_CLIENT link remote: X.X.X.X:1194
Tue Oct 13 18:46:58 2009 Peer Connection Initiated with X.X.X.X:1194
Tue Oct 13 18:46:58 2009 TEST ROUTES: 0/0 succeeded len=1 ret=0 a=0 u/d=down
Tue Oct 13 18:46:58 2009 Route: Waiting for TUN/TAP interface to come up...
Tue Oct 13 18:47:00 2009 TEST ROUTES: 0/0 succeeded len=1 ret=0 a=0 u/d=down
Tue Oct 13 18:47:00 2009 Route: Waiting for TUN/TAP interface to come up...
Tue Oct 13 18:47:01 2009 TEST ROUTES: 0/0 succeeded len=1 ret=0 a=0 u/d=down
Tue Oct 13 18:47:01 2009 Route: Waiting for TUN/TAP interface to come up...
Tue Oct 13 18:47:02 2009 TEST ROUTES: 0/0 succeeded len=1 ret=0 a=0 u/d=down
Tue Oct 13 18:47:02 2009 Route: Waiting for TUN/TAP interface to come up...
Tue Oct 13 18:47:04 2009 TEST ROUTES: 1/1 succeeded len=1 ret=1 a=0 u/d=up
Tue Oct 13 18:47:04 2009 route ADD 192.168.200.0 MASK 255.255.255.0 10.0.0.1
Tue Oct 13 18:47:04 2009 Route addition via IPAPI succeeded
Tue Oct 13 18:47:04 2009 Initialization Sequence Completed


I only want to connect my client to the LAN of the server and see
shares, computers etc....

Where I made mistakes???

Thank you very much

---

