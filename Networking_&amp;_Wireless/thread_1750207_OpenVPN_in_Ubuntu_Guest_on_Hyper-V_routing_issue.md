---
title: "OpenVPN in Ubuntu Guest on Hyper-V routing issue"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by mindlessZA on 2011-05-05
Windows 2008 R2 64Bit running Hyper-V with IP 192.168.3.2, default gateway is 192.168.3.1.

Guest Ubuntu 10.04 64Bit running OpenVPN in bridge mode on IP 192.168.3.3, default gateway is 192.168.3.1

OpenVPN issues IPs between 192.168.3.50 and 192.168.3.59 and is running in bridge mode using tap0 and eth0 to create br0.

The setup was working perfectly as a VirtualBox VM on the same server, so I created a Hyper-V guest and scp'ed the whole setup into it after booting with a Gentoo LiveCD.

Issue:
When connecting to the VPN, everything looks fine, but I can only access 192.168.3.3, everything else on the network is not accessible. I.e. I can ping 192.168.3.3 but not 192.168.3.1. Clients are Windows 7 64bit and Mac OSX

I have setup OpenVPN on Gentoo on a different Win 2008 Hyper-V server which works without any issue, but when I try Gentoo on the current server, the symptoms are the same. 

This would indicate either the network adapter inside the Guest OS or some setting on the Host OS.

I am using the Legacy adapter in all instances.

Any ideas?

OpenVPN server config:
```

local 192.168.3.3
dev tap0
port 1194
proto udp
ca privnet/ca.crt
cert privnet/server.crt
key privnet/server.key
dh privnet/dh1024.pem

mode server
server-bridge 192.168.3.3 255.255.248.0 192.168.3.50 192.168.3.69
ifconfig-pool-persist ipp.txt
status /tmp/openvpn.status
push "route 192.168.3.0 255.255.248.0"
push "dhcp-option DNS 192.168.3.2"

keepalive 10 120
comp-lzo
user nobody
group nobody
persist-key
persist-tun
status openvpn-status.log
verb 3
cipher AES-256-CBC


```

client config:
```

client
dev tap
proto udp
remote vpn.example.com 1194
ca ca.crt
cert client.crt
key client.key
resolv-retry infinite
nobind
persist-tun
persist-key
verb 3
comp-lzo
ns-cert-type server
cipher AES-256-CBC

```

Server Routes:
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
0.0.0.0         192.168.3.1     0.0.0.0         UG    0      0        0 br0

```

Client Routes:
```

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
      192.168.0.0    255.255.248.0         On-link      192.168.3.50    286
      192.168.0.0    255.255.248.0      192.168.2.1     192.168.3.50     31
     192.168.3.50  255.255.255.255         On-link      192.168.3.50    286

```

---

