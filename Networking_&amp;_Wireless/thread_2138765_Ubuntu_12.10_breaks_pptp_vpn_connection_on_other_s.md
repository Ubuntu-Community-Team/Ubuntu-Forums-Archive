---
title: "Ubuntu 12.10 breaks pptp vpn connection on other server"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by RuralHunter on 2013-04-25
Here is my situation:

We have a ubuntu server(A) which acts as the router to the network at another remote location. There is a pptp client which connects to the VPN server at the remote location. Here is the network route when we tries to connect to the servers at remote location:
All clients at my location(windows, ubuntu)-->Router device(R)-->Ubuntu Server(A)---pptp--->Remote VPN server(B)
network at my location: 192.168.1.*
network at remote location: 192.168.0.*
I have set up the route on my router device(R) so that all the access to remote network range will be routed to server A and then routed to the remote VPN server through the pptp connection. This works fine with all clients(many versions of windows and ubuntu servers) at my location except one Ubuntu 12.10 desktop. Everytime this client tries to connect to or even ping the servers at remote location(192.168.0.*), the pptp connection between A and B disconnected.

This is really strange. I'm wondering if there is any thing special in the packets the Ubuntu 12.10 desktop sends out? How to troubleshoot this?

---

