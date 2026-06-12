---
title: "Access samba share across internet?"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by mnwaterbug on 2010-06-05
I have Samba on Ubuntu 9.1 server, it works well in my office with several Windows PCs.

The office network connects to the internet with a DSL modem which is configured for SSH,  so I can access the Ubuntu server from my home using putty.

I'd like to map network drives on my home windows PC, so for example:  "Z:\" could refer to a directory on the Ubuntu server.  Any suggestions on how to do that would be appreciated!

---

### Post by mnwaterbug on 2012-05-12
I solved this by installing openvpn on Ubuntu and [http://openvpn.se](http://openvpn.se) and a tap network connection on Windows (named MyTap).  Use client bridging on OpenVPN GUI and config file looks like this:
[COLOR="Blue"]client
dev tap
dev-node MyTap
proto udp
remote 11.111.111.233 500
nobind
resolv-retry infinite
persist-key
persist-tun
ca "C:\\Program Files\\OpenVPN\\config\\ca.crt"
cert "C:\\Program Files\\OpenVPN\\config\\mykey.crt"
key "C:\\Program Files\\OpenVPN\\config\\mykey.key"
tls-auth ta.key 1
auth none
cipher none
tun-mtu 36000
fragment 0
mssfix 0
comp-lzo
verb 4[/COLOR]

---

