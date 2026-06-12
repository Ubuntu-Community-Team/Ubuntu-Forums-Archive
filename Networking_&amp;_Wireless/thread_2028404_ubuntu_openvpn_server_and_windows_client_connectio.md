---
title: "ubuntu openvpn server and windows client connection"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by szabobar on 2012-07-18
Hi all,

I am newbie in openvpn world, I would be happy if anybody can help me.

My Network:
_Internet_ <---->_Router_(with port forwarding)<--->_VPN Server_(ubuntu)
**IP addresses:**
_Router _: 
[list]internet ip: 188.142.227.221[/list]
[list]lan ip: 192.168.0.249[/list]
_VPN server_:
[list]lan ip: 192.168.0.116[/list]

I was installed openvpn server from apt.
Installation steps:
[list]1) copy easy-rsa files from /usr/share/doc/openvpn/examples/easy_rsa/2.0/* to /etc/openvpn/easy_rsa[/list]
[list]2) edit in /etc/openvpn/easy_rsa/vars file the export KEY_* veriables[/list]
[list]3) source vars && clean-all && build-ca && build.dh commands run[/list]
4) Create server.conf:
```
local 192.168.0.116
port 1194
proto udp
dev tap0
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
ifconfig-pool-persist ipp.txt
server-bridge 192.168.0.116 255.255.255.0 192.168.0.220 192.168.0.230
push "route 192.168.0.249 255.255.255.0"
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 192.168.0.100"
push "dhcp-option DNS 192.168.0.82"
keepalive 10 120
tls-auth ta.key 0 # This file is secret
comp-lzo
max-clients 10
user nobody
group nogroup
persist-key
persist-tun
status /var/log/openvpn/openvpn-status.log
log         /var/log/openvpn/openvpn.log
verb 4
```

/etc/network/interfaces
```
auto lo br0

iface lo inet loopback

iface br0 inet static
  address 192.168.0.116
  netmask 255.255.255.0
  gateway 192.168.0.249
  bridge_ports eth0

iface eth0 inet manual
  up ip link set $IFACE up promisc on
  down ip link set $IFACE down promisc off

```

In vpn server I have not got routing (iptables).
[list]4) /etc/init.d/openvpn start -> openvpn start successfully[/list]

I was generated a client certification, and add it to client computer.
I have got a windows xp client computer in somewhere the internet with this config:
client.config in windows xp
```

client
dev tap
remote 188.142.227.221 1194
nobind
resolv-retry infinite
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
tls-auth ta.key 1
cipher BF-CBC
comp-lzo
verb 3

```

The connection from the client winXP is success to the vpn server, but I can not reach the lan.
In client side after the connection I got 2 network adapters. 1. is the original, and the 2. adapter got the lan ip address (192.168.0.220)
If I would like to ping some lan ip, the networks was unreachable.
The other bad news is in winXP client in the vpn ip connection there is no default gateway, but the other wan gateway got it.
Here is the client ipconfig command result
```

Ethernet-adapter Local connection 4:

        IP-address. . . . . . . . . . . . . . . . : 192.168.0.220
        subnet mask. . . . . . . . ........ . . : 255.255.255.0
        default gateway. . . . . . . . :

Ethernet-adapter Local Connection:

        IP-address. . . . . . . . . . . . . . . . : 192.168.43.41
        subnet mask. . . . . ...... . . . . . : 255.255.255.0
        default gateway........ . . . . . . . : 192.168.43.1

```


Can anybody help me how can I reash the lan in winXP client?

Thanks a lot.

---

