---
title: "Can't connect to server running bridged OpenVPN over the vpn"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by Zyprexa on 2009-11-21
I'm having some problems configuring my openvpn server.

the bridge OpenVPN server seems to run fine, and i can connect client to it over LAN (i have not had the chance to test it from the outside yet). I am assigned the correct IP and everything looks ok. But i can't ping the server from the client nor from server to client, over the vpn. And i can not connect to the Ventrilo server also running on the Ubuntu server, over the vpn. I can however connect to the ventrilo server using LAN or Hamachi ip. (Hamachi is starting to blow, the reason i want to replace it with openvpn)

The vpn is mainly intented to be used for LAN gaming over internet, which is why i chose bridge mode (**google told me so**).

OpenVPN server is running on Ubuntu Server, the client is running on Vista.
Ubuntu Server has ip 192.168.0.10 on the lan
Client has ip 192.168.0.3 on the lan

this is the server.conf:
> local 192.168.0.10
port 11194
proto udp
dev tap0

ca <path to file>
cert <path to file>
key <path to file>

dh <path to file>

server-bridge 10.10.0.1 255.255.255.0 10.10.0.10 10.10.0.100

ifconfig-pool-persist ipp.txt

client-to-client
keepalive 10 120

comp-lzo

max-clients 20

persist-key
persist-tun

status openvpn-status.log

log openvpn.log

verb 3This is the client config:> client
dev tap
proto udp
remote 192.168.0.10 11194
resolv-retry infinite
nobind
persist-key
persist-tun

;mute-replay-warnings

ca <path to file>
cert <path to file>
key <path to file>

comp-lzo

verb 3Let me know what other info you need if you can help me.

---

