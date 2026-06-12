---
title: "VPN Subnet Routing Help Required"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by gavinlew on 2012-05-18
Hi All,

For a while I have had a basic P2P VPN working where I can access a linux machine on my home network and that can access a desktop in the office.

What I would now like to-do is to be able to access all machines on the home network from the office.

I have tried all sorts of combinations of iroute and route commands but cannot get the routing configuration to work.

My network is designed as follows ;


                                                            VPS (IPForwarding Enabled)
                                               OpenVPN Server - 87.117.XXX.XX
                                                 OpenVPN 10.9.8.0/24
                              /                                                              \
                             /                                                                \
                            /                                                                  \

                  Office                                                                   Home
                212.11.XX.XX/24                                                 192.168.0.0/24

Should I be able to push the routing for 192.168.0.0/24 via 87.117.XXX.XX (using the tunnel)?

So far my server.conf is defined as ;

local 87.117.XXX.XX
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh1024.pem

server 10.9.8.0 255.255.255.0
ifconfig-pool-persist ipp.txt
client-to-client

client-config-dir ccd

push "route 192.168.0.0 255.255.255.0"
route 212.11.XX.XXX 255.255.255.240 10.9.8.6

push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"

keepalive 10 30
comp-lzo
# maxclients 20
user nobody
group nobody
persist-key
persist-tun
status openvpn-status.log
verb 3
mute 10

In /ccd I have

newark (office VPN) iroute 192.168.0.0 255.255.255.0
173kfrouter (home VPN) iroute 192.168.0.0 255.255.255.0

This doesn't look right.

Any ideas :)

Cheers

---

