---
title: "Connected Wireless Access Point ICS through proxy"
date: 2013-01-14
forum: Networking &amp; Wireless
---

### Post by furything on 2013-01-14
Hi
I am having problems with a Wireless access point (a TP Link box) and sharing my Internet connection. I am hoping some one can point me in the right direction as virtually every search I try points me at creating a wifi share from my linux box.

What am I trying to do?
I have a linux box (mythbuntu installation) that has two ethernet cards. 

[LIST]
[*]One connects to the internet (eth1)
[*]One to a gigabit lan (eth0).
[/LIST]
I am filtering HTTP traffic using squid and dansguardian to all wired PCs successfully. 

My problem is that I am now attaching a Wireless access point on the internal lan. I want all wifi connections to go through the proxy.

Web ---- Linux Box with web filter ----- Lan ---- TP Link (WAP) --- wireless devices
                                                           ---- Wired PC

I have attached outputs from iptable -L and iptables -t nat -L -n-v

From the nat list, if I include 'iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE' 
The wireless devices can now connect to the internet but they bypass the proxy which is a bad thing. Without this MASQUERADE command all wired pcs are filtered and can connect to the internet but the wireless devices timeout.

I need to make the wireless devices go trough the proxy and see the internet?

Please can anyone advise?

---

### Post by furything on 2013-01-22
SOLVED
Updated my iptables now all traffic from wireless devices (android tab/phone, windows laptop) is filtered. 

The iptables I use mean that I don't have to tell the client to go through the proxy it is all done silently.

Wireless Access Point connected to switch connected to eth0
Port 80 is forwarded to 8080 (the dansguardian)
which goes then via proxy (squid3) and through to internet (eth1).

I attach my iptables save tables which I use a script to restore on reboot

---

