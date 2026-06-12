---
title: "setup a VPN and forward trafic to other VPN"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by blejzzz on 2011-12-04
Hello,

I want to setup a VPN connection with my server which already has a secure VPN to another server (over IPsec). And now i need to create a new VPN connection (for testing purposes) that will enable me to connect to the secure VPN via my server. 

My server has 1 network interface (eth0 and external IP ). The secure VPN uses eth0:0 which is a virtual network interface with IP 71.185.200.240.

Goal: connect to the secure VPN (from my work office) and access a page on it with address: [FONT=&quot] [http://20.35.166.61:6084/test/]("http://10.15.122.61:8084/tpim/")[/FONT] 

How it should work:

  my home office -> connects to work VPN (which is on my server)   -> the server gets packets through interface ppp0 -> iptables  should forward and translate all the  packets to eth0:0 (VPN over IPsec)

What i've done so far: 
 - installed poptop (pptpd) 
 - gave it a localeip and a remoteip (localeip 192.168.0.1 remoteip 192.168.0.100-200)
 - accept all trafic from ppp0: iptables -A INPUT -i ppp0 -j ACCEPT  
 - accept all forward from ppp0 to eth0: iptables -A INPUT -i ppp0 -o eth0 -j ACCEPT 
opened gre protocol: 
        - iptables -A INPUT -p gre -j ACCEPT 
        - iptables -A OUTPUT -p gre -j ACCEPT
 -  addded the DNAT and SNAT:
     - iptables -A PREROUTING -p tcp -i ppp0 -j DNAT --to 91.185.200.240 (forward to eth0:0)
     - iptables -t nat -A POSTROUTING -s 192.168.0.1 -o eth0 -j SNAT --to  71.185.200.240 (change the IP if coming from ppp0)

But the problem is that nothing works and i'm not quite sure how to debug it to see whats going wrong (not an expert on networks). I can connect through the VPN, but it disconnects after a couple minutes. And i can't ping the IP on the secure VPN (i can ping it from the server just fine). Also when i connect to the VPN my internet connection drops..

Did anyone try to setup a connection like this? What am i missing?
Any help is appreciated.
Thanks for the help,

Regards,
J.

---

