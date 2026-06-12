---
title: "OpenVPN Behind a NAT?"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by icelander on 2011-06-12
I'm trying to set up an OpenVPN server on 11.04. I have it authenticating alright, but I get a weird error in my log:

```

new incoming connection would exceed maximum number of clients (10)

```

Considering I'm just setting up the server and I'm the only person connecting this is obviously incorrect.

I'm behind an Airport Extreme that's NATing the connection and is the DHCP server. Here's my network interface configuration:

```

## This is the network bridge declaration

## Start these interfaces on boot
auto lo br0

iface lo inet loopback

iface br0 inet static 
  address 192.168.1.100 
  netmask 255.255.255.0
  gateway 192.168.1.1
  bridge_ports eth0

iface eth0 inet manual
  up ip link set $IFACE up promisc on
  down ip link set $IFACE down promisc off

```

Here's my OpenVPN configuration:

```

mode server
tls-server

local 192.168.1.100 ## ip/hostname of server
port 1194 ## default openvpn port
proto udp

#bridging directive
dev tap0 ## If you need multiple tap devices, add them here
up "/etc/openvpn/up.sh br0 tap0 1500"
down "/etc/openvpn/down.sh br0 tap0"

persist-key
persist-tun

#certificates and encryption
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
tls-auth ta.key 0 # This file is secret

cipher BF-CBC        # Blowfish (default)
comp-lzo

#DHCP Information
ifconfig-pool-persist ipp.txt
server-bridge 192.168.1.100 255.255.255.0 192.168.1.200 192.168.1.210
max-clients 10 ## set this to the max number of clients that should be connected at a time

#log and security
user nobody
group nogroup
keepalive 10 120
status openvpn-status.log
verb 3

```

And here's the settings I'm using in Tunnelblick:

```

### Client configuration file for OpenVPN

# Specify that this is a client
client

# Bridge device setting
dev tap

# Host name and port for the server (default port is 1194)
# note: replace with the correct values your server set up
remote home.movetoiceland.com 11094

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
cert cubert.crt
key cubert.key

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

Can anybody see what I'm doing wrong?

---

