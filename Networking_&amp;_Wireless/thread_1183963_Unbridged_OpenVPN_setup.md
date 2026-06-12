---
title: "Unbridged OpenVPN setup?"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by gilgongo on 2009-06-10
I'm on Jaunty, and want to set up a VPN from my desktop machine to a server outside my network so that I can access other machines on the net via SSH and other protocols, which are being blocked on my network.

The trouble is, I'm a screaming n00b.

I've had a look at these forums, and this HOWTO for setup information: [http://www.ossramblings.com/configuring_openvpn_ubuntu_hardy](http://www.ossramblings.com/configuring_openvpn_ubuntu_hardy), but I get "bad source address from client" messages when I try to connect (using NetworkManager and the OpenVPN plugin). I can ping the VPN's server address (10.8.0.1) when I'm connected though.

I've set sysctl -w net.ipv4.ip_forward=1 on my client machine.

Can anyone give me any clues? Here's my config (my desktop's IP is 192.168.1.200):

```
local 120.189.x.x
port 80
proto tcp
dev tun

ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/server.crt
key /etc/openvpn/keys/server.key  # This file should be kept secret
dh /etc/openvpn/keys/dh1024.pem

server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.1.5 255.255.255.255"
push "route 192.168.1.128 255.255.255.128"

keepalive 10 120
comp-lzo
max-clients 4
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
log openvpn.log
verb 3
mute 20
```

:(

---

### Post by UBSec on 2009-06-10
can u post ur client conf file and the full error ?

---

### Post by gombadi on 2009-06-10
> 
local 120.189.x.x
port 80
proto tcp
dev tun


I see you are using tcp port 80 - I guess that is the only port open for you and the reason you want to have the VPN.

Could there be some sort of transparent proxy between you and the remote VPN server that is causing the "bad source address from client" messages?

---

### Post by gilgongo on 2009-06-15
> **UBSec said:**
> can u post ur client conf file and the full error ?

Hmm. Where is my client config? /etc/openvpn just has the file update-resolv-conf in it and nothing else.

I'm using the OpenVPN plugin for the Gnome Network Manager Applet. Any clues there?

Oh, and yes, I'm using port 80 but I assume it's OK.

BTW this is the firewall config on the VPN server:

iptables -A FORWARD -i tun0 -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -j MASQUERADE

(IP forwarding is turned on as well)

---

### Post by jhannah on 2009-06-17
The error you are seeing has to do with the server seeing traffic from a host it doesn't have a route for. You should be able to fix it by removing the push lines, and making the changes below:

OpenVPN config:
```
client-config-dir ccd
route 192.168.1.0 255.255.255.0

```/etc/openvpn/ccd/client1:
```
iroute 192.168.1.0 255.255.255.0
```After that, just restart the OpenVPN server- you shouldn't need to change anything on the client side.

Make sure to change 'client1' to whatever you named your client when you ran ./build-key in the initial OpenVPN setup.

---

### Post by gilgongo on 2009-06-22
Ah! Thanks for that!

---

