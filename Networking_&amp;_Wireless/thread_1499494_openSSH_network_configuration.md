---
title: "openSSH network configuration"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by trioggle on 2010-06-02
Hi guys,

I've been reading manuals on how to get openSSH to work properly. The theory is straight forward but when it comes to the practical application, I get stuck with the private ip configuration.

I have a bell modem/router 192.168.2.1 connected to a D-link router with the address as 192.168.0.1

I understand that this is my local network address/gateway and on the internet side, my ip address is 66.100.122.123

While setting up the server should I be using my public ip address as the connection source?
ssh -w0:0 66.100.122.123 

A client would want to connect to my public ip address and then I'd want to configure the server to route that to a private ip address, i.e. 10.0.0.2. Does that make sense?


Basically I'm getting confused between the different addresses:

Server:

Public IP address 66.100.122.123 .
Private Network 192.168.0.0/24
Private IP address 192.168.0.199
default gw 192.168.0.1

Client

Public IP address - does not matter?
Private network 192.168.0.0/24
Private IP address 192.168.0.10
Default gw 192.168.0.1

Tunnel 

Server tun0 IP address = 10.0.0.1
Client tun0 IP address = 10.0.0.2


What I think in theory: The client connects to the public ip address on the server (66.xx....) and the ssh port (22) gets routed to the private address (192.168.0.199). Then it somehow gets translated to the tunnel address 10.0.0.1
:confused:

---

