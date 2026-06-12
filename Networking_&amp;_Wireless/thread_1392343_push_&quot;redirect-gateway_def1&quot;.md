---
title: "push &quot;redirect-gateway def1&quot;"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by linux000019 on 2010-01-28
heres my server config

everytime i connect i cannot browse internet....

edit: better logs posted

> **linux000019 said:**
> thank you for the reply. heres the config files and log outputs.
I looked for anything to do with openvpn in syslog and messages in /var/log/ and couldn't find anything. I'll put the server log and config following.

CLIENT CONFIG/LOG

client
dev tun
proto tcp
float
remote ******** 443
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
ns-cert-type server
comp-lzo
verb 3

```
ryan@ryan-laptop:/etc/openvpn$ sudo openvpn client.conf
[sudo] password for ryan: 
Fri Jan 29 10:13:29 2010 OpenVPN 2.1_rc19 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Fri Jan 29 10:13:29 2010 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Fri Jan 29 10:13:29 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Fri Jan 29 10:13:29 2010 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Fri Jan 29 10:13:29 2010 LZO compression initialized
Fri Jan 29 10:13:29 2010 Control Channel MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Fri Jan 29 10:13:29 2010 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Fri Jan 29 10:13:29 2010 Local Options hash (VER=V4): '69109d17'
Fri Jan 29 10:13:29 2010 Expected Remote Options hash (VER=V4): 'c0103fa8'
Fri Jan 29 10:13:29 2010 Attempting to establish TCP connection with*********:443 [nonblock]
Fri Jan 29 10:13:30 2010 TCP connection established with *********:443
Fri Jan 29 10:13:30 2010 Socket Buffers: R=[87380->131072] S=[16384->131072]
Fri Jan 29 10:13:30 2010 TCPv4_CLIENT link local: [undef]
Fri Jan 29 10:13:30 2010 TCPv4_CLIENT link remote: *********:443
Fri Jan 29 10:13:30 2010 TLS: Initial packet from*********:443, sid=0481ec69 ccd47f2e
Fri Jan 29 10:13:31 2010 VERIFY OK: ***
Fri Jan 29 10:13:31 2010 VERIFY OK: ***
Fri Jan 29 10:13:33 2010 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Jan 29 10:13:33 2010 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Jan 29 10:13:33 2010 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Jan 29 10:13:33 2010 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Jan 29 10:13:33 2010 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Fri Jan 29 10:13:33 2010 [server] Peer Connection Initiated with *********:443
Fri Jan 29 10:13:34 2010 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Fri Jan 29 10:13:34 2010 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway local def1,dhcp-option DNS 208.67.222.222,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.8.0.6 10.8.0.5'
Fri Jan 29 10:13:34 2010 OPTIONS IMPORT: timers and/or timeouts modified
Fri Jan 29 10:13:34 2010 OPTIONS IMPORT: --ifconfig/up options modified
Fri Jan 29 10:13:34 2010 OPTIONS IMPORT: route options modified
Fri Jan 29 10:13:34 2010 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Fri Jan 29 10:13:34 2010 ROUTE default_gateway=192.168.21.254
Fri Jan 29 10:13:34 2010 TUN/TAP device tun0 opened
Fri Jan 29 10:13:34 2010 TUN/TAP TX queue length set to 100
Fri Jan 29 10:13:34 2010 /sbin/ifconfig tun0 10.8.0.6 pointopoint 10.8.0.5 mtu 1500
Fri Jan 29 10:13:34 2010 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 10.8.0.5
Fri Jan 29 10:13:34 2010 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.8.0.5
Fri Jan 29 10:13:34 2010 /sbin/route add -net 10.8.0.1 netmask 255.255.255.255 gw 10.8.0.5
Fri Jan 29 10:13:34 2010 Initialization Sequence Completed
^CFri Jan 29 10:14:01 2010 event_wait : Interrupted system call (code=4)
Fri Jan 29 10:14:01 2010 TCP/UDP: Closing socket
Fri Jan 29 10:14:01 2010 /sbin/route del -net 10.8.0.1 netmask 255.255.255.255
Fri Jan 29 10:14:01 2010 /sbin/route del -net 0.0.0.0 netmask 128.0.0.0
Fri Jan 29 10:14:01 2010 /sbin/route del -net 128.0.0.0 netmask 128.0.0.0
Fri Jan 29 10:14:01 2010 Closing TUN/TAP interface
Fri Jan 29 10:14:01 2010 /sbin/ifconfig tun0 0.0.0.0
Fri Jan 29 10:14:02 2010 SIGINT[hard,] received, process exiting
```_________________________________________________________________________

SERVER CONFIG/LOG

OPENVPN_CONFIG=
port 443
proto tcp
dev tun
ca /tmp/openvpn/ca.crt
cert /tmp/openvpn/cert.pem
key /tmp/openvpn/key.pem
dh /tmp/openvpn/dh.pem
server 10.8.0.0 255.255.255.0
push "redirect-gateway local def1"
push "dhcp-option DNS 208.67.222.222"
keepalive 10 120
comp-lzo
persist-key
persist-tun
verb 3

RC_FIREWALL=
iptables -I INPUT -p udp --dport 11907 -j logaccept
iptables -I INPUT -p tcp --dport 11907 -j logaccept
iptables -I INPUT -p udp --dport 443 -j logaccept
iptables -I INPUT -p tcp --dport 443 -j logaccept
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE

```
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: OpenVPN 2.1_rc20 mipsel-unknown-linux-gnu [SSL] [LZO1] [EPOLL] built on Oct 10 2009
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: Diffie-Hellman initialized with 1024 bit key
Jan 29 10:06:00 DD-WRT daemon.warn openvpn[774]: WARNING: file '/tmp/openvpn/key.pem' is group or others accessible
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: TLS-Auth MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: TUN/TAP device tun0 opened
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: TUN/TAP TX queue length set to 100
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: /sbin/ifconfig tun0 10.8.0.1 pointopoint 10.8.0.2 mtu 1500
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: /sbin/route add -net 10.8.0.0 netmask 255.255.255.0 gw 10.8.0.2
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: Listening for incoming TCP connection on [undef]:443
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: Socket Buffers: R=[43689->65534] S=[16384->65534]
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: TCPv4_SERVER link local (bound): [undef]:443
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: TCPv4_SERVER link remote: [undef]
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: MULTI: multi_init called, r=256 v=256
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: IFCONFIG POOL: base=10.8.0.4 size=62
Jan 29 10:06:01 DD-WRT daemon.warn openvpn[798]: Note: sys_epoll API is unavailable, falling back to poll/select API
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: MULTI: TCP INIT maxclients=1024 maxevents=1028
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: Initialization Sequence Completed
Jan 29 10:06:20 DD-WRT authpriv.notice dropbear[815]: pubkey auth succeeded for 'root' with key md5 20:49:a1:18:08:d2:25:61:be:64:41:3d:12:19:a1:78 from 170.213.131.190:34112
Jan 29 10:13:14 DD-WRT authpriv.info dropbear[815]: exit after auth (root): Exited normally
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: MULTI: multi_create_instance called
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: Re-using SSL/TLS context
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: LZO compression initialized
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: Control Channel MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: TCP connection established with 170.213.131.190:8397
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: Socket Buffers: R=[65534->65534] S=[65534->65534]
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: TCPv4_SERVER link local: [undef]
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: TCPv4_SERVER link remote: 170.213.131.190:8397
Jan 29 10:13:31 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 TLS: Initial packet from 170.213.131.190:8397, sid=d9274e0a 997a8057
Jan 29 10:13:32 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 VERIFY OK: ***
Jan 29 10:13:32 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 VERIFY OK: ***
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 [client] Peer Connection Initiated with 170.213.131.190:8397
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: client/170.213.131.190:8397 MULTI: Learn: 10.8.0.6 -> client/170.213.131.190:8397
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: client/170.213.131.190:8397 MULTI: primary virtual IP for client/170.213.131.190:8397: 10.8.0.6
Jan 29 10:13:34 DD-WRT daemon.notice openvpn[798]: client/170.213.131.190:8397 PUSH: Received control message: 'PUSH_REQUEST'
Jan 29 10:13:34 DD-WRT daemon.notice openvpn[798]: client/170.213.131.190:8397 SENT CONTROL [client]: 'PUSH_REPLY,redirect-gateway local def1,dhcp-option DNS 208.67.222.222,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.8.0.6 10.8.0.5' (status=1)
Jan 29 10:14:04 DD-WRT daemon.err openvpn[798]: client/170.213.131.190:8397 Connection reset, restarting [0]
Jan 29 10:14:04 DD-WRT daemon.notice openvpn[798]: client/170.213.131.190:8397 SIGUSR1[soft,connection-reset] received, client-instance restarting
Jan 29 10:14:04 DD-WRT daemon.notice openvpn[798]: TCP/UDP: Closing socket
Jan 29 10:25:53 DD-WRT authpriv.notice dropbear[1280]: pubkey auth succeeded for 'root' with key md5 20:49:a1:18:08:d2:25:61:be:64:41:3d:12:19:a1:78 from 170.213.131.190:17836

```

---

### Post by linux000019 on 2010-01-28
edit: better logs posted below

---

### Post by linux000019 on 2010-01-28
Bump

---

### Post by linux000019 on 2010-01-28
bump, setup client side to up and down resolve; will try later

---

### Post by Muppet on 2010-01-29
> **linux000019 said:**
> heres my server config

everytime i connect i cannot browse internet....


port 1194
proto udp
dev tun
ca /tmp/openvpn/ca.crt
cert /tmp/openvpn/cert.pem
key /tmp/openvpn/key.pem
dh /tmp/openvpn/dh.pem
server 10.8.0.0 255.255.255.0
push "redirect-gateway local def1"
keepalive 10 120
comp-lzo
persist-key
persist-tun
verb 3

iptables -I INPUT -p udp --dport 11907 -j logaccept
iptables -I INPUT -p tcp --dport 11907 -j logaccept
iptables -I INPUT -p udp --dport 1194 -j logaccept
iptables -I INPUT -p tcp --dport 1194 -j logaccept
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
push "dhcp-option DNS 10.8.0.1"
I assume your iptable entries are actually entered via terminal and not entered like that in your OpenVPN config?

Instead of pushing DNS 10.8.0.1 - try pushing OpenDNS servers 208.67.222.222 and 208.67.220.220.

If your client can't then perform nslookups on any domains, the problem lies elsewhere in the configuration (i would guess a dodgy/missed iptables entry).

---

### Post by linux000019 on 2010-01-29
thank you for the reply. heres the config files and log outputs.
I looked for anything to do with openvpn in syslog and messages in /var/log/ and couldn't find anything. I'll put the server log and config following.

CLIENT CONFIG/LOG

client
dev tun
proto tcp
float
remote ******** 443
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
ns-cert-type server
comp-lzo
verb 3

```
ryan@ryan-laptop:/etc/openvpn$ sudo openvpn client.conf
[sudo] password for ryan: 
Fri Jan 29 10:13:29 2010 OpenVPN 2.1_rc19 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Fri Jan 29 10:13:29 2010 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Fri Jan 29 10:13:29 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Fri Jan 29 10:13:29 2010 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Fri Jan 29 10:13:29 2010 LZO compression initialized
Fri Jan 29 10:13:29 2010 Control Channel MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Fri Jan 29 10:13:29 2010 Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Fri Jan 29 10:13:29 2010 Local Options hash (VER=V4): '69109d17'
Fri Jan 29 10:13:29 2010 Expected Remote Options hash (VER=V4): 'c0103fa8'
Fri Jan 29 10:13:29 2010 Attempting to establish TCP connection with*********:443 [nonblock]
Fri Jan 29 10:13:30 2010 TCP connection established with *********:443
Fri Jan 29 10:13:30 2010 Socket Buffers: R=[87380->131072] S=[16384->131072]
Fri Jan 29 10:13:30 2010 TCPv4_CLIENT link local: [undef]
Fri Jan 29 10:13:30 2010 TCPv4_CLIENT link remote: *********:443
Fri Jan 29 10:13:30 2010 TLS: Initial packet from*********:443, sid=0481ec69 ccd47f2e
Fri Jan 29 10:13:31 2010 VERIFY OK: ***
Fri Jan 29 10:13:31 2010 VERIFY OK: ***
Fri Jan 29 10:13:33 2010 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Jan 29 10:13:33 2010 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Jan 29 10:13:33 2010 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Fri Jan 29 10:13:33 2010 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Jan 29 10:13:33 2010 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Fri Jan 29 10:13:33 2010 [server] Peer Connection Initiated with *********:443
Fri Jan 29 10:13:34 2010 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Fri Jan 29 10:13:34 2010 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway local def1,dhcp-option DNS 208.67.222.222,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.8.0.6 10.8.0.5'
Fri Jan 29 10:13:34 2010 OPTIONS IMPORT: timers and/or timeouts modified
Fri Jan 29 10:13:34 2010 OPTIONS IMPORT: --ifconfig/up options modified
Fri Jan 29 10:13:34 2010 OPTIONS IMPORT: route options modified
Fri Jan 29 10:13:34 2010 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Fri Jan 29 10:13:34 2010 ROUTE default_gateway=192.168.21.254
Fri Jan 29 10:13:34 2010 TUN/TAP device tun0 opened
Fri Jan 29 10:13:34 2010 TUN/TAP TX queue length set to 100
Fri Jan 29 10:13:34 2010 /sbin/ifconfig tun0 10.8.0.6 pointopoint 10.8.0.5 mtu 1500
Fri Jan 29 10:13:34 2010 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 10.8.0.5
Fri Jan 29 10:13:34 2010 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.8.0.5
Fri Jan 29 10:13:34 2010 /sbin/route add -net 10.8.0.1 netmask 255.255.255.255 gw 10.8.0.5
Fri Jan 29 10:13:34 2010 Initialization Sequence Completed
^CFri Jan 29 10:14:01 2010 event_wait : Interrupted system call (code=4)
Fri Jan 29 10:14:01 2010 TCP/UDP: Closing socket
Fri Jan 29 10:14:01 2010 /sbin/route del -net 10.8.0.1 netmask 255.255.255.255
Fri Jan 29 10:14:01 2010 /sbin/route del -net 0.0.0.0 netmask 128.0.0.0
Fri Jan 29 10:14:01 2010 /sbin/route del -net 128.0.0.0 netmask 128.0.0.0
Fri Jan 29 10:14:01 2010 Closing TUN/TAP interface
Fri Jan 29 10:14:01 2010 /sbin/ifconfig tun0 0.0.0.0
Fri Jan 29 10:14:02 2010 SIGINT[hard,] received, process exiting
```_________________________________________________________________________

SERVER CONFIG/LOG

OPENVPN_CONFIG=
port 443
proto tcp
dev tun
ca /tmp/openvpn/ca.crt
cert /tmp/openvpn/cert.pem
key /tmp/openvpn/key.pem
dh /tmp/openvpn/dh.pem
server 10.8.0.0 255.255.255.0
push "redirect-gateway local def1"
push "dhcp-option DNS 208.67.222.222"
keepalive 10 120
comp-lzo
persist-key
persist-tun
verb 3

RC_FIREWALL=
iptables -I INPUT -p udp --dport 11907 -j logaccept
iptables -I INPUT -p tcp --dport 11907 -j logaccept
iptables -I INPUT -p udp --dport 443 -j logaccept
iptables -I INPUT -p tcp --dport 443 -j logaccept
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE

```
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: OpenVPN 2.1_rc20 mipsel-unknown-linux-gnu [SSL] [LZO1] [EPOLL] built on Oct 10 2009
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: Diffie-Hellman initialized with 1024 bit key
Jan 29 10:06:00 DD-WRT daemon.warn openvpn[774]: WARNING: file '/tmp/openvpn/key.pem' is group or others accessible
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: TLS-Auth MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: TUN/TAP device tun0 opened
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: TUN/TAP TX queue length set to 100
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: /sbin/ifconfig tun0 10.8.0.1 pointopoint 10.8.0.2 mtu 1500
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: /sbin/route add -net 10.8.0.0 netmask 255.255.255.0 gw 10.8.0.2
Jan 29 10:06:00 DD-WRT daemon.notice openvpn[774]: Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: Listening for incoming TCP connection on [undef]:443
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: Socket Buffers: R=[43689->65534] S=[16384->65534]
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: TCPv4_SERVER link local (bound): [undef]:443
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: TCPv4_SERVER link remote: [undef]
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: MULTI: multi_init called, r=256 v=256
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: IFCONFIG POOL: base=10.8.0.4 size=62
Jan 29 10:06:01 DD-WRT daemon.warn openvpn[798]: Note: sys_epoll API is unavailable, falling back to poll/select API
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: MULTI: TCP INIT maxclients=1024 maxevents=1028
Jan 29 10:06:01 DD-WRT daemon.notice openvpn[798]: Initialization Sequence Completed
Jan 29 10:06:20 DD-WRT authpriv.notice dropbear[815]: pubkey auth succeeded for 'root' with key md5 20:49:a1:18:08:d2:25:61:be:64:41:3d:12:19:a1:78 from 170.213.131.190:34112
Jan 29 10:13:14 DD-WRT authpriv.info dropbear[815]: exit after auth (root): Exited normally
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: MULTI: multi_create_instance called
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: Re-using SSL/TLS context
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: LZO compression initialized
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: Control Channel MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: TCP connection established with 170.213.131.190:8397
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: Socket Buffers: R=[65534->65534] S=[65534->65534]
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: TCPv4_SERVER link local: [undef]
Jan 29 10:13:30 DD-WRT daemon.notice openvpn[798]: TCPv4_SERVER link remote: 170.213.131.190:8397
Jan 29 10:13:31 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 TLS: Initial packet from 170.213.131.190:8397, sid=d9274e0a 997a8057
Jan 29 10:13:32 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 VERIFY OK: ***
Jan 29 10:13:32 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 VERIFY OK: ***
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: 170.213.131.190:8397 [client] Peer Connection Initiated with 170.213.131.190:8397
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: client/170.213.131.190:8397 MULTI: Learn: 10.8.0.6 -> client/170.213.131.190:8397
Jan 29 10:13:33 DD-WRT daemon.notice openvpn[798]: client/170.213.131.190:8397 MULTI: primary virtual IP for client/170.213.131.190:8397: 10.8.0.6
Jan 29 10:13:34 DD-WRT daemon.notice openvpn[798]: client/170.213.131.190:8397 PUSH: Received control message: 'PUSH_REQUEST'
Jan 29 10:13:34 DD-WRT daemon.notice openvpn[798]: client/170.213.131.190:8397 SENT CONTROL [client]: 'PUSH_REPLY,redirect-gateway local def1,dhcp-option DNS 208.67.222.222,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.8.0.6 10.8.0.5' (status=1)
Jan 29 10:14:04 DD-WRT daemon.err openvpn[798]: client/170.213.131.190:8397 Connection reset, restarting [0]
Jan 29 10:14:04 DD-WRT daemon.notice openvpn[798]: client/170.213.131.190:8397 SIGUSR1[soft,connection-reset] received, client-instance restarting
Jan 29 10:14:04 DD-WRT daemon.notice openvpn[798]: TCP/UDP: Closing socket
Jan 29 10:25:53 DD-WRT authpriv.notice dropbear[1280]: pubkey auth succeeded for 'root' with key md5 20:49:a1:18:08:d2:25:61:be:64:41:3d:12:19:a1:78 from 170.213.131.190:17836

```

---

### Post by linux000019 on 2010-01-29
linux guru told me to run traceroute; heres results:

```
ryan@ryan-laptop:/etc/openvpn$ ping 10.8.0.1
PING 10.8.0.1 (10.8.0.1) 56(84) bytes of data.
^C
--- 10.8.0.1 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6047ms

ryan@ryan-laptop:/etc/openvpn$ traceroute 10.8.0.1
traceroute to 10.8.0.1 (10.8.0.1), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  *^C
ryan@ryan-laptop:/etc/openvpn$ traceroute 192.168.1.1
traceroute to 192.168.1.1 (192.168.1.1), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  *^C
ryan@ryan-laptop:/etc/openvpn$ traceroute 10.8.0.5
traceroute to 10.8.0.5 (10.8.0.5), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  *^C
ryan@ryan-laptop:/etc/openvpn$ traceroute 10.8.0.6
traceroute to 10.8.0.6 (10.8.0.6), 30 hops max, 60 byte packets
 1  10.8.0.6 (10.8.0.6)  0.031 ms  0.008 ms  0.007 ms
ryan@ryan-laptop:/etc/openvpn$ traceroute google.com
traceroute to google.com (66.102.7.105), 30 hops max, 60 byte packets
 1  192.168.21.254 (192.168.21.254)  2.147 ms  2.409 ms  2.484 ms
 2  192.168.247.242 (192.168.247.242)  2.711 ms  3.036 ms  3.166 ms
 3  10.45.249.253 (10.45.249.253)  3.398 ms  3.501 ms  3.573 ms
 4  * * *
 5  * * *
 6  *^C
ryan@ryan-laptop:/etc/openvpn$ 
```

---

