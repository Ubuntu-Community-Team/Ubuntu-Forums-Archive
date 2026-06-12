---
title: "OpenVPN routing problems"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by Badgerness on 2011-12-12
Hello everyone,
 
First timer on this forum, and been using Ubuntu for less than a week so far.
 
I installed OpenVPN on a VPS a few days ago and set it up properly, and is able to connect from my client PC to the internet via the VPN.
 
So here is my scenario. I decided to setup my OpenVPN on Ubuntu Server 10.04 on my dedicated server. Assuming I setup the networking interface properly (able to ping google from the terminal and etc), created the certs.
 
My client PC is able to connect to the VPN and is assigned with an internal IP address, but the client PC is unable to reach/ping anywhere, but the default gateway of the VPN (10.8.0.1).
 
Here is my config for /etc/rc.local, where 175.xx.xx.xxx is my server IP
 
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
# add iptables rule for openvpn
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o venet0 -j SNAT --to 175.xx.xx.xxx
exit 0

 
This is my openvpn server config file at /etc/openvpn/openvpn.conf
 
> dev tun
proto tcp
port 1194
ca /etc/openvpn/easy-rsa/2.0/keys/ca.crt
cert /etc/openvpn/easy-rsa/2.0/keys/server.crt
key /etc/openvpn/easy-rsa/2.0/keys/server.key
dh /etc/openvpn/easy-rsa/2.0/keys/dh1024.pem
user nobody
group nogroup
server 10.8.0.0 255.255.255.0
persist-key
persist-tun
#status openvpn-status.log
#verb 3
client-to-client
duplicate-cn
push "redirect-gateway def1"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 4.2.2.4"
comp-lzo

 
ipv4 forwarding is set to 1 (enabled) in /etc/sysctl.conf
 
> net.ipv4.ip_forward = 1 
 
Further looking into the problem by typing iptables -L -t nat
 
Here is what I got,
 
> 
Chain PREROUTING (policy ACCEPT)
target prot opt source destination 
Chain POSTROUTING (policy ACCEPT)
target prot opt source destination 
MASQUERADE tcp -- 192.168.122.0/24 !192.168.122.0/24 masq ports: 1024-65535 
MASQUERADE udp -- 192.168.122.0/24 !192.168.122.0/24 masq ports: 1024-65535 
MASQUERADE all -- 192.168.122.0/24 !192.168.122.0/24 
SNAT all -- 10.8.0.0/24 anywhere to:175.xx.xx.xxx 
Chain OUTPUT (policy ACCEPT)
target prot opt source destination 

 
I don't understand why there is a MASQUERADE tcp/udp on the postrouting when I did not specify it. Unless some other programs in the background was interfering it. 
 
I tried flushing the iptables, rebooting the server and restarting the client PC, but the same problem exists. 
 
Any help would be appreciated. :D
 
Thanks!~

---

