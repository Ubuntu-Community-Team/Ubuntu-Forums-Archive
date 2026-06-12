---
title: "OpenVPN problems"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by ericus on 2009-03-09
I've been trying to figure out how to tunnel all my internet traffic trough an OpenVPN tunnel; [www.ivacy.com](www.ivacy.com), but so far it's not working out so well.

In /etc/openvpn I have all the required config-files.
```
ericus@charlotte:~$ ls /etc/openvpn/
Ivacy-ca.crt  Ivacy-client.crt  Ivacy-client.key  Ivacy-client.ovpn  Ivacy-client.ovpn~  Ivacy-tls.key  update-resolv-conf
```

Connecting with network-manager-openvpn seems to be doomed to fail, so right now I run this command..
```
sudo openvpn --config /etc/openvpn/Ivacy-client.ovpn
```
..and it gives me this, which for me looks fine?
```
Mon Mar  9 20:21:28 2009 OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 15 2008
Enter Auth Username:xxxxxxx
Enter Auth Password:
Mon Mar  9 20:21:35 2009 /usr/bin/openssl-vulnkey -q -b 2048 -m <modulus omitted>
Mon Mar  9 20:21:35 2009 Control Channel Authentication: using '/etc/openvpn/Ivacy-tls.key' as a OpenVPN static key file
Mon Mar  9 20:21:35 2009 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar  9 20:21:35 2009 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar  9 20:21:35 2009 LZO compression initialized
Mon Mar  9 20:21:35 2009 Local Options hash (VER=V4): '5474e'
Mon Mar  9 20:21:35 2009 Expected Remote Options hash (VER=V4): '141683'
Mon Mar  9 20:21:35 2009 Socket Buffers: R=[112640->131072] S=[112640->131072]
Mon Mar  9 20:21:35 2009 UDPv4 link local: [undef]
Mon Mar  9 20:21:35 2009 UDPv4 link remote: xx.xx.xx.xx:1194
Mon Mar  9 20:21:35 2009 TLS: Initial packet from xx.xx.xx.xx:1194, sid=e47bccdc b494c687
Mon Mar  9 20:21:35 2009 VERIFY OK: depth=1, /C=RU/ST=MR/L=Moscow/O=ivacy.com/CN=ivacy.com_CA/emailAddress=admin@ivacy.com
Mon Mar  9 20:21:35 2009 VERIFY OK: nsCertType=SERVER
Mon Mar  9 20:21:35 2009 VERIFY OK: depth=0, /C=RU/ST=MR/L=Moscow/O=ivacy.com/CN=openvpn.ivacy.com/emailAddress=admin@ivacy.com
Mon Mar  9 20:21:36 2009 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Mar  9 20:21:36 2009 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar  9 20:21:36 2009 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Mar  9 20:21:36 2009 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar  9 20:21:36 2009 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Mon Mar  9 20:21:36 2009 [openvpn.ivacy.com] Peer Connection Initiated with 213.232.208.199:1194
Mon Mar  9 20:21:38 2009 SENT CONTROL [openvpn.ivacy.com]: 'PUSH_REQUEST' (status=1)
Mon Mar  9 20:21:38 2009 PUSH: Received control message: 'PUSH_REPLY,route 1.0.0.0 255.0.0.0,dhcp-option DNS 1.254.2.2,dhcp-option DNS 1.254.2.3,dhcp-option DOMAIN vpn,explicit-exit-notify 2,route-gateway 1.2.124.1,topology subnet,ping 10,ping-restart 60,ifconfig 1.2.124.104 255.255.255.0'
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: timers and/or timeouts modified
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: explicit notify parm(s) modified
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: --ifconfig/up options modified
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: route options modified
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: route-related options modified
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Mon Mar  9 20:21:38 2009 ROUTE default_gateway=85.226.52.1
Mon Mar  9 20:21:38 2009 TUN/TAP device tun0 opened
Mon Mar  9 20:21:38 2009 TUN/TAP TX queue length set to 100
Mon Mar  9 20:21:38 2009 /sbin/ifconfig tun0 1.2.124.104 netmask 255.255.255.0 mtu 1500 broadcast 1.2.124.255
Mon Mar  9 20:21:38 2009 /etc/openvpn/update-resolv-conf tun0 1500 1542 1.2.124.104 255.255.255.0 init
dhcp-option DNS 1.254.2.2
dhcp-option DNS 1.254.2.3
dhcp-option DOMAIN vpn
Mon Mar  9 20:21:39 2009 /sbin/route add -net 213.232.208.199 netmask 255.255.255.255 gw 85.226.52.1
Mon Mar  9 20:21:39 2009 /sbin/route del -net 0.0.0.0 netmask 0.0.0.0
Mon Mar  9 20:21:39 2009 /sbin/route add -net 0.0.0.0 netmask 0.0.0.0 gw 1.2.124.1
Mon Mar  9 20:21:39 2009 WARNING: potential route subnet conflict between local LAN [1.2.124.0/255.255.255.0] and remote VPN [1.0.0.0/255.0.0.0]
Mon Mar  9 20:21:39 2009 /sbin/route add -net 1.0.0.0 netmask 255.0.0.0 gw 1.2.124.1
Mon Mar  9 20:21:39 2009 Initialization Sequence Completed
```

At this state, I cannot ping or use internet at all, so I tried *sudo dhclient tun0*; and it returns this:
```
There is already a pid file /var/run/dhclient.pid with pid 8291
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

tun0: unknown hardware address type 65534
tun0: unknown hardware address type 65534
Listening on LPF/tun0/
Sending on   LPF/tun0/
Sending on   Socket/fallback
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Seems strange that they dont have any IP for me, doesnt it?
Am I missing something? What am I doing wrong.
New to this (and somewhat new with linux), so please explain and help me out.

Thanks in advance,
Ericus

---

### Post by jherasb on 2009-03-09
The most probably problem is that once you connect the server assign you a default route for everything (0.0.0.0) to 1.2.124.1 that is the ip of the server in the tunnel, but What is the public IP of the server? Maybe 213.232.208.199 and 85.226.52.1 your gateway router of the client?

/sbin/route add -net 213.232.208.199 netmask 255.255.255.255 gw 85.226.52.1

The thing is, once the computer is connected hot to reach the public IP of the router?

If your normal gateway is X.X.X.X you need add a static router to your server public IP before connect.

Also it can be  a server error, maybe iptables in the server are blocking your outgoing traffic through the server, or maybe the problem is in the route of your client.

Can you post your client router after connect?

And your ifconfig (the tun0 related only)?

Also post the server.conf of openvpn without the certs.

Jesus.


> **ericus said:**
> I've been trying to figure out how to tunnel all my internet traffic trough an OpenVPN tunnel; [www.ivacy.com](www.ivacy.com), but so far it's not working out so well.

In /etc/openvpn I have all the required config-files.
```
ericus@charlotte:~$ ls /etc/openvpn/
Ivacy-ca.crt  Ivacy-client.crt  Ivacy-client.key  Ivacy-client.ovpn  Ivacy-client.ovpn~  Ivacy-tls.key  update-resolv-conf
```

Connecting with network-manager-openvpn seems to be doomed to fail, so right now I run this command..
```
sudo openvpn --config /etc/openvpn/Ivacy-client.ovpn
```
..and it gives me this, which for me looks fine?
```
Mon Mar  9 20:21:28 2009 OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 15 2008
Enter Auth Username:xxxxxxx
Enter Auth Password:
Mon Mar  9 20:21:35 2009 /usr/bin/openssl-vulnkey -q -b 2048 -m <modulus omitted>
Mon Mar  9 20:21:35 2009 Control Channel Authentication: using '/etc/openvpn/Ivacy-tls.key' as a OpenVPN static key file
Mon Mar  9 20:21:35 2009 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar  9 20:21:35 2009 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar  9 20:21:35 2009 LZO compression initialized
Mon Mar  9 20:21:35 2009 Local Options hash (VER=V4): '5474e'
Mon Mar  9 20:21:35 2009 Expected Remote Options hash (VER=V4): '141683'
Mon Mar  9 20:21:35 2009 Socket Buffers: R=[112640->131072] S=[112640->131072]
Mon Mar  9 20:21:35 2009 UDPv4 link local: [undef]
Mon Mar  9 20:21:35 2009 UDPv4 link remote: xx.xx.xx.xx:1194
Mon Mar  9 20:21:35 2009 TLS: Initial packet from xx.xx.xx.xx:1194, sid=e47bccdc b494c687
Mon Mar  9 20:21:35 2009 VERIFY OK: depth=1, /C=RU/ST=MR/L=Moscow/O=ivacy.com/CN=ivacy.com_CA/emailAddress=admin@ivacy.com
Mon Mar  9 20:21:35 2009 VERIFY OK: nsCertType=SERVER
Mon Mar  9 20:21:35 2009 VERIFY OK: depth=0, /C=RU/ST=MR/L=Moscow/O=ivacy.com/CN=openvpn.ivacy.com/emailAddress=admin@ivacy.com
Mon Mar  9 20:21:36 2009 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Mar  9 20:21:36 2009 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar  9 20:21:36 2009 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Mar  9 20:21:36 2009 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar  9 20:21:36 2009 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Mon Mar  9 20:21:36 2009 [openvpn.ivacy.com] Peer Connection Initiated with 213.232.208.199:1194
Mon Mar  9 20:21:38 2009 SENT CONTROL [openvpn.ivacy.com]: 'PUSH_REQUEST' (status=1)
Mon Mar  9 20:21:38 2009 PUSH: Received control message: 'PUSH_REPLY,route 1.0.0.0 255.0.0.0,dhcp-option DNS 1.254.2.2,dhcp-option DNS 1.254.2.3,dhcp-option DOMAIN vpn,explicit-exit-notify 2,route-gateway 1.2.124.1,topology subnet,ping 10,ping-restart 60,ifconfig 1.2.124.104 255.255.255.0'
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: timers and/or timeouts modified
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: explicit notify parm(s) modified
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: --ifconfig/up options modified
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: route options modified
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: route-related options modified
Mon Mar  9 20:21:38 2009 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Mon Mar  9 20:21:38 2009 ROUTE default_gateway=85.226.52.1
Mon Mar  9 20:21:38 2009 TUN/TAP device tun0 opened
Mon Mar  9 20:21:38 2009 TUN/TAP TX queue length set to 100
Mon Mar  9 20:21:38 2009 /sbin/ifconfig tun0 1.2.124.104 netmask 255.255.255.0 mtu 1500 broadcast 1.2.124.255
Mon Mar  9 20:21:38 2009 /etc/openvpn/update-resolv-conf tun0 1500 1542 1.2.124.104 255.255.255.0 init
dhcp-option DNS 1.254.2.2
dhcp-option DNS 1.254.2.3
dhcp-option DOMAIN vpn
Mon Mar  9 20:21:39 2009 /sbin/route add -net 213.232.208.199 netmask 255.255.255.255 gw 85.226.52.1
Mon Mar  9 20:21:39 2009 /sbin/route del -net 0.0.0.0 netmask 0.0.0.0
Mon Mar  9 20:21:39 2009 /sbin/route add -net 0.0.0.0 netmask 0.0.0.0 gw 1.2.124.1
Mon Mar  9 20:21:39 2009 WARNING: potential route subnet conflict between local LAN [1.2.124.0/255.255.255.0] and remote VPN [1.0.0.0/255.0.0.0]
Mon Mar  9 20:21:39 2009 /sbin/route add -net 1.0.0.0 netmask 255.0.0.0 gw 1.2.124.1
Mon Mar  9 20:21:39 2009 Initialization Sequence Completed
```

At this state, I cannot ping or use internet at all, so I tried *sudo dhclient tun0*; and it returns this:
```
There is already a pid file /var/run/dhclient.pid with pid 8291
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

tun0: unknown hardware address type 65534
tun0: unknown hardware address type 65534
Listening on LPF/tun0/
Sending on   LPF/tun0/
Sending on   Socket/fallback
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on tun0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Seems strange that they dont have any IP for me, doesnt it?
Am I missing something? What am I doing wrong.
New to this (and somewhat new with linux), so please explain and help me out.

Thanks in advance,
Ericus

---

### Post by ericus on 2009-03-09
> **jherasb said:**
> The most probably problem is that once you connect the server assign you a default route for everything (0.0.0.0) to 1.2.124.1 that is the ip of the server in the tunnel, but What is the public IP of the server? Maybe 213.232.208.199 and 85.226.52.1 your gateway router of the client?

/sbin/route add -net 213.232.208.199 netmask 255.255.255.255 gw 85.226.52.1

The thing is, once the computer is connected hot to reach the public IP of the router?

If your normal gateway is X.X.X.X you need add a static router to your server public IP before connect.

Also it can be  a server error, maybe iptables in the server are blocking your outgoing traffic through the server, or maybe the problem is in the route of your client.

Can you post your client router after connect?

And your ifconfig (the tun0 related only)?

Also post the server.conf of openvpn without the certs.

Jesus.


Thank you for answering.

This is tun0:
```
tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:1.2.124.104  P-t-P:1.2.124.104  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

By client router you mean route -n?
```
ericus@charlotte:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.232.208.199 85.226.52.1     255.255.255.255 UGH   0      0        0 eth0
1.2.124.0       0.0.0.0         255.255.255.0   U     0      0        0 tun0
85.226.52.0     0.0.0.0         255.255.252.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
1.0.0.0         1.2.124.1       255.0.0.0       UG    0      0        0 tun0
0.0.0.0         1.2.124.1       0.0.0.0         UG    0      0        0 tun0
```

I can ping 213.232.208.199, but nothing else.
```
ericus@charlotte:~$ ping google.se
PING google.se (66.249.93.104) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
```

Dont have any server.conf file.

---

### Post by jherasb on 2009-03-09
Try to add a manual route to your client before make the connection.

route add YOUR_SERVER_IP netmask 255.255.255.255 YOU_LOCAL_GATEWAY_IP.

Are you activate IP Forwarding in the server?

Jesus

---

### Post by ericus on 2009-03-09
Double, sorry

---

### Post by ericus on 2009-03-09
> **jherasb said:**
> Try to add a manual route to your client before make the connection.

route add YOUR_SERVER_IP netmask 255.255.255.255 YOU_LOCAL_GATEWAY_IP.

Are you activate IP Forwarding in the server?

Jesus

Where do I find server IP and local gateway IP? Is it this?
sudo /sbin/route add -net 213.232.208.199 netmask 255.255.255.255 gw 85.226.52.1
Didnt help.

The server is not mine, so I dont know.
I'm not very familiar with this, much of it is hard to understand :(

---

### Post by jherasb on 2009-03-09
Ok. There is a line in your client config file  Ivacy-client.ovpn like remote YOUR_SERVER_NAME 1194. The line start with remote.

If you has a name ping to that name and this is your server IP, if you has a IP in your remote you add the route for that IP like I said in my last message.

Jesus


> **ericus said:**
> Where do I find server IP and local gateway IP?
The server is not mine, so I dont know.
I'm not very familiar with this, much of it is hard to understand :(

---

### Post by ericus on 2009-03-09
> **jherasb said:**
> Ok. There is a line in your client config file  Ivacy-client.ovpn like remote YOUR_SERVER_NAME 1194. The line start with remote.

If you has a name ping to that name and this is your server IP, if you has a IP in your remote you add the route for that IP like I said in my last message.

Jesus

openvpn.ivacy.com IP is 213.232.208.199.
Running this command before connecting did not help :(
sudo /sbin/route add -net 213.232.208.199 netmask 255.255.255.255 gw 85.226.52.1

---

### Post by jherasb on 2009-03-09
I think the problem maybe is the command
sudo /sbin/route add 213.232.208.199 gw 85.226.52.1 

This is a route just for host.

Can you try this and post a tracroute to google.com?
Jesus

> **ericus said:**
> openvpn.ivacy.com IP is 213.232.208.199.
Running this command before connecting did not help :(
sudo /sbin/route add -net 213.232.208.199 netmask 255.255.255.255 gw 85.226.52.1

---

### Post by ericus on 2009-03-09
> **jherasb said:**
> I think the problem maybe is the command
sudo /sbin/route add 213.232.208.199 gw 85.226.52.1 

This is a route just for host.

Can you try this and post a tracroute to google.com?
Jesus

```
ericus@charlotte:~$ traceroute www.google.com
traceroute to www.google.com (74.125.79.103), 30 hops max, 40 byte packets
send: Operation not permitted

```
Weird.

---

### Post by jherasb on 2009-03-09
Your config is correct. Ask for administrator server where is the problem, because there something bad in the server, I have the config as you and it works. 

Sorry but it is everything I can do if you don't have access to the server.

Regards,
Jesus

> **ericus said:**
> ```
ericus@charlotte:~$ traceroute www.google.com
traceroute to www.google.com (74.125.79.103), 30 hops max, 40 byte packets
send: Operation not permitted

```
Weird.

---

### Post by ericus on 2009-03-09
> **jherasb said:**
> Your config is correct. Ask for administrator server where is the problem, because there something bad in the server, I have the config as you and it works. 

Sorry but it is everything I can do if you don't have access to the server.

Regards,
Jesus

Okay. Read something about pushing DNS and thing like that before it would work, but didnt understand even half of it.

But thanks for taking your time, I appreciate it!

---

### Post by jherasb on 2009-03-09
It is a routing problem, the push DNS works fine because you can resolve DNS in the traceroute to google.

If you find the problem please post a comment.

Regards,
Jesus

> **ericus said:**
> Okay. Read something about pushing DNS and thing like that before it would work, but didnt understand even half of it.

But thanks for taking your time, I appreciate it!

---

### Post by ericus on 2009-03-10
Anyone else who might have a clue?

---

### Post by ericus on 2009-03-10
Tried to connect from my windows machine, and it worked great.
How do I fix this? :( Drives me nuts.. I'm so close!

I can ping the server IP. I cant ping anything else.
Routing problems?

---

### Post by SpaceTeddy on 2009-03-11
Found your PM.

So let me summarize what your setup is. You want to use the service provided by [www.ivacy.com](www.ivacy.com). They supply a sample configuration, but it does not work with your computer, right ?

I will not sign up to their service just to try this out - but it would really help if you posted the client configuration and let me have a look at it. Also, the route command that you show are kind of messed up, as you have errors in your client about conflicting subnets (don't ask me where they are coming from).

The problem that was discussed earlier (i.e. you missing a route to your vpn server via your normal gateway) is not really an issue, as your routing table clearly shows this route being present after a connect...

here is an output earlier from the thread i can use to explain this:
> ericus@charlotte:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
213.232.208.199 85.226.52.1     255.255.255.255 UGH   0      0        0 eth0
1.2.124.0       0.0.0.0         255.255.255.0   U     0      0        0 tun0
85.226.52.0     0.0.0.0         255.255.252.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
1.0.0.0         1.2.124.1       255.0.0.0       UG    0      0        0 tun0
0.0.0.0         1.2.124.1       0.0.0.0         UG    0      0        0 tun0

Looking at this, you can see that all your traffic is redirected via 1.2.124.1 - but 1.2.124.1 MUST NOT be redirected. That's what the first rule is for. As 213.232.208.199 is your VPN server, it is the only IP in the internet that is still contacted directly. and it is still the only ip that as your old default gateway (i.e. the one from your ISP). So your routing seems to be setup correctly from my point of view. 

> ericus@charlotte:~$ traceroute [www.google.com](www.google.com)
traceroute to [www.google.com](www.google.com) (74.125.79.103), 30 hops max, 40 byte packets
send: Operation not permitted

This error usually only occurs at the local machine and means that the kernel forbids your to send a packet. If this was a remote error (i.e. from the vpn server) this should be an icmp reply (or so i think). Anyway, this usually indicates that you have some kind of firewall and/or packet filter active that prevents you from sending stuff to the internet. To see if i am running even slightly in the right direction, can you please post the output of the following command ?

```
sudo iptables -L -vnx
```

otherwise - this seems to be very confusing...

---

### Post by ericus on 2009-03-11
> **SpaceTeddy said:**
> Found your PM.

So let me summarize what your setup is. You want to use the service provided by [www.ivacy.com](www.ivacy.com). They supply a sample configuration, but it does not work with your computer, right ?

I will not sign up to their service just to try this out - but it would really help if you posted the client configuration and let me have a look at it. Also, the route command that you show are kind of messed up, as you have errors in your client about conflicting subnets (don't ask me where they are coming from).

The problem that was discussed earlier (i.e. you missing a route to your vpn server via your normal gateway) is not really an issue, as your routing table clearly shows this route being present after a connect...

here is an output earlier from the thread i can use to explain this:


Looking at this, you can see that all your traffic is redirected via 1.2.124.1 - but 1.2.124.1 MUST NOT be redirected. That's what the first rule is for. As 213.232.208.199 is your VPN server, it is the only IP in the internet that is still contacted directly. and it is still the only ip that as your old default gateway (i.e. the one from your ISP). So your routing seems to be setup correctly from my point of view. 



This error usually only occurs at the local machine and means that the kernel forbids your to send a packet. If this was a remote error (i.e. from the vpn server) this should be an icmp reply (or so i think). Anyway, this usually indicates that you have some kind of firewall and/or packet filter active that prevents you from sending stuff to the internet. To see if i am running even slightly in the right direction, can you please post the output of the following command ?

```
sudo iptables -L -vnx
```

otherwise - this seems to be very confusing...

First of all I must give you a BIG thank you for taking your time.


```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   37  1480 ACCEPT     tcp  --  any    any     localhost            anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
   14  1175 ACCEPT     udp  --  any    any     localhost            anywhere            
   37  1628 ACCEPT     all  --  lo     any     anywhere             anywhere            
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            limit: avg 10/sec burst 5 
    0     0 DROP       all  --  eth0   any     anywhere             255.255.255.255     
    0     0 DROP       all  --  any    any     anywhere             192.168.1.255       
    0     0 DROP       all  --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere            
    0     0 DROP       all  --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8 
    0     0 DROP       all  --  any    any     255.255.255.255      anywhere            
    0     0 DROP       all  --  any    any     anywhere             0.0.0.0             
    0     0 DROP       all  --  any    any     anywhere             anywhere            state INVALID 
    0     0 LSI        all  -f  any    any     anywhere             anywhere            limit: avg 10/min burst 5 
  417  417K INBOUND    all  --  eth0   any     anywhere             anywhere            
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 5 packets, 284 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  any    any     charlotte.system.lan  localhost           tcp dpt:domain 
    0     0 ACCEPT     udp  --  any    any     charlotte.system.lan  localhost           udp dpt:domain 
   88  4283 ACCEPT     all  --  any    lo      anywhere             anywhere            
    0     0 DROP       all  --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere            
    6   438 DROP       all  --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8 
    0     0 DROP       all  --  any    any     255.255.255.255      anywhere            
    0     0 DROP       all  --  any    any     anywhere             0.0.0.0             
    0     0 DROP       all  --  any    any     anywhere             anywhere            state INVALID 
  381 46450 OUTBOUND   all  --  any    eth0    anywhere             anywhere            
    5   284 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    5   284 LOG        all  --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  359  409K ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
   56  7989 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:26208 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:26208 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:openvpn 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:openvpn 
    0     0 LSI        all  --  any    any     anywhere             anywhere            

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
    0     0 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
    0     0 LOG        icmp --  any    any     anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       icmp --  any    any     anywhere             anywhere            icmp echo-request 
    0     0 LOG        all  --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain LSO (6 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
    0     0 REJECT     all  --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            
  306 40285 ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
   56  5191 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 LSO        tcp  --  any    any     anywhere             anywhere            tcp dpt:26208 
    0     0 LSO        udp  --  any    any     anywhere             anywhere            udp dpt:26208 
    0     0 LSO        tcp  --  any    any     anywhere             anywhere            tcp dpt:ftp 
    0     0 LSO        udp  --  any    any     anywhere             anywhere            udp dpt:fsp 
   19   974 ACCEPT     all  --  any    any     anywhere             anywhere            
```

Long output there.

Here is Ivacy-client.ovpn:
```
client
dev tun
proto udp
remote openvpn.ivacy.com 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca /etc/openvpn/Ivacy-ca.crt
cert /etc/openvpn/Ivacy-client.crt
key /etc/openvpn/Ivacy-client.key
tls-auth /etc/openvpn/Ivacy-tls.key 1
ns-cert-type server
comp-lzo
verb 3
auth-user-pass
redirect-gateway
script-security 3
reneg-sec 0
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf
```
2 last rows from a howto, tried with them and without them.

Also my sys.log gives me a lot of lines like this, is it relevant?
```
Mar 11 14:26:32 charlotte kernel: [61699.640046] Unknown OutputIN= OUT=tun0 SRC=1.2.124.107 DST=65.54.239.80 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=59816 DF PROTO=TCP SPT=59138 DPT=1863 WINDOW=5840 RES=0x00
```

---

### Post by SpaceTeddy on 2009-03-11
ok, as i suspected, you have a firewall loaded. DISABLE IT ! Then retry to connect (the iptables command you pasted the output from should look like this when you have a disabled firewall)

> Chain INPUT (policy ACCEPT 1027933 packets, 777111460 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 886102 packets, 80631938 bytes)
    pkts      bytes target     prot opt in     out     source               destination         


If this works with an empty, all allowing firewall we can get into configuring the firewall properly. 
In case a simple disable of the firewall does not work - these commands will delete any firewall rules temporarily until you reboot:

> sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT

hope it helps :)

---

### Post by ericus on 2009-03-11
> **SpaceTeddy said:**
> ok, as i suspected, you have a firewall loaded. DISABLE IT ! Then retry to connect (the iptables command you pasted the output from should look like this when you have a disabled firewall)



If this works with an empty, all allowing firewall we can get into configuring the firewall properly. 
In case a simple disable of the firewall does not work - these commands will delete any firewall rules temporarily until you reboot:



hope it helps :)
That did the trick! :D

And now for the next question (:D), how can I ensure myself that all my traffic is tunnel trough without no DNS leaks or things like that?

---

### Post by SpaceTeddy on 2009-03-11
if i read your config correct, you have a full redirect of any and everything that is going and comming from your computer. The rest of the world will see you to connect to everywhere from the vpn server - there is no way to figure out where you really are (unless someone gets a hold of the server logs).

The only thing that you might want to check is if your dns is rewritten as well, as this could give others a hint where you are from (DNS servers are ISP specific). But if you still have the update-resolv-conf in your dns should be automatically rewritten to the DNS provided by the VPN Server. Thus - you are hidden.

glad i could help :)

---

### Post by joniedayie on 2010-08-10
I am having the same issues. I've tried the solutions on this post, none of them have worked. 

I have Kernel 2.6.32 Ubuntu. I was running firestarter, but I have since uninstalled it.

I have cleared my IP tables using the commands here.

I have compiled 2.1.1 of OpenVPN (the latest version) from the source code -- and also tried the 2.1.0 version in the SVN Repository.

My VPN is working fine on my windows machine.

On Ubuntu, I am running openvpn --config c.ovpn as root with the sudo command. 

After Initialization Sequence Compeleted, I open a browser, and I can load the web interface of my openvpn server. I can't, however, load any other web page.

Please help me.

---

### Post by SpaceTeddy on 2010-08-10
most likely missing or incorrect configured dns server - what is the content of your /etc/resolv.conf ?

---

### Post by jherasb on 2010-08-11
It might be three things: route, dns or firewall:
-Route problem. Once you have successfully connected try to do a ping to [www.ubuntu.com](www.ubuntu.com), if it doesn't work, try to do a ping to the IP address 91.189.94.156.

If you can ping to IP but you can't ping to [www.ubuntu.com](www.ubuntu.com) check your /etc/resolv.conf.

If you can't ping to IP please do a "traceroute -n 91.189.94.156" and paste the output to analyze it.

Do you know if the server use the option "push dns" or "push "redirect-gateway"?

Another posible problem is that local and remote network are the same, for example your localnet is 192.168.1.0/24 and the remote network where you need to access is the same.

Kind Regards,
Jesus de las Heras

> **joniedayie said:**
> I am having the same issues. I've tried the solutions on this post, none of them have worked. 

I have Kernel 2.6.32 Ubuntu. I was running firestarter, but I have since uninstalled it.

I have cleared my IP tables using the commands here.

I have compiled 2.1.1 of OpenVPN (the latest version) from the source code -- and also tried the 2.1.0 version in the SVN Repository.

My VPN is working fine on my windows machine.

On Ubuntu, I am running openvpn --config c.ovpn as root with the sudo command. 

After Initialization Sequence Compeleted, I open a browser, and I can load the web interface of my openvpn server. I can't, however, load any other web page.

Please help me.

---

