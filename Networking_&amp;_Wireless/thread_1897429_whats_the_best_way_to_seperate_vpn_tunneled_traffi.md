---
title: "whats the best way to seperate vpn tunneled traffic using 2 nic's same router"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by bababooey on 2011-12-19
I have 2 nics connected to same router. I want to use openvpn with all traffic routed through tun0/eth0. Whats the best way to setup like a proxy to seperate traffic from the vpn, utilizing eth1? For example, I have vmware windows 7 guest running, and I have it using eth1 to use my own internet service. So I been looking into squid3, tinyproxy, but they just bind to ip and port rather than interfaces which makes the setup much easier. Im guessing by using a proxy i would need iptables to forward ports to eth1. Besides using squid, tinyproxy, or iptables, is there anything else someone can recommend I try that could be much easier to setup? An http proxy is sufficient, but socks is fine too.

---

### Post by KeithKris on 2011-12-19
Can you explain what you're trying to do?  If you're looking to route VPN destined traffic over the tunnel and internet traffic over your normal connection, you'd just want to create routes for each subnet that's destined for VPN.  None of those other packages are needed.

---

