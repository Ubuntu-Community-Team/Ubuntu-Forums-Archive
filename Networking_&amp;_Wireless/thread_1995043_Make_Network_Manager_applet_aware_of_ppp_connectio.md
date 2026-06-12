---
title: "Make Network Manager applet aware of ppp connections"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by diosney on 2012-06-03
Hi

         The issue I've is that when I connect via modem through  gnome-ppp the Network Manager Applet don't detect a connection and don't  let me use the configured VPNs via its interface.


  How Can I manually activate the Network Manager Applet or make it aware of the ppp connection?


  What I need is to enable the Network Manager apple in order to use the "VPN Connection" section of the GUI.


  When I don't have an ethernet cable connected and I connect through a  modem the Network Manager applet doesn't enables itself, it is like if  don't recognizes the ppp0 interface. My question is: there is a way to  force the Network Manager GUI indicator to make it  "alive"/"up"/"enabled" in order to use the "VPN Connections"section?


pd. I'm using 11.10


  Thanks in advance.

---

### Post by steeldriver on 2012-06-03
if gnome-ppp defines the connection in /etc/network/interfaces then by default network-manager will ignore it

you could edit /etc/NetworkManager/NetworkManager.conf and set 

```
[ifupdown]
managed=false
```to
```
[ifupdown]
managed=true

```and then

```
sudo service network-manager restart
```I've heard that the two services might not play nicely though - if you get problems you may want to consider redefining the ppp connection directly in NetworkManager (Edit Connections... --> DSL --> Add) and removing it from /etc/network/interfaces altogether

I also don't know if that will be enough to enable your VPN setup

---

