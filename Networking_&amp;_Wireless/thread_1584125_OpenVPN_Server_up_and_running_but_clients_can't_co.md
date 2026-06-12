---
title: "OpenVPN Server up and running but clients can't connect"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by Telémakhos on 2010-09-28
Hi guys,

I've been the las 4 days setting up my first VPN (OpenVPN bridged). The server is up and running OK but when I try to connect I've got this message in the client log.

> TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
TLS Error: TLS handshake failed


Can you take a quick look to my config files and tell me if you can see anything wrong?

**/etc/network/interfaces**
```

auto lo br0

iface lo inet loopback

iface br0 inet static
  address 10.9.8.13
  netmask 255.255.255.0
  gateway 10.9.8.1
  bridge_ports eth0

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down

```

[B]
/etc/openvpn/openvpn.conf[/B]
```
mode server
tls-server


#Host configuration

local 10.9.8.13
port 1194


#bridging directive

dev tap0
dev tap1 ## If you need multiple tap devices, add them here
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"

persist-key
persist-tun


#certificates and encryption
ca "/etc/openvpn/easy-rsa/keys/ca.crt"
cert "/etc/openvpn/easy-rsa/keys/server.crt"
key "/etc/openvpn/easy-rsa/keys/server.key"  # This file should be kept sec$
dh "/etc/openvpn/easy-rsa/keys/dh1024.pem"
tls-auth "/etc/openvpn/easy-rsa/keys/ta.key" 0 # This file is secret

cipher BF-CBC        # Blowfish (default)
comp-lzo


#DHCP Information

ifconfig-pool-persist ipp.txt
server-bridge 10.9.8.13 255.255.255.0 10.9.8.150 10.9.8.159
push "dhcp-option DNS 10.9.8.1"
push "dhcp-option DOMAIN mydomain.com"
max-clients 5 ## set this to the max number of clients that should be conne$


#log and security

user nobody
group nogroup
keepalive 10 120
status openvpn-status.log
verb 3

```

**Client.conf**
```
### Client configuration file for OpenVPN

client

# Bridge device setting
dev tap

# Host name and port for the server (default port is 1194)
remote my.wan.server.ip 1194

# Client does not need to bind to a specific local port
nobind

resolv-retry infinite

# Preserve state across restarts
persist-key
persist-tun

# SSL/TLS parameters
ca ca.crt
cert client.crt
key client.key

#tls-auth for server
tls-auth ta.key 1

# Specify same cipher as server
cipher BF-CBC

# Use compression
comp-lzo

# Log verbosity 
verb 3
```

The router is forwarding the port 1194 (UDP) to my ubuntu server (which has instaled OpenVPN Server) **10.9.8.13**

Anyone can help me? It's driving me crazy... :(

---

### Post by SeijiSensei on 2010-09-28
Try connecting from a client and look at the most recent files in /var/log on the server.  (You'll probably want to concentrate on /var/log/messages, /var/log/syslog and /var/log/daemon.log.)  What do you see?  If you don't get enough information, restart the server with "verb 9" in openvpn.conf.  You'll get more debugging information than any sane person would want.

Open *TCP* port 1194 as well.  I believe the initial handshake requires it; after that traffic is sent via UDP.

---

### Post by Telémakhos on 2010-09-28
Hi,

This is what I got:

**/var/log/messages**
> Sep 28 23:53:24 delfos kernel: [42174.289651] br0: port 2(tap1) entering disabled state
Sep 28 23:53:24 delfos kernel: [42174.321328] br0: port 2(tap1) entering disabled state
Sep 28 23:53:25 delfos kernel: [42175.370768] device tap0 entered promiscuous mode
Sep 28 23:53:25 delfos kernel: [42175.371397] br0: port 2(tap0) entering learning state
Sep 28 23:53:40 delfos kernel: [42190.363726] br0: port 2(tap0) entering forwarding state
Sep 28 23:54:26 delfos kernel: [42236.177450] Unknown ForwardIN=br0 OUT=br0 PHYSIN=eth0 PHYSOUT=tap0 SRC=10.9.8.1 DST=239.255.255.250 LEN=301 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=281 
Sep 28 23:54:26 delfos kernel: [42236.178223] Unknown ForwardIN=br0 OUT=br0 PHYSIN=eth0 PHYSOUT=tap0 SRC=10.9.8.1 DST=239.255.255.250 LEN=296 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=276 
Sep 28 23:54:26 delfos kernel: [42236.179179] Unknown ForwardIN=br0 OUT=br0 PHYSIN=eth0 PHYSOUT=tap0 SRC=10.9.8.1 DST=239.255.255.250 LEN=373 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=353 
Sep 28 23:54:26 delfos kernel: [42236.180258] Unknown ForwardIN=br0 OUT=br0 PHYSIN=eth0 PHYSOUT=tap0 SRC=10.9.8.1 DST=239.255.255.250 LEN=365 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=345 


**/var/log/syslog**
> Sep 29 01:33:56 delfos ovpn-openvpn[16090]: Authenticate/Decrypt packet error: packet HMAC authentication failed
Sep 29 01:33:56 delfos ovpn-openvpn[16090]: TLS Error: incoming packet authentication failed from [AF_INET]XX.XXX.69.42:59207
Sep 29 01:33:58 delfos ovpn-openvpn[16090]: Authenticate/Decrypt packet error: packet HMAC authentication failed
Sep 29 01:33:58 delfos ovpn-openvpn[16090]: TLS Error: incoming packet authentication failed from [AF_INET]XX.XXX.69.42:59207
Sep 29 01:34:02 delfos ovpn-openvpn[16090]: Authenticate/Decrypt packet error: packet HMAC authentication failed
Sep 29 01:34:02 delfos ovpn-openvpn[16090]: TLS Error: incoming packet authentication failed from [AF_INET]XX.XXX.69.42:59207
Sep 29 01:34:11 delfos ovpn-openvpn[16090]: Authenticate/Decrypt packet error: packet HMAC authentication failed
Sep 29 01:34:11 delfos ovpn-openvpn[16090]: TLS Error: incoming packet authentication failed from [AF_INET]XX.XXX.69.42:59207
Sep 29 01:34:27 delfos ovpn-openvpn[16090]: Authenticate/Decrypt packet error: packet HMAC authentication failed
Sep 29 01:34:27 delfos ovpn-openvpn[16090]: TLS Error: incoming packet authentication failed from [AF_INET]XX.XXX.69.42:59207
Sep 29 01:34:28 delfos kernel: [48237.006951] Unknown ForwardIN=br0 OUT=br0 PHYSIN=eth0 PHYSOUT=tap0 SRC=10.9.8.1 DST=239.255.255.250 LEN=301 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=281 

**/var/log/daemon.log**
> Sep 29 01:33:56 delfos ovpn-openvpn[16090]: Authenticate/Decrypt packet error: packet HMAC authentication failed
Sep 29 01:33:56 delfos ovpn-openvpn[16090]: TLS Error: incoming packet authentication failed from [AF_INET]XX.XXX.69.42:59207
Sep 29 01:33:58 delfos ovpn-openvpn[16090]: Authenticate/Decrypt packet error: packet HMAC authentication failed
Sep 29 01:33:58 delfos ovpn-openvpn[16090]: TLS Error: incoming packet authentication failed from [AF_INET]XX.XXX.69.42:59207
Sep 29 01:34:02 delfos ovpn-openvpn[16090]: Authenticate/Decrypt packet error: packet HMAC authentication failed
Sep 29 01:34:02 delfos ovpn-openvpn[16090]: TLS Error: incoming packet authentication failed from [AF_INET]XX.XXX.69.42:59207
Sep 29 01:34:11 delfos ovpn-openvpn[16090]: Authenticate/Decrypt packet error: packet HMAC authentication failed
Sep 29 01:34:11 delfos ovpn-openvpn[16090]: TLS Error: incoming packet authentication failed from [AF_INET]XX.XXX.69.42:59207
Sep 29 01:34:27 delfos ovpn-openvpn[16090]: Authenticate/Decrypt packet error: packet HMAC authentication failed
Sep 29 01:34:27 delfos ovpn-openvpn[16090]: TLS Error: incoming packet authentication failed from [AF_INET]XX.XXX.69.42:59207

Why is it saying "Unknow forward" in the messages log??? Apparently is failing the authentication... I'm going to try with verbosity 9 and check the output...

---

### Post by SeijiSensei on 2010-09-28
I'm actually more concerned about errors like this:

```
Sep 29 01:33:56 delfos ovpn-openvpn[16090]: Authenticate/Decrypt packet error: packet HMAC authentication failed
```

It sounds like your machines aren't negotiating the encryption key correctly.

Have you tried simple shared-key authentication?  That's a good place to start to make sure everything is set up correctly.  If you don't have many clients to support, it might be a lot easier than using certificates.  I run a number of point-to-point tunnels between my office and my clients' networks this way.  Here are some sample files I use:

Server (myopenvpn.example.com):
```

dev tun
ifconfig 192.168.110.1 192.168.110.2

#optional: runs /etc/openvpn/add_routes.sh when the connection is established]
#up ./add_routes.sh  

secret /etc/openvpn/mykey
port 9999
user nobody
group nogroup
comp-lzo
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3
```

Client
```

dev tun
remote myopenvpn.example.com
ifconfig 192.168.110.2 192.168.110.1

#up ./add_routes.sh

secret /etc/openvpn/mykey
port 9999
user nobody
group nogroup
comp-lzo
ping 15
ping-restart 45
ping-timer-rem
persist-tun
persist-key
verb 3
```

Basically, the two files are identical with the exception of the order of the IP addresses in the "ifconfig" directive, and the "remote" directive on the client.

You generate the key using the command "openvpn --genkey --secret /etc/openvpn/mykey", and copy it to both client and server.  

More help [here](http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html).

---

### Post by tOOmBa on 2011-01-17
I have the same issue, but I can't realise the thing with making up the key. I introduce that command or i should make a file with my key and indicate the path?
And do i need to config the VPN using the network manager?

I installed the openvpn server on my computer (Ubuntu OS 10.04).
when i type in the browser "http://myipaddress:943/admin" i see the openvpn interface, asking admin's username and password, so I've read a little of documentation which said that the username is "openvpn" & that i should do "passwd openvpn" (i didn't get what to do with this), and after that to use the "openvpn" username and my user's password to enter. Also i tried to find where's the config file for the server (just found the config.log). I need some little instructions to get done.

P.S. I hit for p2p vpn connection. 1st Ubuntu machine, 2nd XP machine. how to configure the Xp machine, i've read the link on the openvpn site, but i didn't get where to put the config files.

---

