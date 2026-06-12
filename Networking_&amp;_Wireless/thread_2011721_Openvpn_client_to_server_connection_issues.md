---
title: "Openvpn client to server connection issues"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by amngco on 2012-06-27
I've been hitting my head against the wall for about three days now trying to get a VPN setup between 2 Ubuntu servers. I'm a complete noob when it comes to VPN setup so I'm not entirely sure where things are wrong or what to do about them. 

I have my server.conf file which is a self generated file that I tweaked as I needed, but I dson't know if that's enough. Feel free to edit it if need be.
Code:
```
#################################################
# Sample OpenVPN 2.0 config file for            #
# multi-client server.                          #
#                                               #
# This file is for the server side              #
# of a many-clients <-> one-server              #
# OpenVPN configuration.                        #
#                                               #
# OpenVPN also supports                         #
# single-machine <-> single-machine             #
# configurations (See the Examples page         #
# on the web site for more info).               #
#                                               #
# This config should work on Windows            #
# or Linux/BSD systems.  Remember on            #
# Windows to quote pathnames and use            #
# double backslashes, e.g.:                     #
# "C:\\Program Files\\OpenVPN\\config\\foo.key" #
#                                               #
# Comments are preceded with '#' or ';'         #
#################################################

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
dev tap
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"

;dev tun

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
#server 10.8.0.0 255.255.255.0

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
server-bridge 192.168.200.199 255.255.255.0 192.168.200.200 192.168.200.250

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
;push "redirect-gateway def1 bypass-dhcp"

# Certain Windows-specific network settings
# can be pushed to clients, such as DNS
# or WINS server addresses.  CAVEAT:
# http://openvpn.net/faq.html#dhcpcaveats
# The addresses below refer to the public
# DNS servers provided by opendns.com.
;push "dhcp-option DNS 208.67.222.222"
;push "dhcp-option DNS 208.67.220.220"

# Uncomment this directive to allow different
# clients to be able to "see" each other.
# By default, clients will only see the server.
# To force clients to only see the server, you
# will also need to appropriately firewall the
# server's TUN/TAP interface.
client-to-client

# Uncomment this directive if multiple clients
# might connect with the same certificate/key
# files or common names.  This is recommended
# only for testing purposes.  For production use,
# each client should have its own certificate/key
# pair.
#
# IF YOU HAVE NOT GENERATED /etc/openvpn/server.confINDIVIDUAL
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
;tls-auth ta.key 0 # This file is secret

# Select a cryptographic cipher.
# This config item must be copied to
# the client config file as well.
cipher BF-CBC        # Blowfish (default)
;cipher AES-128-CBC   # AES
;cipher DES-EDE3-CBC  # Triple-DES

# Enable compression on the VPN link.
# If you enable it here, you must also
# enable it in the client config file.
comp-lzo

# The maximum number of concurrently connected
# clients we want to allow.
max-clients 100

# It's a good idea to reduce the OpenVPN
# daemon's privileges after initialization.
#
# You can uncomment this out on
# non-Windows systems.
;user nobody
;group nogroup

# The persist options will try to avoid
# accessing certain resources on restart
# that may no longer be accessible because
# of the privilege downgrade.
;persist-key
;persist-tun

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
;log-append  openvpn.log

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

script-security 3 system
status statuslog 5
status-version 2

```

I also have my client.conf from the client this one pulled and tweaked from another online tutorial.

code
```
### Client configuration file for OpenVPN

# Specify that this is a client
client

# Bridge device setting
dev tap

# Host name and port for the server (default port is 1194)
# note: replace with the correct values your server set up
remote 10.8.0.100 1194

# Client does not need to bind to a specific local port
nobind

# Keep trying to resolve the host name of OpenVPN server.
## The windows GUI seems to dislike the following rule. 
##You may need to comment it out.
resolv-retry infinite

# Preserve state across restarts
persist-key
persist-tun

# SSL/TLS parameters - files created previously
ca ca.crt
cert client1.crt
key client1.key

# Since we specified the tls-auth for server, we need it for the client
# note: 0 = server, 1 = client
tls-auth ta.key 1

# Specify same cipher as server
cipher BF-CBC

# Use compression
comp-lzo

# Log verbosity (to help if there are problems)
verb 3

```

Now using I'm using gopenvpn on the client, I don't know if that's an issue or not but I don't think so. 
The log output from the gopenvpn client is:

```
Wed Jun 27 16:03:14 2012: MANAGEMENT: CMD 'state on' 
Wed Jun 27 16:03:14 2012: MANAGEMENT: CMD 'auth-retry interact' 
Wed Jun 27 16:03:14 2012: MANAGEMENT: CMD 'hold release' 
Wed Jun 27 16:03:14 2012: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info. 
Wed Jun 27 16:03:14 2012: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts 
Wed Jun 27 16:03:14 2012: WARNING: file 'client1.key' is group or others accessible 
Wed Jun 27 16:03:14 2012: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted> 
Wed Jun 27 16:03:14 2012: WARNING: file 'ta.key' is group or others accessible 
Wed Jun 27 16:03:14 2012: Control Channel Authentication: using 'ta.key' as a OpenVPN static key file 
Wed Jun 27 16:03:14 2012: Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication 
Wed Jun 27 16:03:14 2012: Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication 
Wed Jun 27 16:03:14 2012: LZO compression initialized 
Wed Jun 27 16:03:14 2012: Control Channel MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ] 
Wed Jun 27 16:03:14 2012: Socket Buffers: R=[126976->131072] S=[126976->131072] 
Wed Jun 27 16:03:14 2012: Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ] 
Wed Jun 27 16:03:14 2012: Local Options hash (VER=V4): '13a273ba' 
Wed Jun 27 16:03:14 2012: Expected Remote Options hash (VER=V4): '360696c5' 
Wed Jun 27 16:03:14 2012: UDPv4 link local: [undef] 
Wed Jun 27 16:03:14 2012: UDPv4 link remote: [AF_INET]10.8.0.100:1194 
Wed Jun 27 16:03:14 2012: MANAGEMENT: >STATE:1340830994,WAIT,,, 
Wed Jun 27 16:04:14 2012: TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity) 
Wed Jun 27 16:04:14 2012: TLS Error: TLS handshake failed 
Wed Jun 27 16:04:14 2012: TCP/UDP: Closing socket 
Wed Jun 27 16:04:14 2012: SIGUSR1[soft,tls-error] received, process restarting 
Wed Jun 27 16:04:14 2012: MANAGEMENT: >STATE:1340831054,RECONNECTING,tls-error,, 
Wed Jun 27 16:04:14 2012: MANAGEMENT: CMD 'hold release' 
Wed Jun 27 16:04:14 2012: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info. 
Wed Jun 27 16:04:14 2012: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts 
Wed Jun 27 16:04:14 2012: Re-using SSL/TLS context 
Wed Jun 27 16:04:14 2012: LZO compression initialized 
Wed Jun 27 16:04:14 2012: Control Channel MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ] 
Wed Jun 27 16:04:14 2012: Socket Buffers: R=[126976->131072] S=[126976->131072] 
Wed Jun 27 16:04:14 2012: Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ] 
Wed Jun 27 16:04:14 2012: Local Options hash (VER=V4): '13a273ba' 
Wed Jun 27 16:04:14 2012: Expected Remote Options hash (VER=V4): '360696c5' 
Wed Jun 27 16:04:14 2012: UDPv4 link local: [undef] 
Wed Jun 27 16:04:14 2012: UDPv4 link remote: [AF_INET]10.8.0.100:1194 
Wed Jun 27 16:04:14 2012: MANAGEMENT: >STATE:1340831054,WAIT,,, 
Wed Jun 27 16:05:14 2012: TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity) 
Wed Jun 27 16:05:14 2012: TLS Error: TLS handshake failed 
Wed Jun 27 16:05:14 2012: TCP/UDP: Closing socket 
Wed Jun 27 16:05:14 2012: SIGUSR1[soft,tls-error] received, process restarting 
Wed Jun 27 16:05:14 2012: MANAGEMENT: >STATE:1340831114,RECONNECTING,tls-error,, 
Wed Jun 27 16:05:14 2012: MANAGEMENT: CMD 'hold release' 
Wed Jun 27 16:05:14 2012: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info. 
Wed Jun 27 16:05:14 2012: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts 
Wed Jun 27 16:05:14 2012: Re-using SSL/TLS context 
Wed Jun 27 16:05:14 2012: LZO compression initialized 
Wed Jun 27 16:05:14 2012: Control Channel MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ] 
Wed Jun 27 16:05:14 2012: Socket Buffers: R=[126976->131072] S=[126976->131072] 
Wed Jun 27 16:05:14 2012: Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ] 
Wed Jun 27 16:05:14 2012: Local Options hash (VER=V4): '13a273ba' 
Wed Jun 27 16:05:14 2012: Expected Remote Options hash (VER=V4): '360696c5' 
Wed Jun 27 16:05:14 2012: UDPv4 link local: [undef] 
Wed Jun 27 16:05:14 2012: UDPv4 link remote: [AF_INET]10.8.0.100:1194 
Wed Jun 27 16:05:14 2012: MANAGEMENT: >STATE:1340831114,WAIT,,, 
Wed Jun 27 16:06:14 2012: TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity) 
Wed Jun 27 16:06:14 2012: TLS Error: TLS handshake failed 
Wed Jun 27 16:06:14 2012: TCP/UDP: Closing socket 
Wed Jun 27 16:06:14 2012: SIGUSR1[soft,tls-error] received, process restarting 
Wed Jun 27 16:06:14 2012: MANAGEMENT: >STATE:1340831174,RECONNECTING,tls-error,, 
Wed Jun 27 16:06:14 2012: MANAGEMENT: CMD 'hold release' 
Wed Jun 27 16:06:14 2012: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info. 
Wed Jun 27 16:06:14 2012: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts 
Wed Jun 27 16:06:14 2012: Re-using SSL/TLS context 
Wed Jun 27 16:06:14 2012: LZO compression initialized 
Wed Jun 27 16:06:14 2012: Control Channel MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ] 
Wed Jun 27 16:06:14 2012: Socket Buffers: R=[126976->131072] S=[126976->131072] 
Wed Jun 27 16:06:14 2012: Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ] 
Wed Jun 27 16:06:14 2012: Local Options hash (VER=V4): '13a273ba' 
Wed Jun 27 16:06:14 2012: Expected Remote Options hash (VER=V4): '360696c5' 
Wed Jun 27 16:06:14 2012: UDPv4 link local: [undef] 
Wed Jun 27 16:06:14 2012: UDPv4 link remote: [AF_INET]10.8.0.100:1194 
Wed Jun 27 16:06:14 2012: MANAGEMENT: >STATE:1340831174,WAIT,,,
```

Now some other things that I'm not sure about is whether or not to bridge the connection on the client like I did on the server. I doubt that's necessary but still....

Any help would be good and preferably command line as this server will be on a different site tomorrow, and the only interface I can use will be to SSH into it. 

Thanks.

---

### Post by amngco on 2012-07-13
bump

---

### Post by Kirk Schnable on 2012-07-15
I think I made this slip-up once too. If I remember correctly, that error about your key files being "works or others accessible" is a problem. 

 In your keys folder:

```
chmod 700 ta.key
chmod 700 client1.key
chmod 700 client1.crt
chmod 700 ca.crt
```

But the reason your TLS handshake is failing is ta.key isn't being used on the server. 

Uncomment this in your server.conf:
```
tls-auth ta.key 0
```

Make sure you restart the server and client daemons. 

Let me know how it goes!

Kirk

---

### Post by amngco on 2012-07-16
Well first thanks for the help, I was getting more than a little desperate. 

Now the server is firing up fine, but one of my client certificates doesn't appear to load.

```
Mon Jul 16 09:26:29 2012 OpenVPN 2.2.1 i486-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Mar 23 2012
Mon Jul 16 09:26:29 2012 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Mon Jul 16 09:26:29 2012 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Mon Jul 16 09:26:29 2012 Cannot load certificate file client1.crt: error:02001002:system library:fopen:No such file or directory: error:20074002:BIO routines:FILE_CTRL:system lib: error:140AD002:SSL routines:SSL_CTX_use_certificate_file:system lib
Mon Jul 16 09:26:29 2012 Exiting
```Says it can't load, and something about no such file or directory.

The certificate is in the client.conf directory, do I need to make a keys folder and move it there?

Oh I fixed the server verification part of the error notification

---

### Post by amngco on 2012-07-16
Ok problem resolved. I decided to try and run openvpn as root instead of sudo. the server and the client are authenticating to each other, and the logs show a connection has taken place. Thanks for the help Kirk.

---

