---
title: "Help spiting VPN connection and normal connection"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by BudworthTDog on 2013-02-10
So I try not to be that guy that just posts new threads without exploring to see if they have already been posted in previous threads. I'm honestly not quite sure where to go for this though, any pointers, even if its just a link to another thread will help.

I like to run my internet connection through a VPN service. I have it up and running just fine. iVPN.net is the service I use. I have recently started running a Plex server on my computer. The Plex server runs fine when not connected to the VPN but doesn't want to publish when I have my VPN running. Frankly I'm okay with this in a sense because preferably I would like Plex to bypass my VPN altogether but my other services through the VPN. 

I'm not new to Linux or command line but not super knowledgeable at the same time. My educated guess is to use iptables to route by port, not sure but just a guess.

Here are the particulars to what I want to do

Run through normal internet connection:
Plex server runs through port 32400

Run through VPN:
I guess preferably all but if it needs to be defined at least
Web surfing port 80 (duh)
and qBittorent port 6881

I use an ethernet connection on this computer eth0

I set up my VPN service though a pre-configured .conf file. If that is helpful here are its contents

```
client
dev tun
proto udp

remote gw1.uk.ivpn.net 2049
auth-user-pass

resolv-retry infinite
nobind
persist-tun
persist-key

ca ca.crt
cert client1.crt
key client1.key
tls-auth ta.key 1

cipher AES-256-CBC
ns-cert-type server
comp-lzo
verb 3
```

Any help is appreciated

---

### Post by BudworthTDog on 2013-03-01
bump

---

