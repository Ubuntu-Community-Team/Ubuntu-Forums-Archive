---
title: "Routing all traffic via Openswan IPSEC tunnel"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by rwhiteside90 on 2013-02-22
I'm trying to route traffic from my local network over the VPN. I have a VPN server running Ubuntu 12.04 LTS using OpenSwan for an IPSEC tunnel from my Sonicwall router. 

For an example I routed all ICMP traffic from one computer on my network (10.250.0.99) to route over the VPN. On the VPN server  I can verify using tcpdump -i eth0 icmp that my server is receiving my test ping to google.ca but it's receiving any replies or not even forwarding the traffic out. 
ubuntu@ip-10-254-0-5:~$ sudo tcpdump -i eth0 icmp
sudo: unable to resolve host ip-10-254-0-5
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
20:50:24.627018 IP 10.250.0.99 > ord08s08-in-f24.1e100.net: ICMP echo request, id 1, seq 191, length 72
20:50:28.615379 IP 10.250.0.99 > ord08s08-in-f24.1e100.net: ICMP echo request, id 1, seq 192, length 72
20:50:32.617661 IP 10.250.0.99 > ord08s08-in-f24.1e100.net: ICMP echo request, id 1, seq 193, length 72

I can ping anything on the subnet and get replies no problem. 

Any suggestions on how to fix this? I'd like to just have all traffic routed all over the VPN through this VPN server to work hopefully.

---

