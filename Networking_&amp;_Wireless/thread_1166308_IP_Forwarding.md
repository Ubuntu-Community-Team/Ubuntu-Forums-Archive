---
title: "IP Forwarding"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by mindfields83 on 2009-05-21
Hi,

My setup is like this

[IMG]http://www.iain09.pwp.blueyonder.co.uk/xbox%20wireless.jpg[/IMG]

The devices have the following IP addresses,
 
Xbox - IP Address 192.168.1.126
Access Point - IP Address 192.168.1.1
PC wlan0 - IP Address 192.168.1.142

PC eth0 - IP Address 192.168.10.15
Router - IP Address 192.168.10.1

I want the xbox to be able to access the internet but don't know how!

So far I have enabled ip forwarding with sudo sysctl net.ipv4.ip_forward=1
I think its not working due to the default gateway being wrong. Can anybody tell me what the gateway should be on the xbox and access point so I can ping the router from them.

Thanks

---

### Post by Iowan on 2009-05-21
Have you seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page? there's a [link]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") near the end on wireless.

---

### Post by mindfields83 on 2009-05-23
That first link sorted me right out, thanks a lot.

This part in particular 

sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE

The all I had to do was set the default gateways on the wireless side to the ubuntu gateways wlan IP address. :)

---

