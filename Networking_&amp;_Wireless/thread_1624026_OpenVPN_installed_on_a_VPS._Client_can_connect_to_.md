---
title: "OpenVPN installed on a VPS. Client can connect to OpenVPN server, but no internet."
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by britbloke on 2010-11-17
I recently setup a cheap VPS for the sole intention of using it as a VPN server so I can access geo restricted content.

I used a script to setup OpenVPN server on the VPS and retrieved the keys for use on my client Win 7 OpenVPN.

On my Win 7 client, I can connect to the VPN, but I can't use the internet.

I'm a novice when it comes to networking and my needs are quite basic.

Here's my log from OpenVPN GUI:

```
Wed Nov 17 11:19:36 2010 OpenVPN 2.1.3 i686-pc-mingw32 [SSL] [LZO2] [PKCS11] built on Oct 20 2010
Wed Nov 17 11:19:36 2010 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Wed Nov 17 11:19:36 2010 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Wed Nov 17 11:19:36 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Wed Nov 17 11:19:36 2010 LZO compression initialized
Wed Nov 17 11:19:36 2010 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Wed Nov 17 11:19:36 2010 Socket Buffers: R=[8192->8192] S=[8192->8192]
Wed Nov 17 11:19:36 2010 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Wed Nov 17 11:19:36 2010 Local Options hash (VER=V4): '41690919'
Wed Nov 17 11:19:36 2010 Expected Remote Options hash (VER=V4): '530fdded'
Wed Nov 17 11:19:36 2010 UDPv4 link local (bound): [undef]:1194
Wed Nov 17 11:19:36 2010 UDPv4 link remote: 184.154.90.198:1194
Wed Nov 17 11:19:36 2010 TLS: Initial packet from 184.154.90.198:1194, sid=5d07493d 6bf9fc82
Wed Nov 17 11:19:37 2010 VERIFY OK: depth=1, /C=US/ST=CA/L=SanFrancisco/O=Fort-Funston/CN=Fort-Funston_CA/emailAddress=me@myhost.mydomain
Wed Nov 17 11:19:37 2010 VERIFY OK: depth=0, /CN=server1
Wed Nov 17 11:19:37 2010 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Nov 17 11:19:37 2010 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Nov 17 11:19:37 2010 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Wed Nov 17 11:19:37 2010 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed Nov 17 11:19:37 2010 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Wed Nov 17 11:19:37 2010 [server1] Peer Connection Initiated with 184.154.90.198:1194
Wed Nov 17 11:19:40 2010 SENT CONTROL [server1]: 'PUSH_REQUEST' (status=1)
Wed Nov 17 11:19:40 2010 PUSH: Received control message: 'PUSH_REPLY,route 10.8.0.0 255.255.255.0,redirect-gateway,route 10.8.0.1,topology net30,ping 10,ping-restart 60,ifconfig 10.8.0.6 10.8.0.5'
Wed Nov 17 11:19:40 2010 OPTIONS IMPORT: timers and/or timeouts modified
Wed Nov 17 11:19:40 2010 OPTIONS IMPORT: --ifconfig/up options modified
Wed Nov 17 11:19:40 2010 OPTIONS IMPORT: route options modified
Wed Nov 17 11:19:40 2010 ROUTE default_gateway=192.168.1.1
Wed Nov 17 11:19:40 2010 TAP-WIN32 device [Local Area Connection 3] opened: \\.\Global\{BA874378-D056-4C92-9150-BDD137E282D5}.tap
Wed Nov 17 11:19:40 2010 TAP-Win32 Driver Version 9.7 
Wed Nov 17 11:19:40 2010 TAP-Win32 MTU=1500
Wed Nov 17 11:19:40 2010 Notified TAP-Win32 driver to set a DHCP IP/netmask of 10.8.0.6/255.255.255.252 on interface {BA874378-D056-4C92-9150-BDD137E282D5} [DHCP-serv: 10.8.0.5, lease-time: 31536000]
Wed Nov 17 11:19:40 2010 Successful ARP Flush on interface [21] {BA874378-D056-4C92-9150-BDD137E282D5}
Wed Nov 17 11:19:42 2010 TEST ROUTES: 3/3 succeeded len=2 ret=1 a=0 u/d=up
Wed Nov 17 11:19:42 2010 C:\WINDOWS\system32\route.exe ADD 184.154.90.198 MASK 255.255.255.255 192.168.1.1
 OK!
Wed Nov 17 11:19:42 2010 C:\WINDOWS\system32\route.exe ADD 0.0.0.0 MASK 128.0.0.0 10.8.0.5
 OK!
Wed Nov 17 11:19:42 2010 C:\WINDOWS\system32\route.exe ADD 128.0.0.0 MASK 128.0.0.0 10.8.0.5
 OK!
Wed Nov 17 11:19:42 2010 C:\WINDOWS\system32\route.exe ADD 10.8.0.0 MASK 255.255.255.0 10.8.0.5
 OK!
Wed Nov 17 11:19:42 2010 C:\WINDOWS\system32\route.exe ADD 10.8.0.1 MASK 255.255.255.255 10.8.0.5
 OK!
Wed Nov 17 11:19:42 2010 Initialization Sequence Completed
```

---

### Post by SeijiSensei on 2010-11-17
The virtual server is running Ubuntu or some other Linux flavor?

See if the suggestion I made here works for you: [http://ubuntuforums.org/showpost.php?p=10128058&postcount=4](http://ubuntuforums.org/showpost.php?p=10128058&postcount=4)

---

### Post by britbloke on 2010-11-17
> **SeijiSensei said:**
> The virtual server is running Ubuntu or some other Linux flavor?

See if the suggestion I made here works for you: [http://ubuntuforums.org/showpost.php?p=10128058&postcount=4](http://ubuntuforums.org/showpost.php?p=10128058&postcount=4)It's Debian 5, but I also tried CentOS originally, and both give me the same problem.

I will take a look at the post you mentioned.

---

### Post by britbloke on 2010-11-18
I tried your post and edited the sysctl.conf file, but I still get exactly the same as I originally posted.

I also reinstalled my VPS with Ubuntu 9 to see if that makes a difference, but the same problem occurs.

---

### Post by SeijiSensei on 2010-11-19
You need to "masquerade" the tunnelled connection so it appears to be coming from the server's external IP address.  Google for "iptables masquerade"; you'll find a large number of tutorials.

Something as simple as:

```

iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to your.external.ip.addr
iptables -A FORWARD -i tun0 -o eth0 -j ACCEPT
iptables -A FORWARD -i eth0 -o tun0 -j ACCEPT

```

might be enough.

---

### Post by britbloke on 2010-11-22
> **SeijiSensei said:**
> You need to "masquerade" the tunnelled connection so it appears to be coming from the server's external IP address.  Google for "iptables masquerade"; you'll find a large number of tutorials.

Something as simple as:

```

iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to your.external.ip.addr
iptables -A FORWARD -i tun0 -o eth0 -j ACCEPT
iptables -A FORWARD -i eth0 -o tun0 -j ACCEPT

```might be enough.Thanks, I got it working great now.

It was an iptables issues. I believe that it wasn't correctly activated on my VPS, so I got it re-activated.

I then used:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o venet0 -j MASQUERADE
```
And I'm now connected and can view websites via my OpenVPN server.

---

