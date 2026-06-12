---
title: "OpenVPN static route problem"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by guardia on 2011-07-08
Dear forum,

I have been trying to get my OpenVPN to work; to protect sensitive company data sent via public WiFi networks.

Please assume:
1) server running OpenVPN 2.2.0 as daemon
2) laptop running Ubuntu 11.04 + OpenVPN 2.1.3 as client

Basically, the OpenVPN works. I can connect to the VM and on the client/laptop i get this output:
```
tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.6  P-t-P:10.8.0.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```Now the static routes look a bit weird to me:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.5        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.8.0.1        10.8.0.5        255.255.255.255 UGH   0      0        0 tun0
```(note: i censored the non-relevant static routes for privacy reasons)

Now these static routes appear weird to me, and i think it all has to do with the fact that OpenVPN uses a multi-client configuration that allows multiple clients to connect. For example, if i have to believe ifconfig i have a tunnel from 10.8.0.6 (client) to 10.8.0.5 (server); but this is incorrect. The server is 10.8.0.1 instead; not 10.8.0.5. Pinging 10.8.0.5 will not give response but pinging 10.8.0.1 will!

**_Now the real problem_**: i cannot add a default gateway to 10.8.0.1!

```
$ sudo route add default gw 10.8.0.1
SIOCADDRT: No such process
```If i try to add a gateway to 10.8.0.5 instead, then the command works without error and it appears in the route tables; but of course that does not work; i need default gateway to 10.8.0.1 instead!

The openvpn.conf at the beginning states:
```
# This file is for the server side              #
# of a many-clients <-> one-server              #
# OpenVPN configuration.                        #
#                                               #
# OpenVPN also supports                         #
# single-machine <-> single-machine             #
# configurations (See the Examples page         #
# on the web site for more info).               #
```However on the website i cannot see any single client configuration example; i'm linked instead to the 'many client' example.

So basically that's where i'm stuck. Everything works, except adding the static route doesn't due to the odd IP addresses. Ideally i would just want to have a simple 10.8.0.1 -> 10.8.0.2 tunnel; plain and simple. I use only one client and just want to be able to set my default gateway over the tunnel. Seems pretty basic setup to me, what did i do wrong?

My full openvpn.conf on the server:

```

port 22222
proto tcp
dev tun

ca keys/ca.crt
cert keys/server.crt
key keys/server.key
dh dh1024.pem

server 10.8.0.0 255.255.255.0
keepalive 3600 8000
comp-lzo
max-clients 2

user nobody
group nobody

persist-key
persist-tun

status openvpn-status.log
log         openvpn.log
verb 3
mute 2
```

---

### Post by spynappels on 2011-07-08
You need to understand a little about VPN tunnels. They are point to point tunnels, with an IP at the client end (10.8.0.5) and an IP at the server end (10.8.0.6). Because a server may have many tunnels connected to it, it could conceivably have to listen to many IPs at its end, so it automatically routes traffic from all it's endpoint IPs to it's "master" IP (10.8.0.1). 

So the route specified is correct in that all traffic which is to go through the VPN server has to go through 10.8.0.5 to the other end of the tunnel 10.8.0.6 where it is "routed" through 10.8.0.1 and then further to it's destination.

This setup is the same whether you use a one to one setup or many to one.

Are you having problems routing traffic to the LAN from your VPN?

---

### Post by guardia on 2011-07-08
> **spynappels said:**
> They are point to point tunnels
To me that means one server and one client; point to point. It seems to me that OpenVPN plays tricks with that and it's not a real point-to-point tunnel but rather a point to multiple point tunnel; am i making any sense?

> so it automatically routes traffic from all it's endpoint IPs to it's "master" IP (10.8.0.1).And that's where it goes wrong; because the client sets up static routes on the wrong IP, where it should setup the static routes to 10.8.0.1 instead.

> Are you having problems routing traffic to the LAN from your VPN?My problem is - as described - that i cannot add a default gateway to 10.8.0.1 with mentioned error message. If OpenVPN would not do the IP address trick then i'd assume it would have worked perfectly instead, since i *can* add a default gateway to 10.8.0.5 but that does not work; i have to use 10.8.0.1.

Without being able to setup a default gateway, the tunnel is useless to me since i cannot use it for internet access and thus secure my sensitive data from public unprotected WiFi hotspots.

Please note i do not need access to the LAN 'behind' the server or connectivity between multiple VPN clients; i only need the simplest of VPN setup where there is a secure connection between client and server, where the client can use default gateway to the server which also acts as NAT gateway and DNS server, to allow for secure internet access.

In the past i can remember using OpenVPN with a setup mentioned above and it 'just worked' -- but now i seem to be stuck on that weird error message not allowing me to set a default gateway in Ubuntu. Bummer!

---

### Post by spynappels on 2011-07-08
You could try to use the Gnome OpenVPN Manager plugin for Network Manager, this allows you to specify whether you want all traffic to go through an established tunnel or only traffic for the resources behind it. I believe it uses the first option as a default.

re. the Point to Point tunnels, each client will have it's own point to point tunnel, with it's own endpoint IPs, but the server can handle multiple tunnels at once and "aggregates" all its own endpoints to one IP which all clients can reference.

---

### Post by SeijiSensei on 2011-07-08
With one client and one server, a shared static-key approach is much simpler to configure.  See this [HOWTO]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") for details.

---

### Post by guardia on 2011-07-08
> **spynappels said:**
> You could try to use the Gnome OpenVPN  Manager plugin for Network Manager, this allows you to specify whether  you want all traffic to go through an established tunnel or only traffic  for the resources behind it. I believe it uses the first option as a  default.
I have the openvpn gnome thingy installed and i  connect to the VPN using the NetworkManage (click-> VPN connections  -> *name of VPN*). I then get a message that the VPN is connected  successfully. So that appears to work. And i can ping and ssh to the  server. So it works, or so i thought.

But the real problem is my  inability to set the server as default gateway; so my internet traffic  is routed over the VPN and thus protected from the unencrypted WiFi  hotspot which everyone can snoop. I cannot send sensitive customer data  over unprotected WiFi!

> re. the Point to Point tunnels, each client will have it's  own point to point tunnel, with it's own endpoint IPs, but the server  can handle multiple tunnels at once and "aggregates" all its own  endpoints to one IP which all clients can reference.
I think i  understand a little; but if i'm right this also causes my problem.  Since the client sees a wrong IP belonging to the 'end point' of the  tunnel.

So because of this 'feature' the client cannot set a  default route to the host at the end of the VPN tunnel. How would i go  about fixing that?

> **SeijiSensei said:**
> With one client and one server, a shared  static-key approach is much simpler to configure.  See this [HOWTO]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") for details.
I understand that; but i've already got the certificate stuff working.  Am i wrong assuming that my network problem is unrelated to the method  of authentication?

---

### Post by SeijiSensei on 2011-07-09
> **guardia said:**
> But the real problem is my  inability to set the server as default gateway; so my internet traffic  is routed over the VPN and thus protected from the unencrypted WiFi  hotspot which everyone can snoop. I cannot send sensitive customer data  over unprotected WiFi!

You can only make the remote VPN host the default gateway if you also have a route for the traffic that encapsulates the tunnel.  Otherwise there would be no way for the tunnel to be maintained.  The computer I am writing on now has a wifi connection that it uses to reach my Linux egress router; all other traffic is sent through the tunnel.  My routing table looks like this:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.1   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
10.100.1.1      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
0.0.0.0         10.100.1.1      0.0.0.0         UG    0      0        0 tun0
```

192.168.100.1 is the IP address of the Ethernet adapter on the router.  I have a route to that via my wifi router at 192.168.1.1.  10.100.1.1 is the IP address of the VPN interface on the router.  With these routes all traffic for 192.168.100.1 is sent over the wifi connection so that the tunnel can be established, but all other traffic is sent through the tunnel.

I have to run a separate script using sudo after starting the wifi connection.  I've tried on a couple of occasions to figure out how to make plasma-network-widget (in KDE) run the script for me automatically after the connection is made.  So far I've been unsuccessful at figuring out how to do this, so I just run the script manually from the terminal after I start the wireless connection.

Trying to do this from any random wifi connection is a bit tricky since you'd need to know the default gateway that your client is using.  I'd try this approach.  First connect to the wifi network, then use the route command to see what the default gateway is.  Then add a route to your VPN server that uses that host.  Finally replace the default gateway with one that points to the server VPN address.  If you're using a variety of remote locations, this is a bit of a pain.  You might be able to script it, or you can just set it up manually each time you need to do this.

---

### Post by guardia on 2011-07-12
In the end i managed to solve my problem by using a static key instead.  This does change the behavior of the assigned IP addresses. In the  ifconfig output you get to see 10.8.0.1 -> 10.8.0.2 and those are the  real IP addresses; unlike the fake 10.8.0.5 -> 10.8.0.6 i got  earlier when using certificate authentication.

The result is that setting the default route to 10.8.0.1 is no problem  and works as i'm used to it. So the fake 'internal IP address rerouting'  feature of OpenVPN did not work well for me and circumventing this  'feature' using static key proved to be the solution to my problem.

The other problems i encountered were not being able to set the static  route in the gnome VPN configuration (GUI) - so i eventually needed to  use a terminal script anyway. Seems to me not many people use a VPN to  relay internet traffic; strange since that should mean alot of people  send their data unprotected via WiFi? Sounds very insecure to me...

Anyway, thanks to everyone who replied. I wish OpenVPN was polished a  bit better so configuring it wasn't such a pain. Eventually i got what i  wanted: protect 'open WiFi' traffic from eavesdroppers.

---

