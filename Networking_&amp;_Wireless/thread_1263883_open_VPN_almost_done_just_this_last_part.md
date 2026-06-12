---
title: "open VPN almost done just this last part"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by bigboy7foru on 2009-09-11
TCP/UDP: Socket Bind failed on local address 216.253.219.22:1194: Cannot assign requested address 
 
any ideas??

---

### Post by gombadi on 2009-09-11
What is the ip address of the machine you are running this on?

Post the output of ifconfig command.

---

### Post by bigboy7foru on 2009-09-11
I believe the ip is 192.168.0.104

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:09:5b:1a:3d:ca  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe1a:3dca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7050561 (7.0 MB)  TX bytes:481939 (481.9 KB)
          Interrupt:10 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by SpaceTeddy on 2009-09-11
Ok, if you want a roadwarrior configuration there are a few basic steps you need to take. 

a) you need a computer/server/something that is reachable from the outside. This machine does not need a lot of juice, but it *must* be reachable from the Internet and know a path (or be directly attached) to the network you want to do stuff with. Since you wrote you want remote control, it is probably the best way to go for a pure layer-3 connection. This will reduce the traffic on the Uplink of the company.

b)you will need to understand a little about routing and how subnets are propagated. This will cause a headache at the start, but will (hopefully) become clear rather quickly.

So, the basic setup we are talking about here looks like this

OpenVPN Client
|
(public IP)
Firewall/Nat
(private IP, in your case probably 192.168.0.1)
|
(192.168.0.0/24 Network)
Internal Lan
|
(192.168.0.104)
OpenVPN Server

The first thing you really... really need to do is to make sure that the firewall accepts requests on port 1194 (tcp) and forwards them to 192.168.0.104. Without this, there is no way this is going to work - at all. Also, you cannot test this from your office (well - you could, but that would get complicated).

So - once you have your forward on the nat box setup (you can test this via telnet'ing to port 1194 on the public IP FROM SOMEWHERE ELSE on the Internet) you will need to setup the server

here is a "sample" configuration for a simple roadwarrior configuration:

```

daemon
port 1194
proto tcp
dev tun0

ca <path to ca.crt>
cert <path to server.crt>
key <path to server.key>
dh <path to dh file>

server 192.168.4.0 255.255.255.0
push "route 192.168.0.0 255.255.255.0"

client-to-client
keepalive 10 120
comp-lzo

user nobody
group nogroup

persist-key
persist-tun
status /var/log/openvpn/public-status.log
log-append  /var/log/openvpn/public.lo

```

Please notice that i am NOT binding the server to any specific IP - i am letting it figure that out by itself. Actually, i want to be reachable on all interfaces.
Also notice that i am using *a differnt* network than the one configured on the server. This will make the server open a complete new network which is (for now) separate from the rest of the Lan you want to reach.
Lastly, i am pushing a route to all clients that connect. This will cause clients to use the VPN connection for the pushed network INSTEAD of their normal Internet connection.
I saw in your configuration that you had other options (like pam authentication) enabled. You can extend this config any way you want - this is only the bare minimum i feel is needed.

Now, the next thing you need to do is tell your server that is shall forward packets (needed to reach something behind the vpn server)

```

sudo sysctl -w net.ipv4.ip_forward=1

```

and tell your server to masquerade all traffic from the clients behind it's own ip address. This could be circumvented in other ways, but for now this is the safest way as it requires NO CHANGES to anything else in the Network. 

```

sudo iptables -t nat -A POSTROUTING -s 192.168.4.0/24 -o eth0 -j MASQUERADE

```

This option will also prohibit LAN computers to connect to VPN clients - if you need this the setup needs to be changed...

If i am not mistaken, your server should be functional now... 

Now for the client - here is a sampe config for the client:
```

float

client
dev tun
proto tcp

remote <the external IP of the NAT/Firewall box>

resolv-retry infinite
nobind
persist-key
persist-tun
ca <ca.crt of the server - this needs to be the same file>
cert <your client certificate - if you use PAM, this is not needed>
key <your client key - if you use PAM this is not needed>
ns-cert-type server
comp-lzo
verb 3

#vista options - uncomment if needed
# route-delay 2
# route-method exec


```

with this config and the appropriate keys you should be able to establish a connection...

I know this is very... very brief. Here are some more articles about how to setup OpenVPN
[http://ubuntuforums.org/showthread.php?t=752127](http://ubuntuforums.org/showthread.php?t=752127)
I cannot find my other posts anymore - but i know i have written a tut on almost any setup that you can do with OpenVPN... somewhere... 
However, the mentioned article there should not be followed by you at the moment - this is a far to complex setup for now...

Hope it helps

---

### Post by bigboy7foru on 2009-09-15
Thanks ill try that this week and hopfully it will work for me

---

