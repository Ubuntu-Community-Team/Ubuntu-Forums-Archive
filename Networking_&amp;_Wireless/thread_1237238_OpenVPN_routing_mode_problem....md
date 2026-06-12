---
title: "OpenVPN routing mode problem..."
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by maxchock on 2009-08-11
Hi all,

I'm a internet cafe operator and recently i have a idea to setup a VPN so other's internet cafe can link together for the convenience while playing multiplayer LAN game such as Counter strike, warcraft and etc.

This is the idea...
[IMG]http://www.buddyjoy.com/images/phocagallery/thumbs/phoca_thumb_l_planning.jpg[/IMG]

Before getting such ideal environment, my current testing environment is actually like look like this.
[IMG]http://www.buddyjoy.com/images/phocagallery/thumbs/phoca_thumb_l_testsite.jpg?imagesid=b8b6dfb49b671958eb5c3955e39036a7[/IMG]


This is the **SERVER **configuration file (/etc/openvpn/atomicsv.conf)
```

# Which local IP address should OpenVPN 
# listen on? (optional) 
local 192.168.120.16 
port 1194

#client configuration directory
client-config-dir /etc/openvpn/clientconfig

#This will tell the OpenVPN server that the 192.168.1.0 subnet should be routed to testclient.
route 192.168.2.0 255.255.255.0


# TCP or UDP server? 
proto udp 

#This is key to configuring our bridge 
#dev tap0 

#use TUN instead of TAP for routed mode
dev tun

#direct these to your generated files 
ca /etc/openvpn/easy-rsa/2.0/keys/ca.crt 
cert /etc/openvpn/easy-rsa/2.0/keys/atomicsv.crt 
key /etc/openvpn/easy-rsa/2.0/keys/atomicsv.key   
dh /etc/openvpn/easy-rsa/2.0/keys/dh1024.pem 
ifconfig-pool-persist ipp.txt 

#ensure the range of ip addresses you use in the last  two arguments 
# of this statement are not in use by  either the DHCP server or any other
# device on your  internal network. 
# server-bridge 192.168.120.12 255.255.255.0 192.168.120.100 192.168.120.254
server 192.168.10.0 255.255.255.0

#needed to allow communication to internal network 
client-to-client 
keepalive 10 120 

#allow network traffic between testclient subnet (192.168.1.0) and other clients of the OpenVPN server
push "route 192.168.2.1 255.255.255.0"

#encryption - very important ;) 
#AES encryption is backed by many security firms
#however if you are concerned about speed use blowfish: "BF-CB"

#cipher AES-128-CBC  
cipher BF-CBC
  
#if you have another subnet you need to provide the route
#push "route 173.23.2.0 255.255.255.0"

#server id protection
#tls-auth ta.key 0

#compression for network speed 
comp-lzo 

# if packets are too large fragment them (only really useful if you have an old router) 
#fragment 1400 

#limit the number of connections
max-clients 100

#some secuurity settings 
# do not use if running server on Windows
user nobody 
group nogroup 
persist-key 
persist-tun 

#log file settings 
status openvpn-status.log 
verb 3 
# authentication plugin
#forces client to have a linux acount in order to connect
#plugin /usr/lib/openvpn/openvpn-auth-pam.so login 

```

the **/etc/openvpn/clientconfig/testclient**
```
iroute 192.168.2.0 255.255.255.0
```

and this is the VPN **client **config files (C:\program files\openvpn\config\testclient.ovpn)
```

client

#dev tap

#use TUN instead of TAP for routed mode
dev tun

mssfix 1400

#dev-node MyTAP  #If you renamed your TAP interface or have more than one TAP interface then remove the # at the beginning and change "MyTAP" to its name

proto udp

remote kazaa2.game-server.cc 1194  #You will need to enter you dyndns account or static IP address here. The number following it is the port you set in the server's config

#route 192.168.2.0 255.255.255.0 vpn_gateway 3  #This is the IP address scheme and subnet of your normal network your server is on.  Your router would usually be 192.168.1.1

resolv-retry infinite

nobind

persist-key

persist-tun

ca "C:\\Program Files\\OpenVPN\\easy-rsa\\keys\\ca.crt"

cert "C:\\Program Files\\OpenVPN\\easy-rsa\\keys\\testclient.crt" # Change the next two lines to match the files in the keys directory.  This should be be different for each client.

key "C:\\Program Files\\OpenVPN\\easy-rsa\\keys\\testclient.key"  # This file should be kept secret

ns-cert-type server

cipher BF-CBC        # Blowfish (default) encrytion

comp-lzo

verb 1

```

after I issue a command to run the VPN server on Ubuntu Hardy..
```

root@atomiclinux:/etc/openvpn# openvpn --config /etc/openvpn/atomicsv.conf --verb 3 
Tue Aug 11 16:29:19 2009 OpenVPN 2.1_rc7 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on May  8 2009
Tue Aug 11 16:29:19 2009 Diffie-Hellman initialized with 1024 bit key
Tue Aug 11 16:29:19 2009 WARNING: file '/etc/openvpn/easy-rsa/2.0/keys/atomicsv.key' is group or others accessible
Tue Aug 11 16:29:19 2009 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Tue Aug 11 16:29:20 2009 TLS-Auth MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Tue Aug 11 16:29:20 2009 TUN/TAP device tun0 opened
Tue Aug 11 16:29:20 2009 TUN/TAP TX queue length set to 100
Tue Aug 11 16:29:20 2009 ifconfig tun0 192.168.10.1 pointopoint 192.168.10.2 mtu 1500
Tue Aug 11 16:29:20 2009 route add -net 192.168.10.0 netmask 255.255.255.0 gw 192.168.10.2
Tue Aug 11 16:29:20 2009 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Tue Aug 11 16:29:20 2009 GID set to nogroup
Tue Aug 11 16:29:20 2009 UID set to nobody
Tue Aug 11 16:29:20 2009 Socket Buffers: R=[124928->131072] S=[124928->131072]
Tue Aug 11 16:29:20 2009 UDPv4 link local (bound): 192.168.120.16:1194
Tue Aug 11 16:29:20 2009 UDPv4 link remote: [undef]
Tue Aug 11 16:29:20 2009 MULTI: multi_init called, r=256 v=256
Tue Aug 11 16:29:20 2009 IFCONFIG POOL: base=192.168.10.4 size=62
Tue Aug 11 16:29:20 2009 IFCONFIG POOL LIST
Tue Aug 11 16:29:20 2009 testclient,192.168.10.4
Tue Aug 11 16:29:20 2009 Initialization Sequence Completed

```

it appear the server is up and running. additional line was added after the VPN client "testclient" connect to the VPN server 

```

Tue Aug 11 16:29:40 2009 MULTI: multi_create_instance called
Tue Aug 11 16:29:40 2009 124.13.127.111:55078 Re-using SSL/TLS context
Tue Aug 11 16:29:40 2009 124.13.127.111:55078 LZO compression initialized
Tue Aug 11 16:29:40 2009 124.13.127.111:55078 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Tue Aug 11 16:29:40 2009 124.13.127.111:55078 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Tue Aug 11 16:29:40 2009 124.13.127.111:55078 Local Options hash (VER=V4): '530fdded'
Tue Aug 11 16:29:40 2009 124.13.127.111:55078 Expected Remote Options hash (VER=V4): '41690919'
Tue Aug 11 16:29:40 2009 124.13.127.111:55078 TLS: Initial packet from 124.13.127.111:55078, sid=9c1c27da e6bcd0b1
Tue Aug 11 16:29:42 2009 124.13.127.111:55078 VERIFY OK: depth=1, /C=MY/ST=SL/L=SERIKEMBANGAN/O=Atomic/OU=gamenet/CN=atomicsv/emailAddress=zvulcan@yahoo.com
Tue Aug 11 16:29:42 2009 124.13.127.111:55078 VERIFY OK: depth=0, /C=MY/ST=SL/L=SERIKEMBANGAN/O=Atomic/OU=gamenet/CN=testclient/emailAddress=zvulcan@yahoo.com
Tue Aug 11 16:29:43 2009 124.13.127.111:55078 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Tue Aug 11 16:29:43 2009 124.13.127.111:55078 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue Aug 11 16:29:43 2009 124.13.127.111:55078 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Tue Aug 11 16:29:43 2009 124.13.127.111:55078 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Tue Aug 11 16:29:43 2009 124.13.127.111:55078 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Tue Aug 11 16:29:43 2009 124.13.127.111:55078 [testclient] Peer Connection Initiated with 124.13.127.111:55078
Tue Aug 11 16:29:43 2009 testclient/124.13.127.111:55078 OPTIONS IMPORT: reading client specific options from: /etc/openvpn/clientconfig/testclient
Tue Aug 11 16:29:43 2009 testclient/124.13.127.111:55078 MULTI: Learn: 192.168.10.6 -> testclient/124.13.127.111:55078
Tue Aug 11 16:29:43 2009 testclient/124.13.127.111:55078 MULTI: primary virtual IP for testclient/124.13.127.111:55078: 192.168.10.6
Tue Aug 11 16:29:43 2009 testclient/124.13.127.111:55078 MULTI: internal route 192.168.2.0/24 -> testclient/124.13.127.111:55078
Tue Aug 11 16:29:43 2009 testclient/124.13.127.111:55078 MULTI: Learn: 192.168.2.0/24 -> testclient/124.13.127.111:55078
Tue Aug 11 16:29:43 2009 testclient/124.13.127.111:55078 REMOVE PUSH ROUTE: 'route 192.168.2.0 255.255.255.0'
Tue Aug 11 16:29:44 2009 testclient/124.13.127.111:55078 PUSH: Received control message: 'PUSH_REQUEST'
Tue Aug 11 16:29:44 2009 testclient/124.13.127.111:55078 SENT CONTROL [testclient]: 'PUSH_REPLY,route 192.168.10.0 255.255.255.0,topology net30,ping 10,ping-restart 120,ifconfig 192.168.10.6 192.168.10.5' (status=1)

```

Log from **testclient**
```

Tue Aug 11 16:29:11 2009 OpenVPN 2.1_rc19 i686-pc-mingw32 [SSL] [LZO2] [PKCS11] built on Jul 16 2009
Tue Aug 11 16:29:11 2009 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Tue Aug 11 16:29:11 2009 LZO compression initialized
Tue Aug 11 16:29:11 2009 UDPv4 link local: [undef]
Tue Aug 11 16:29:11 2009 UDPv4 link remote: 115.133.212.230:1194
Tue Aug 11 16:29:14 2009 [atomicsv] Peer Connection Initiated with 115.133.212.230:1194
Tue Aug 11 16:29:15 2009 TAP-WIN32 device [MyTap] opened: \\.\Global\{ECA104FA-3E28-4A9F-A88F-BF52F28504FD}.tap
Tue Aug 11 16:29:15 2009 Notified TAP-Win32 driver to set a DHCP IP/netmask of 192.168.10.6/255.255.255.252 on interface {ECA104FA-3E28-4A9F-A88F-BF52F28504FD} [DHCP-serv: 192.168.10.5, lease-time: 31536000]
Tue Aug 11 16:29:15 2009 Successful ARP Flush on interface [15] {ECA104FA-3E28-4A9F-A88F-BF52F28504FD}
Tue Aug 11 16:29:21 2009 Initialization Sequence Completed

```

After the VPN server and VPN client are interconnected, I can ping VPN server (VPN-IP 192.168.10.1)  from VPN client (VPN-IP 192.168.10.6) or vice versa. But I can't ping their LAN IP (VPN server LAN-IP 192.168.120.16 and VPN client LAN-IP 192.168.2.3)

I think the problem is around the routing configuration so this is my "route -n" on Ubuntu Hardy
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.2    0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.53.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.186.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.120.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    192.168.10.2    255.255.255.0   UG    0      0        0 tun0
0.0.0.0         192.168.120.1   0.0.0.0         UG    0      0        0 eth0

```

and this is my "route Print" on my vista
```
IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.2.1      192.168.2.3     25
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      169.254.0.0      255.255.0.0         On-link      192.168.10.6    306
  169.254.255.255  255.255.255.255         On-link      192.168.10.6    286
      192.168.2.0    255.255.255.0         On-link       192.168.2.3    281
      192.168.2.3  255.255.255.255         On-link       192.168.2.3    281
    192.168.2.255  255.255.255.255         On-link       192.168.2.3    281
     192.168.10.0    255.255.255.0     192.168.10.5     192.168.10.6     30
     192.168.10.4  255.255.255.252         On-link      192.168.10.6    286
     192.168.10.6  255.255.255.255         On-link      192.168.10.6    286
     192.168.10.7  255.255.255.255         On-link      192.168.10.6    286
    192.168.120.0    255.255.255.0         On-link      192.168.10.6     31
  192.168.120.255  255.255.255.255         On-link      192.168.10.6    286
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link      192.168.10.6    286
        224.0.0.0        240.0.0.0         On-link       192.168.2.3    281
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link      192.168.10.6    286
  255.255.255.255  255.255.255.255         On-link       192.168.2.3    281
===========================================================================
Persistent Routes:
  Network Address          Netmask  Gateway Address  Metric
    192.168.120.0    255.255.255.0     192.168.10.6       1
===========================================================================

```

I can't ping the VPN Server VPN-IP from PC behind VPN client but I notice a line will be added from server log if I run 
**"ping 192.168.10.1"**
```
Tue Aug 11 16:56:06 2009 testclient/124.13.127.111:55078 MULTI: Learn: 192.168.2.2 -> testclient/124.13.127.111:55078

```

As a summary :
1. Can't ping to VPN Server LAN-IP from VPN client. (Or vice versa)
2. Can't ping to VPN server VPN-IP from PC behind VPN client. (Or vice versa)

3. I have enable **below** on my Vista
```
HKEY_Local_Machine\System\CurrentControlSet\Services\Tcpip\Parameters\IPEnableRouter
```

4. I have run the command **below** on the PC behind VPN client
```
route -p add 192.168.10.0 mask 255.255.255.0 192.168.2.3
```


I can't go further on and can't really find any helpful resource on the internet. 

Has anyone from this forum successful setup something like this ? Any help will be appreciate and I plan to write everything from here and the solution (if found) into the blog as a contribution to everyone who is interested.

Thanks & regards,
Max.

---

