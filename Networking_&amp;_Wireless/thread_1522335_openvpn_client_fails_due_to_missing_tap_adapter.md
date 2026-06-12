---
title: "openvpn client fails due to missing tap adapter?"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by fackelein on 2010-07-02
Hey, I'm a newbie of Openvpn.
I get to establish a VPN between my host(ubuntu 10.04) and my VM(also lucid) in virtualbox these days. I've already read HOWTO, tutorial, FAQ in openvpn offical site and searched many threads in this site, unfortunately problem lasts not solving...

My issue is I've completed the configuration of my host as a server in bridge type and the openvpn service is on, I can see the tap0 device.
On the other side, the configuration of client in virtual box is also done, BUT I CANNOT SEE THE TAP ADAPTER through ifconfig. How can I make the client connected to the sever...? I've tried to append similar script up.sh and down.sh with that in sever.conf after "dev tap" in client.conf, but it doesn't work. Could you help to diagnose it or share your experience, thx in advance;)
BTW,the vm network is configured as bridge type.
The client.conf is as follows,

client.conf:
client
dev tap
proto udp
remote 192.168.a.b 1194
resolve-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
ns-cert-type server
tls-auth ta.key 1
comp-lzo
verb 3

---

