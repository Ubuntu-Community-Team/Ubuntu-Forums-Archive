---
title: "OpenVPN routing issues"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by ChromoX on 2009-05-29
I started to setup a routed openvpn server.

My network topology looks like this...

<Client> --->--- <Internet> ---->---- <Airport Extreme> --->--- <OpenVPN Server(172.16.1.0)> --->--- <Internal Network(192.168.1.0)>

I am trying to allow my Client to talk to my internal network. As of now I have no problems talking to the openvpn server, for example pinging or ftp, but I can't communicate with the internal network...

If I traceroute from a client trying to get into the internal network it just goes to the openvpn server and stops.

I do have net.ipv4.ip_forwarding enabled and my firewall configuration is about two lines.

Firewall Config:
```

-I FORWARD -i tun+ -o eth0 -j ACCEPT
-I FORWARD -i eth0 -o tun+ -j ACCEPT

```



My Server.conf:
```
# Where to listen and what port
local 192.168.1.25
port 443
# Protocols
proto tcp
# Bridge Type
dev tun

ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key
dh /etc/openvpn/easy-rsa/keys/dh1024.pem
ifconfig-pool-persist ipp.txt
server 172.16.1.0 255.255.255.0
push "route 192.168.1.0 255.255.255.0"
# Need to allow communication to internal network
client-to-client
keepalive 10 120
#Encryption
cipher BF-CBC
#For routing to another subnet
#push “route 10.0.0.0 255.0.0.0&#8243;
#Server ID protection
#tls-auth ta.key 0
#Compression for network speed
comp-lzo
#Limit number of clients
max-clients 3
#Some security settings
persist-key
persist-tun
#Log files
status /var/log/openvpn-status.log
verb 4

```

Thanks.

---

### Post by ChromoX on 2009-05-29
So I have tried several more things now without a resolution.

I tried turning the firewall completely off - Setting all the policies to allow.

---

### Post by gombadi on 2009-05-29
> If I traceroute from a client trying to get into the internal network it just goes to the openvpn server and stops.

You do not say what the ip range of the client machine is or is it the client end of the OpenVPN tunnel - i.e 172.16.1.x - We will say it is 172.16.1.2 for the example. Also you do not say, but my guess is, your vpn server is not the default gateway for the 192.168.1.0/24 network. 

If so then -

Packets from the client 172.16.1.2 will arrive at the vpn server 172.16.1.x(tun0 interface) with a destination ip address of 192.168.1.55 for example. They will have a source address of 172.16.1.2. The vpn server will send them out to the destination machine via its local eth interface.

Machine 192.168.1.55 will receive the ping packet and reply to the destination ip address of 172.16.1.2.

As 172.16.1.2 is not in the local network then 192.168.1.55 will actualy send the packet to its default gateway - assuming 192.168.1.1.

The default gateway will then send the ping reply packet up the line, probably adsl to your ISP which will drop it because it is for an internal ip range and therefore not routeable on the public Internet.

Run a tcpdump on the 192.168.1.55 or whatever ip, machine and see if you can see ping packets from the clients ip address.

How to fix - add the following to the 192.168.1.55 machine

```

sudo route add -net 172.16.1.0 netmask 255.255.255.0 gw 192.168.1.25

```

Could be wrong but worth a try. If it works then all machines in the 192.168.1.0/24 network that need to talk to the client will have to know where to send packets for the 172.16.1.0/24 network.

---

### Post by ChromoX on 2009-05-31
That is actually a very good idea. But I was wondering if I could do what I want without making any commands on the computers on the other side of the VPN. Essentially I want a routed(tun based) network compared to a bridged(tap based) network because tun is more efficient.

Is what I want possible?

---

### Post by ChromoX on 2009-06-01
Ok I got everything working I think how I would like except I don't know what I should tell IP Tables to allow this....

```

Jun  1 10:44:01 freedom kernel: [236403.926770] [UFW BLOCK] IN=eth0 OUT=tun0 SRC=192.168.1.20 DST=172.16.1.6 LEN=84 TOS=0x00 PREC=0x00 TTL=63 ID=60912 PROTO=ICMP TYPE=0 CODE=0 ID=47368 SEQ=2 

```

---

### Post by superprash2003 on 2009-06-01
i see your using UFW , install GUFW , has a GUI ,easier to configure

---

### Post by ChromoX on 2009-06-01
I am not using a GUI though....

I tried this:
```
-A FORWARD -i eth+ -o tun+ -j ACCEPT
```

But it didn't work. Does anyone else have any ideas?

---

### Post by sefs on 2009-08-11
> **ChromoX said:**
> I am not using a GUI though....

I tried this:
```
-A FORWARD -i eth+ -o tun+ -j ACCEPT
```

But it didn't work. Does anyone else have any ideas?

You would probably have to do it vice versa as well:

```

-A FORWARD -i tun+ -o eth+ -j ACCEPT

```

---

