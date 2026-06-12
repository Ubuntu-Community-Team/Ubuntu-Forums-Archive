---
title: "Forwarding traffic from a specific port to either WAN or VPN"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by PikkuIcaros on 2012-02-08
I just flashed "Tomato by Shibby" firmware on my Asus RT-N16 router. I also subscribed an OpenVPN service from Vpntunnel.se. My router works as an OpenVPN client and routes all the traffic through VPN-tunnel. It is working fine.

I'm new to iptables. I just figured out how to forward a specific port from VPN-tunnel to a specific LAN client. I still have this problem: there are some services I want to route directly to WAN.

I want iptables NOT to route smtp (port 25) traffic form LAN client 192.168.1.15 through VPN. What should I tell my router's iptables? (Yes, this is unsecure but I have my reasons…)


Some technical details:

Network interfaces on my router:

br0        Link encap:Ethernet  HWaddr BC:AE:C5:C5:1D:94  
           inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0

eth0       Link encap:Ethernet  HWaddr BC:AE:C5:C5:1D:94  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth1       Link encap:Ethernet  HWaddr BC:AE:C5:C5:1D:96  
           UP BROADCAST RUNNING ALLMULTI MULTICAST  MTU:1500  Metric:1

lo         Link encap:Local Loopback  
           inet addr:127.0.0.1  Mask:255.0.0.0

tap0       Link encap:Ethernet  HWaddr 00:FF:2F:44:8B:B0  
           inet addr:178.73.xxx.xxx  Bcast:178.73.xxx.xxx  Mask:255.255.255.0

tap21      Link encap:Ethernet  HWaddr 00:FF:60:0D:52:DC  
           UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1

vlan1      Link encap:Ethernet  HWaddr BC:AE:C5:C5:1D:94  
           UP BROADCAST RUNNING ALLMULTI MULTICAST  MTU:1500  Metric:1

vlan2      Link encap:Ethernet  HWaddr BC:AE:C5:C5:1D:95  
           inet addr:86.50.xxx.xxx  Bcast:86.50.xxx.xxx  Mask:255.255.254.0


I think vlan2 is WAN interface and tap0 is VPN, and of course bro is local.

---

