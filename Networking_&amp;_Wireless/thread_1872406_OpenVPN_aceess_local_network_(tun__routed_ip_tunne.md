---
title: "OpenVPN aceess local network (tun / routed ip tunnel)"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by peerus on 2011-10-30
Hi, could anyone help me. I've spent whole day trying to figure out how to connect to OpenVPN server and get access to local network resources.

OpenVPN is running on machine, that acts as router for internet access. The router has 2 physical ethernet cards:
eth0 - internet access
eth1 - local area network 192.168.2.0/255.255.255.0

I can access server via intenet address, vpn address (10.10.2.1) and local network address 192.168.2.1
I can ssh, ping etc. but i can't comunicate any machine on local network, for example 192.168.2.50

here is server config
```

port 1194
proto tcp
dev tun

ca ca.crt
cert server.crt
key server.key
dh dh1024.pem

server 10.10.2.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.2.0 255.255.255.0"

keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3

```

---

### Post by peerus on 2011-10-31
anybody?

---

### Post by jonobr on 2011-10-31
I wonder is it to do with IP forwarding needing to be enabled?

```
cat /proc/sys/net/ipv4/ip_forward
```

if it returns 0, try setting it to one

If mem serves its 

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

---

### Post by peerus on 2011-10-31
jonobr, thanks for answer!

cat /proc/sys/net/ipv4/ip_forward returns 1. it's akay. server already acts as router.

i've changed some config options
```

proto udp
route 192.168.1.0 255.255.255.0
push "route 192.168.2.0 255.255.255.0"
client-config-dir ccd

```

ccd contains
```

iroute 192.168.1.0 255.255.255.0

```

trace from server to client (looks good)
```

$tracepath 192.168.1.100
 1:  10.10.2.1                                             0.674ms pmtu 1500
 1:  192.168.1.100                                        44.124ms reached
 1:  192.168.1.100                                        43.693ms reached
     Resume: pmtu 1500 hops 1 back 64 

```

trace from client to server (looks good)
```

tracepath 192.168.2.1
 1:  10.10.2.6                                             0.166ms pmtu 1500
 1:  192.168.2.1                                          31.970ms reached
 1:  192.168.2.1                                          31.167ms reached
     Resume: pmtu 1500 hops 1 back 64 

```

trace from client to resource on server local network. here i have some problem. have no idea why.
192.168.2.50 is pingable from server
```

tracepath 192.168.2.50
 1:  10.10.2.6                                             0.238ms pmtu 1500
 1:  10.10.2.1                                            33.992ms 
 1:  10.10.2.1                                            33.560ms 
 2:  no reply
 3:  no reply
 4:  no reply
 5:  no reply

```

---

### Post by jonobr on 2011-10-31
Close but no cigar as they say :)

I notice that in your OP you didn't mention the network 192.168.1.x
You did mention 192.168.2.x?

How does the first address fit in? Is that intentional?

---

### Post by peerus on 2011-10-31
192.168.1.X is my home network from where i'm trying to get access to office net. 192.168.1.100/255.255.255.0 is my local address at home. 192.168.1.1 is router

Whole thig looks like this:
1. home network 192.168.1.0/255.255.255.0 gw 192.168.1.1
2. office network 192.168.2.0/255.255.255.0 gw 192.168.2.1
3. vpn 10.10.2.0/255.255.255.0

i'm trying to get connection to local resources on 192.168.2.X through vpn tunnel
server and client communicates well. But:
1. can't ping 192.168.2.50 from 192.168.1.100
1. can't ping 192.168.1.1 from 192.168.2.1

PS: this set up is way to keep brain in good shape :) or damage it..

---

### Post by peerus on 2011-10-31
Solution was found! take a look here [https://forums.openvpn.net/post17140.html](https://forums.openvpn.net/post17140.html)

---

