---
title: "openvpn"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by network2180 on 2009-11-08
Can someone please give a detailed tutorial on setting up openvpn on a server for secure internet surfing? Here is my problem:
1. I have ubuntu linux installed on my system
2. I have ssh access (root ssh) on a dedicated server. I have ONLY ssh access (NOT physical access) but can install anything I want on it (including any other service I want), I can use ssh tunnel but it has limitations so I need openvpn
3. I have the latest openvpn on my system and remote server (I can ping both 10.4.0.1 and 10.4.0.2, and make tcp connections over the server to services running on the server)
4. I successfully configured openvpn on both my system and server to the point where I can ping both sides of the tunnel.
5. When I specify routing to go over vpn tunnel interface, I can ONLY access the tunnel and the local network (since there's another route for my LAN 192.168.*.* to bypass VPN), I CANNOT ping other hosts on internet or make ANY internet traffic with them (icmp, udp, tcp: http, dns, anything)
6. I can only ping other hosts if I specify routing to bypass the vpn, but then what's the point? I want internet traffic to go over vpn
7. I'm using openvpn latest version, with tcp connection and a tun interface, and shared secret key, and static ip for both sides of the vpn tunnel (no dhcp over vpn, only one client for vpn, this is all I need)
8. please do NOT tell me to run iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE on the server, I tried this twice (including once on another test server) and the server becomes instantly unresponsive to everything, ping, all ports, etc. and then I need to wait for the servers to be rebooted, I think that command interferes with incoming requests or something, I must have ssh access and other servers able to run, this is a server with services other than vpn running like ssh, it CANNOT be a vpn-only server
9. there is no firewall running on the server, on my system I have so simple iptables rules for INPUT only, I tried disabling those and same thing, so it's almost certainly not a firewall problem. also ran ifconfig on server and there was a tun interface on both server and me

I would like a detaied, step-by-step tutorial on how to configure both server and client for internet access with openvpn
Also, server is normal linux server, it's not a router or something, it's a regular server

---

### Post by gombadi on 2009-11-09
> 
Can someone please give a detailed tutorial on setting up openvpn on a server for secure internet surfing


Is web surfing the main purpose of the vpn link? If so then can you use apache as a reverse proxy on the dedicated server?

I have a VPN connection to my dedicated server (mainly to provide my own ipv6 tunnel) but I also have apache configured to listen on the tunnel interface and proxy connections to the world. I then set my local Firefox to use the remote http proxy and connections go over the vpn to the dedicated server and then off to the world.

You are already able to ping to each end of the tunnel so no further changes will be needed.

> 
8. please do NOT tell me to run iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE on the server


There are other solutions available but I am not able to tell you what they are :-)

---

### Post by koenn on 2009-11-09
Your vpn seems to work, so you don't need an openvpn tut.
It sounds like you have routing issues. 

I don't quite get what you are trying to do, so you'll have to explain that more clearly in order to see what  you require in terms of routing.

Something like: you want to browse the internet (from your PC) but all traffic should go through the tunnel and that server on the other and acts as your gateway to the internet ? 

(and, out of curiosity, why ?)

---

### Post by kevdog on 2009-11-09
SpaceTeddy is a forum user who has great knowledge about this type of question.  Possibly try to get a hold of him.

---

### Post by network2180 on 2009-11-09
ok, here's the problem
1. yes it's a routing issue, not with openvpn as I can succesfully connect
2. I don't know how to configure this routing
3.from the openvpn sample server config file:

# If enabled, this directive will configure
# all clients to redirect their default
# network gateway through the VPN, causing
# all IP traffic such as web browsing and
# and DNS lookups to go through the VPN
# (The OpenVPN server machine may need to NAT
# or bridge the TUN/TAP interface to the internet
# in order for this to work properly).
;push "redirect-gateway def1 bypass-dhcp"

the problem is how do I connect the TUN interface to the internet. I tried playing with route and counldn't find a solution, and then iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE killed the servers connection  the server is not nat or anything, it has a public ip on the internet and no firewall, so that isn't the problem

also I need openvpn, I said surfing but it's not just http, it's also dns, im, and lots of other tcp and sometimes udp protocols, and some apps have poor/no proxy support

>There are other solutions available but I am not able to tell you what they are

anyone who can tell me a solution for routing to internet without iptables?

here is basically what I want:
my system -> isp (often with nat router) -> openvpn server -> internet
and I want all internet traffic  to go over the vpn tunnel to internet, only problem is how to configure routing on my system/server to do this without preventing anyone on the internet from being able to connect to other services running on the server

---

### Post by koenn on 2009-11-09
and the vpn client on your side runs on your PC, right ? not on some other machine.

---

### Post by koenn on 2009-11-09
> **network2180 said:**
> 
1. yes it's a routing issue, 

let's see what your routing looks like :
run this on both the server and your pc, and post the output :

```
route -n
```


Depending on how you're set up (see question in my previous post), this could just be a matter of getting the default gateways right.
In that case, removing the ";" in front of 'push "redirect-gateway def1 bypass-dhcp"' and restarting openvpn might be sufficient.

---

### Post by EJeanmaire on 2009-11-09
I'm by no means a pro at OpenVPN, but are you running the vpn service with privileges / does it have access to networking interfaces?  Just a shot in the dark...

> **network2180 said:**
> Can someone please give a detailed tutorial on setting up openvpn on a server for secure internet surfing? Here is my problem:
1. I have ubuntu linux installed on my system
2. I have ssh access (root ssh) on a dedicated server. I have ONLY ssh access (NOT physical access) but can install anything I want on it (including any other service I want), I can use ssh tunnel but it has limitations so I need openvpn
3. I have the latest openvpn on my system and remote server (I can ping both 10.4.0.1 and 10.4.0.2, and make tcp connections over the server to services running on the server)
4. I successfully configured openvpn on both my system and server to the point where I can ping both sides of the tunnel.
5. When I specify routing to go over vpn tunnel interface, I can ONLY access the tunnel and the local network (since there's another route for my LAN 192.168.*.* to bypass VPN), I CANNOT ping other hosts on internet or make ANY internet traffic with them (icmp, udp, tcp: http, dns, anything)
6. I can only ping other hosts if I specify routing to bypass the vpn, but then what's the point? I want internet traffic to go over vpn
7. I'm using openvpn latest version, with tcp connection and a tun interface, and shared secret key, and static ip for both sides of the vpn tunnel (no dhcp over vpn, only one client for vpn, this is all I need)
8. please do NOT tell me to run iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE on the server, I tried this twice (including once on another test server) and the server becomes instantly unresponsive to everything, ping, all ports, etc. and then I need to wait for the servers to be rebooted, I think that command interferes with incoming requests or something, I must have ssh access and other servers able to run, this is a server with services other than vpn running like ssh, it CANNOT be a vpn-only server
9. there is no firewall running on the server, on my system I have so simple iptables rules for INPUT only, I tried disabling those and same thing, so it's almost certainly not a firewall problem. also ran ifconfig on server and there was a tun interface on both server and me

I would like a detaied, step-by-step tutorial on how to configure both server and client for internet access with openvpn
Also, server is normal linux server, it's not a router or something, it's a regular server

---

### Post by network2180 on 2009-11-10
> 			 		   		 		 		I'm by no means a pro at OpenVPN, but are you running the vpn service with privileges / does it have access to networking interfaces? Just a shot in the dark...

no, I'm running all commands with root privileges

anyway I found this, seems like a good tutorial and may try it:
[http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu](http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu)

it uses iptables, but hopefully the -s 10.8.0.0/24 will stop problems****

---

### Post by network2180 on 2009-11-10
can someone please explain exatly what this command does:
**sudo iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE**

It's part of a openvpn tutorial at [http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu](http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu)
as I understand it, it enables packet forwarding from ips on 10.8.0.0/24 to the general internet out on the ethernet port
some questions:
1. can I safely run this command from an ssh shell without problems like disconnecting me?
2. will this command interfere with any non-vpn traffic, including while the vpn session is active? so if I have both openvpn servers and an http server running on the same server, will the http server be always publically accessible, even when I am using the vpn?

---

### Post by network2180 on 2009-11-11
bump
can anyone help please

---

### Post by network2180 on 2009-11-11
I created another thread ([http://ubuntuforums.org/showthread.php?p=8294449](http://ubuntuforums.org/showthread.php?p=8294449)) about iptables, the iptables seems to be the thing I need to configure

---

### Post by koenn on 2009-11-11
it changes the source IP address in IP packets with a source address in the network  -s 10.8.0.0/24 to whatever the IP address is of eth0 on the host where this command is run (and keeps track of the changes so reply-packets will have their destination address modified accordingly)

---

### Post by network2180 on 2009-11-11
ok thanks
one problem: will other packets be redirected through the 10.8.0.0/24 network? so if I have a http server on the system, and I run this command, will users on the internet still be able to access the http server, or will their packets/answers to those packets be redirected to 10.8.0.0/24?

---

### Post by koenn on 2009-11-11
that statement will only affect connections originating (according to their src address) from 10.0.8.0/24

---

### Post by cariboo on 2009-11-11
Please don't double post on the same subject, I have merged your threads.

---

