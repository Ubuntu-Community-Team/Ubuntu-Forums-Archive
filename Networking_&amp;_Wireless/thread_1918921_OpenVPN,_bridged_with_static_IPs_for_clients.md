---
title: "OpenVPN, bridged with static IPs for clients"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by JoeSabido on 2012-02-01
In the near future I'll need to setup a bridged VPN (using OpenVPN) in which each client always gets the same IP, which I should define beforehand. 

I have some previous experience with routed VPN but not with bridged, and the reason it must be bridged with static IPs is because some MySQL databases in the server's internal network that have restricted access depending on the requesting IP, and some people who usually access these servers from the inside, need to do it from the outside too.

I'm such a noob, so I'm gonna tell you things as I see them:

This line would set the server's own VPN IP and which IPs should the clients get (server-ip mask start-ip end-ip):

server-bridge 10.5.0.1 255.255.255.0 10.5.0.2 10.5.0.100

Right?

What I've done with routed VPN before is to make a pre-filled text file with the names of the clients and then use ifconfig-pool-persist (pointing to such file) to tell the client which IP to use, effectively fooling the client into thinking it has connected before and previously got the IP it's getting now.

Then, I guess I need to tell the server that this range of IPs can join the server's own internal network:

push "route 192.168.1.0 255.255.255.0"

What I don't understand is, at which point the client gets an 192.* address? Also, for the ifconfig-pool-persist, do I use 192.* addresses or 10.* addresses?

I hope this makes sense and thanks for any input you can provide.

---

