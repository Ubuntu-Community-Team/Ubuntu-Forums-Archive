---
title: "iptables allow local client to connect to vpn client."
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by darkshadow on 2012-07-24
How can I do this? I am using openvpn with tun, which due to limitations (stock unrooted android phones) can't be changed to tap

Currently I have working
VPN to VPN
VPN to local

But I just can't get local to VPN


Here is my current iptables commands which I don't totally understand since they are copy and pasted from the net. Also all client traffic goes through the VPN which is my choice and the only reason I setup VPN.



sudo iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -s 10.8.0.0/24 -j ACCEPT   
sudo iptables -A FORWARD -j REJECT
sudo iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
sudo iptables -t nat -A PREROUTING -i tun+ -p udp --dport 53 -j DNAT --to-destination 8.8.8.8
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward

---

