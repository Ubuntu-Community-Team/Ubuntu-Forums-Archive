---
title: "Help with OpenVPN, having routing issues..."
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by redmage123 on 2013-02-22
Hello all, 

I posted this to the openvpn forums, but I haven't gotten any response back, so I figured I'd give this forum a try. 

I'm running an openvpn server/client lan setup as follows: 

Server
10.11.14.1 netmask 255.255.0.0

Client gateway

10.10.12.1 netmask 255.255.0.0

client system A
10.10.12.149 netmask 255.255.0.0

My problem is that I can't ping the server from client system A. 
The logs show a bad source address for 10.10.12.149 on the server. 

I've created a CCD/client file with the iroute 10.10.0.0 255.255.0.0
directive as well as put in the route directive route 10.10.0.0 255.255.0.0
in the server.conf file.  

Also, the server and client gateway are set up for ip forwarding, and i've put in rules in the iptables firewall on the server and the client gateway to recognize tun0 (the virtual openvpn routing device) and to open up port 1194.  

My server.conf file looks like this: 

ort 1194
proto tcp-server
dev tun
ca /etc/openvpn/ca.crt
cert /etc/openvpn/server.crt
key /etc/openvpn/server.key
dh /etc/openvpn/dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
#push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
push "route 10.11.0.0 netmask 255.255.0.0"
client-to-client
#duplicate-cn
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
log /var/log/openvpn.log
verb 12
client-config-dir /etc/openvpn/ccd
route 10.10.0.0 255.255.0.0

I have a ccd/client file with the following line:

iroute 10.10.0.0 255.255.0.0

I can ping the server from the client vpn gateway, but not from the connected client A...

Anybody have any ideas? 

Thanks 

== redmage123

---

