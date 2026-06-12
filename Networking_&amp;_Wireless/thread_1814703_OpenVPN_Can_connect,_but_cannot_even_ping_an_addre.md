---
title: "OpenVPN: Can connect, but cannot even ping an address"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by R4KFFE on 2011-07-29
I have installed openvpn on an ubuntu 10.04 server. I run 11.04 on my desktop. It can connect to my VPN server. The problem is, I have ZERO internet access. I cannot even ping an IP address. If anyone can help me, it would be greatly appreciated!


**Here is my OpenVPN server config**

```


# Which local IP address should OpenVPN
# listen on? (optional)
;local a.b.c.d

# Which TCP/UDP port should OpenVPN listen on?
# If you want to run multiple OpenVPN instances
# on the same machine, use a different port
# number for each one.  You will need to
# open up this port on your firewall.
port 1194

# TCP or UDP server?
;proto tcp
proto udp

# "dev tun" will create a routed IP tunnel,
# "dev tap" will create an ethernet tunnel.
# Use "dev tap0" if you are ethernet bridging
# and have precreated a tap0 virtual interface
# and bridged it with your ethernet interface.
# If you want to control access policies
# over the VPN, you must create firewall
# rules for the the TUN/TAP interface.
# On non-Windows systems, you can give
# an explicit unit number, such as tun0.
# On Windows, use "dev-node" for this.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
;dev tap
dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel if you
# have more than one.  On XP SP2 or higher,
# you may need to selectively disable the
# Windows firewall for the TAP adapter.
# Non-Windows systems usually don't need this.
;dev-node MyTap

# SSL/TLS root certificate (ca), certificate
# (cert), and private key (key).  Each client
# and the server must have their own cert and
# key file.  The server and all clients will
# use the same ca file.
#
# See the "easy-rsa" directory for a series
# of scripts for generating RSA certificates
# and private keys.  Remember to use
# a unique Common Name for the server
# and each of the client certificates.
#
# Any X509 key management system can be used.
# OpenVPN can also use a PKCS #12 formatted key file
# (see "pkcs12" directive in man page).
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret

# Diffie hellman parameters.
# Generate your own with:
#   openssl dhparam -out dh1024.pem 1024
# Substitute 2048 for 1024 if you are using
# 2048 bit keys. 
dh dh1024.pem

# Configure server mode and supply a VPN subnet
# for OpenVPN to draw client addresses from.
# The server will take 10.8.0.1 for itself,
# the rest will be made available to clients.
# Each client will be able to reach the server
# on 10.8.0.1. Comment this line out if you are
# ethernet bridging. See the man page for more info.
server 10.8.0.0 255.255.255.0

# Maintain a record of client <-> virtual IP address
# associations in this file.  If OpenVPN goes down or
# is restarted, reconnecting clients can be assigned
# the same virtual IP address from the pool that was
# previously assigned.
ifconfig-pool-persist ipp.txt

# Configure server mode for ethernet bridging.
# You must first use your OS's bridging capability
# to bridge the TAP interface with the ethernet
# NIC interface.  Then you must manually set the
# IP/netmask on the bridge interface, here we
# assume 10.8.0.4/255.255.255.0.  Finally we
# must set aside an IP range in this subnet
# (start=10.8.0.50 end=10.8.0.100) to allocate
# to connecting clients.  Leave this line commented
# out unless you are ethernet bridging.
;server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100

# Configure server mode for ethernet bridging
# using a DHCP-proxy, where clients talk
# to the OpenVPN server-side DHCP server
# to receive their IP address allocation
# and DNS server addresses.  You must first use
# your OS's bridging capability to bridge the TAP
# interface with the ethernet NIC interface.
# Note: this mode only works on clients (such as
# Windows), where the client-side TAP adapter is
# bound to a DHCP client.
;server-bridge

# Push routes to the client to allow it
# to reach other private subnets behind
# the server.  Remember that these
# private subnets will also need
# to know to route the OpenVPN client
# address pool (10.8.0.0/255.255.255.0)
# back to the OpenVPN server.
;push "route 192.168.10.0 255.255.255.0"
;push "route 192.168.20.0 255.255.255.0"

# To assign specific IP addresses to specific
# clients or if a connecting client has a private
# subnet behind it that should also have VPN access,
# use the subdirectory "ccd" for client-specific
# configuration files (see man page for more info).

# EXAMPLE: Suppose the client
# having the certificate common name "Thelonious"
# also has a small subnet behind his connecting
# machine, such as 192.168.40.128/255.255.255.248.
# First, uncomment out these lines:
;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
# Then create a file ccd/Thelonious with this line:
#   iroute 192.168.40.128 255.255.255.248
# This will allow Thelonious' private subnet to
# access the VPN.  This example will only work
# if you are routing, not bridging, i.e. you are
# using "dev tun" and "server" directives.

# EXAMPLE: Suppose you want to give
# Thelonious a fixed VPN IP address of 10.9.0.1.
# First uncomment out these lines:
;client-config-dir ccd
;route 10.9.0.0 255.255.255.252
# Then add this line to ccd/Thelonious:
#   ifconfig-push 10.9.0.1 10.9.0.2

# Suppose that you want to enable different
# firewall access policies for different groups
# of clients.  There are two methods:
# (1) Run multiple OpenVPN daemons, one for each
#     group, and firewall the TUN/TAP interface
#     for each group/daemon appropriately.
# (2) (Advanced) Create a script to dynamically
#     modify the firewall in response to access
#     from different clients.  See man
#     page for more info on learn-address script.
;learn-address ./script

# If enabled, this directive will configure
# all clients to redirect their default
# network gateway through the VPN, causing
# all IP traffic such as web browsing and
# and DNS lookups to go through the VPN
# (The OpenVPN server machine may need to NAT
# or bridge the TUN/TAP interface to the internet
# in order for this to work properly).
push "redirect-gateway def1 bypass-dhcp"

# Certain Windows-specific network settings
# can be pushed to clients, such as DNS
# or WINS server addresses.  CAVEAT:
# http://openvpn.net/faq.html#dhcpcaveats
# The addresses below refer to the public
# DNS servers provided by opendns.com.
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"

# Uncomment this directive to allow different
# clients to be able to "see" each other.
# By default, clients will only see the server.
# To force clients to only see the server, you
# will also need to appropriately firewall the
# server's TUN/TAP interface.
;client-to-client

# Uncomment this directive if multiple clients
# might connect with the same certificate/key
# files or common names.  This is recommended
# only for testing purposes.  For production use,
# each client should have its own certificate/key
# pair.
#
# IF YOU HAVE NOT GENERATED INDIVIDUAL
# CERTIFICATE/KEY PAIRS FOR EACH CLIENT,
# EACH HAVING ITS OWN UNIQUE "COMMON NAME",
# UNCOMMENT THIS LINE OUT.
;duplicate-cn

# The keepalive directive causes ping-like
# messages to be sent back and forth over
# the link so that each side knows when
# the other side has gone down.
# Ping every 10 seconds, assume that remote
# peer is down if no ping received during
# a 120 second time period.
keepalive 10 120

# For extra security beyond that provided
# by SSL/TLS, create an "HMAC firewall"
# to help block DoS attacks and UDP port flooding.
#
# Generate with:
#   openvpn --genkey --secret ta.key
#
# The server and each client must have
# a copy of this key.
# The second parameter should be '0'
# on the server and '1' on the clients.
tls-auth ta.key 0 # This file is secret

# Select a cryptographic cipher.
# This config item must be copied to
# the client config file as well.
cipher BF-CBC        # Blowfish (default)
;cipher AES-128-CBC   # AES
;cipher DES-EDE3-CBC  # Triple-DES

# Enable compression on the VPN link.
# If you enable it here, you must also
# enable it in the client config file.
#comp-lzo

# The maximum number of concurrently connected
# clients we want to allow.
max-clients 100

# It's a good idea to reduce the OpenVPN
# daemon's privileges after initialization.
#
# You can uncomment this out on
# non-Windows systems.
user nobody
group nogroup

# The persist options will try to avoid
# accessing certain resources on restart
# that may no longer be accessible because
# of the privilege downgrade.
persist-key
persist-tun

# Output a short status file showing
# current connections, truncated
# and rewritten every minute.
status openvpn-status.log

# By default, log messages will go to the syslog (or
# on Windows, if running as a service, they will go to
# the "\Program Files\OpenVPN\log" directory).
# Use log or log-append to override this default.
# "log" will truncate the log file on OpenVPN startup,
# while "log-append" will append to it.  Use one
# or the other (but not both).
;log         openvpn.log
log-append  openvpn.log

# Set the appropriate level of log
# file verbosity.
#
# 0 is silent, except for fatal errors
# 4 is reasonable for general usage
# 5 and 6 can help to debug connection problems
# 9 is extremely verbose
verb 3

# Silence repeating messages.  At most 20
# sequential messages of the same message
# category will be output to the log.
;mute 20

```

**Here is my firewall output for BOTH client and server**

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


**Here is my route information when NOT connected to VPN**

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0

```

**Here is my route information when connected to VPN** (btw, it takes several minutes for the route command to run when connected to the VPN)

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.8.0.5        0.0.0.0         UG    0      0        0 tun0
10.8.0.1        10.8.0.5        255.255.255.255 UGH   0      0        0 tun0
10.8.0.5        *               255.255.255.255 UH    0      0        0 tun0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0

```


**NOTE:** When I ping 10.8.0.5, nothing happens! What does that mean?


**Here is my ifconfig on my client**


```
eth0      Link encap:Ethernet  HWaddr 57:42:50:88:4d:ab 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:137336 (137.3 KB)  TX bytes:137336 (137.3 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.6  P-t-P:10.8.0.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:36425 (36.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:215:15:70:33:6b  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:15ff:fe70:726c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38779 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5837132 (5.8 MB)  TX bytes:6512007 (6.5 MB)

wmx0      Link encap:Ethernet  HWaddr 65:d4:db:19:d3:d5  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by R4KFFE on 2011-07-30
**Here is my openvpn log**

```
Sat Jul 30 11:16:57 2011 OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Sat Jul 30 11:16:57 2011 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Sat Jul 30 11:16:57 2011 Diffie-Hellman initialized with 1024 bit key
Sat Jul 30 11:16:57 2011 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Sat Jul 30 11:16:57 2011 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Sat Jul 30 11:16:57 2011 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Sat Jul 30 11:16:57 2011 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Sat Jul 30 11:16:57 2011 TLS-Auth MTU parms [ L:1541 D:166 EF:66 EB:0 ET:0 EL:0 ]
Sat Jul 30 11:16:57 2011 ROUTE: default_gateway=UNDEF
Sat Jul 30 11:16:57 2011 TUN/TAP device tun0 opened
Sat Jul 30 11:16:57 2011 TUN/TAP TX queue length set to 100
Sat Jul 30 11:16:57 2011 /sbin/ifconfig tun0 10.8.0.1 pointopoint 10.8.0.2 mtu 1500
Sat Jul 30 11:16:57 2011 /sbin/route add -net 10.8.0.0 netmask 255.255.255.0 gw 10.8.0.2
Sat Jul 30 11:16:57 2011 Data Channel MTU parms [ L:1541 D:1450 EF:41 EB:4 ET:0 EL:0 ]
Sat Jul 30 11:16:57 2011 GID set to nogroup
Sat Jul 30 11:16:57 2011 UID set to nobody
Sat Jul 30 11:16:57 2011 Socket Buffers: R=[137216->131072] S=[137216->131072]
Sat Jul 30 11:16:57 2011 UDPv4 link local (bound): [undef]
Sat Jul 30 11:16:57 2011 UDPv4 link remote: [undef]
Sat Jul 30 11:16:57 2011 MULTI: multi_init called, r=256 v=256
Sat Jul 30 11:16:57 2011 IFCONFIG POOL: base=10.8.0.4 size=62
Sat Jul 30 11:16:57 2011 IFCONFIG POOL LIST
Sat Jul 30 11:16:57 2011 jsmith-laptop,10.8.0.4
Sat Jul 30 11:16:57 2011 Initialization Sequence Completed
Sat Jul 30 11:17:27 2011 MULTI: multi_create_instance called
Sat Jul 30 11:17:27 2011 201.131.164.22:11337 Re-using SSL/TLS context
Sat Jul 30 11:17:27 2011 201.131.164.22:11337 Control Channel MTU parms [ L:1541 D:166 EF:66 EB:0 ET:0 EL:0 ]
Sat Jul 30 11:17:27 2011 201.131.164.22:11337 Data Channel MTU parms [ L:1541 D:1450 EF:41 EB:4 ET:0 EL:0 ]
Sat Jul 30 11:17:27 2011 201.131.164.22:11337 Local Options hash (VER=V4): 'a2e2498c'
Sat Jul 30 11:17:27 2011 201.131.164.22:11337 Expected Remote Options hash (VER=V4): '70f5b3af'
Sat Jul 30 11:17:27 2011 201.131.164.22:11337 TLS: Initial packet from [AF_INET]201.131.164.22:11337, sid=fb6c421a 095944ea
Sat Jul 30 11:17:33 2011 201.131.164.22:11337 VERIFY OK: depth=1, /C=US/ST=CA/L=SanFrancisco/O=Fort-Funston/CN=Fort-Funston_CA/emailAddress=me@myhost.mydomain
Sat Jul 30 11:17:33 2011 201.131.164.22:11337 VERIFY OK: depth=0, /C=US/ST=CA/L=SanFrancisco/O=Fort-Funston/CN=jsmith-laptop/emailAddress=me@myhost.mydomain
Sat Jul 30 11:17:34 2011 201.131.164.22:11337 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sat Jul 30 11:17:34 2011 201.131.164.22:11337 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sat Jul 30 11:17:34 2011 201.131.164.22:11337 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sat Jul 30 11:17:34 2011 201.131.164.22:11337 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sat Jul 30 11:17:35 2011 201.131.164.22:11337 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Sat Jul 30 11:17:35 2011 201.131.164.22:11337 [jsmith-laptop] Peer Connection Initiated with [AF_INET]201.131.164.22:11337
Sat Jul 30 11:17:35 2011 jsmith-laptop/201.131.164.22:11337 MULTI: Learn: 10.8.0.6 -> jsmith-laptop/201.131.164.22:11337
Sat Jul 30 11:17:35 2011 jsmith-laptop/201.131.164.22:11337 MULTI: primary virtual IP for jsmith-laptop/201.131.164.22:11337: 10.8.0.6
Sat Jul 30 11:17:37 2011 jsmith-laptop/201.131.164.22:11337 PUSH: Received control message: 'PUSH_REQUEST'
Sat Jul 30 11:17:37 2011 jsmith-laptop/201.131.164.22:11337 SENT CONTROL [jsmith-laptop]: 'PUSH_REPLY,redirect-gateway def1 bypass-dhcp,dhcp-option DNS 8.8.8.8,dhcp-option DNS 8.8.4.4,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.8.0.6 10.8.0.5' (status=1)
Sat Jul 30 11:18:17 2011 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Sat Jul 30 11:18:27 2011 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
```

---

### Post by R4KFFE on 2011-08-03
Does anyone have an idea? I have read so many threads and tried everything and it does not seem to work.

---

### Post by R4KFFE on 2011-08-04
I am still trying to troubleshoot this. I have tried every variation of udp/ tcp, compression, no compressions, etc. No matter what, I can connect to the VPN, but I have no access to the internet. I cannot even ping a IP address.


Does anyone have any insights?

---

### Post by jaykubun on 2011-08-07
It seems that upon setup of the openVPN connection your default gateway is switched. I guess you don't want that to happen. There should be somewhere an option where you can prevent the openVPN client of changing the default gateway. 

(I use KVpnc and there is an option under network to keep the default route)

---

### Post by SeijiSensei on 2011-08-07
```
Sat Jul 30 11:18:17 2011 read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
```

The server appears to be rejecting the UDP packets that create your tunnel.  Perhaps there's a firewalling rule in the way?  Perhaps you're not using the same UDP port as the server? 

If you can't ping the tunnel address at other end of the VPN connection, you don't have a connection.

---

