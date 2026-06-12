---
title: "Openvpn problems"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by kojis_ on 2009-12-18
I'm trying to connect internet through openvpn server. I'm able to connect to server with "network-manager-openvpn" and ping 10.8.0.1 but when i'm connected, network stop working (can't use firefox, xchat etc..).

My goal is that i can browse internet through openvpn server.

Openvpn server (Ubuntu 9.04 server):
Santrex VPS, tun/tap devices enabled.
Static IP: 94.xxx.xxx.xxx

Config:
```

dev tun
proto tcp
port 1194

ca ca.crt
cert server.crt
key server.key
dh dh1024.pem

user nobody
group nogroup
server 10.8.0.0 255.255.255.0

persist-key
persist-tun

#status openvpn-status.log
#verb 3
client-to-client

push "redirect-gateway def1"

#log-append /var/log/openvpn
comp-lzo

```

Cliet machine (Ubuntu 9.10 desktop):
Dynamic IP by ISP.
```

dev tun
client
proto tcp
remote 94.xxx.xxx.xxx 1194
resolv-retry infinite
nobind
user nobody
group nogroup

# Try to preserve some state across restarts.
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
comp-lzo

# Set log file verbosity.
verb 3 

```

---

### Post by noway2 on 2010-01-02
Normally, non VPN traffic will go through the standard ethernet link.  In you case, you want to redirect ALL network traffic through the VPN, which is doable, and is handled by the command: push "redirect-gateway def1".

However, when you do this, you will now be dependant upon your VPN server for other network functions such as DNS and you will need to add commands to handle this too.  For example:

push "dhcp-option DNS <your DNS server>" and
push "dhcp-option DOMAIN <your domain>"

---

### Post by DGortze380 on 2010-01-02
In addition to the above advice, you will likely need to enable IP Forwarding on the OpenVPN Server and push a route for the subnet behind the server.

---

