---
title: "OpenVPN works fine, but I can't filter traffic between users"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by b3rkl3y on 2011-05-13
Hello, 

I'm using ubuntu server 10.04 with openvpn installed on it. My vpn is working fine, all the users can connect without any issue.

My problem is that I'm unable to filter the VPN traffic using openvpn. I can't allow all users to be able to interact with other vpn users. I need to avoid this kind of traffic.

I was trying to build an iptables firewall, but I just noticed that my openvpn traffic isn't being filtered by iptables.

In FORWARD chain, no matter what rule I use openvpn would continue to allow traffic between my clients. It does appear that openvpn is skipping FORWARD chain?

For example:
```
# iptables -L FORWARD -nv
Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0        
```
Notice that there is 0 packets and 0 bytes in this chain?
Openvpn users can still contact each other :/
I know that if I disable client-to-client on openvpn config file, my users would not be able to contact each other. But some of then must be able to (thats why I need iptables).


Server config: 
```
port 1194
proto udp
dev tun
ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/server.crt
key /etc/openvpn/keys/server.key 
dh /etc/openvpn/keys/dh1024.pem
server 10.18.1.0 255.255.255.0
ifconfig-pool-persist ipp.txt
client-config-dir ccd
client-to-client
keepalive 10 120
comp-lzo
persist-key
persist-tun
status openvpn-status.log
verb 3

```

Thank you.

---

### Post by SeijiSensei on 2011-05-13
From "man openvpn":

[quote=OpenVPN man page]
--**client-to-client**
Because  the  OpenVPN  server mode handles multiple clients through a single tun or tap interface, it is effectively a router.  The --client-to-client flag  tells  OpenVPN  to internally  route  client-to-client  traffic rather than pushing all client-originating
 traffic to the TUN/TAP interface.

**When this option is used, each client will "see" the other clients which are  currently connected.   Otherwise, each client will only see the server.**  Don't use this option if you want to firewall tunnel traffic using custom, per-client rules.[/quote]

Sounds like you want to remove that directive from your configuration file.

---

### Post by b3rkl3y on 2011-05-13
> **SeijiSensei said:**
> From "man openvpn":



Sounds like you want to remove that directive from your configuration file.

SeijiSensei thanks, but i can't remove this directive from openvpn. I need to be able to have "some traffic" between clients, but I would need to filter this traffic with iptables on the server.


Thank you.

---

### Post by SeijiSensei on 2011-05-13
Then you probably need some INPUT iptables rules on the OpenVPN server that define which ports on which machines are visible from other addresses. Something like

```

iptables -A INPUT -p tcp -s 10.18.1.0/24 -d 10.18.1.0/24 --dport 80 -j ACCEPT
iptables -A INPUT -s 10.18.1.0/24 -d 10.18.1.0/24 -j REJECT
```

allows machines in the 10.18.1.0/24 subnet to connect with TCP to port 80 on any other machine in the subnet.  The next rule blocks all other traffic among machines in that subnet.  You might also need rules with specific IP addresses instead of subnets.

---

