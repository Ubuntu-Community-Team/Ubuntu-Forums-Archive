---
title: "StrongVPN openvpn. Command line works, network-manager doesn't..."
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by Taijitu on 2010-06-02
Hello everyone.

I have recently subscribed to an openvpn account at StrongVPN, and they have then supplied me with the proper certificates, keys etc.

It works quite flawlessly with the following command:

sudo openvpn --config ovpnXXX.ovpn

But if I use network-manager and import the ovpn config file, the vpn-connection times out...

The config file looks like this:
```

remote xxx.xxx.xxx.xxx xxxx
proto udp
ca ca.crt
cert ovpnXXX.crt
key ovpnXXX.key
tls-auth ta.key 1
client
dev tun
resolv-retry infinite
nobind
persist-key
persist-tun
;http-proxy-retry # retry on connection failures
;http-proxy [proxy server] [proxy port #]
verb 4
mute 5
tun-mtu 1500
route-method exe
route-delay 2
explicit-exit-notify 2
fragment  1300
mssfix 1450

```

This is mostly a cosmetic issue, as the command-line approach works, but still, it would be nice to have the GUI work.

Anyone know what might be wrong? 

In, advance, thanks :-).

---

### Post by Castorpoluks on 2010-06-05
I had similar problem with my VPN provider and they told me that they configured VPN accounts on that way that you can not put by ur own.

---

