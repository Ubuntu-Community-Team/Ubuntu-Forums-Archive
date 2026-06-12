---
title: "Ubuntu Server and ip address"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by Gremlyn on 2009-04-19
I am running ubuntu server connected to my network via a dlink dsl 604t router. When the server is booted up it reterives a static ip address from the router with no problem, however if i reboot the router, it will not assign a ip address to the server. So i need to reboot the server to get an ip address. 

im not sure if this is a problem with the server or the router but as my windows machines have no problem i am guessing the problem lies with the settings on the server.

Any help appreciated.

---

### Post by puppywhacker on 2009-04-19
ubuntu runs the dhcp client and connects tot the dhcp server on the router. By protocol it is always the client that initiates dhcp, never the router sending new IP-address. Some windows machines use unexplained magic to retrieve a new address when it figures out that the connection has failed. In Ubuntu you can do many things to retrieve a new ip-address

one of them is to restart the network
sudo /etc/init.d/networking restart

---

