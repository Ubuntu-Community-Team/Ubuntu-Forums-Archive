---
title: "Iptables port forwarding"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by ApEkV2 on 2010-10-25
Hello there, I have two ethernet cards eth0 and eth1, in where the Internet connection on eth0 is shared with eth1.
I'm having a problem forwarding tcp 80 to my web server on eth1.
The commands I used to share the connection are as follows:
```
sudo ifconfig eth1 192.168.0.1
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo iptables -A FORWARD -i eth1 -p tcp --dport 80 -j ACCEPT
sudo iptables-save
```

Here is the setup:
```
Router address:             192.168.1.1
|___Forwards tcp 80 to:     192.168.1.105

Computer eth0:              192.168.1.105    Static
Computer eth1:              192.168.0.1      Static

Server eth0:                192.168.0.110    Static
|___Gateway:                192.168.0.1
|___DNS:                    192.168.0.1

Mask:                       255.255.255.0
```

I have installed dnsmasq and set IP forwarding to true on the computer.

I am able to access the Internet from the web server, but the server is not accessible from the Internet.
My goal is to have the web server accessible by the Internet, if anyone could help me out I would appreciate it.

Here is the output from iptables -L
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by ApEkV2 on 2010-10-26
I confirmed with wireshark that requests from the Internet don't make it to the server.
The Computer receives requests but replies with rst acks so in effect there is no forwarding happening.

---

### Post by SeijiSensei on 2010-10-26
The FORWARD rule chain just controls permission for packets to be forwarded; it doesn't do any actual forwarding itself.  In fact, since the default FORWARD policy is ACCEPT, that rule doesn't do anything at all.

I think what you want is a NAT rule like this:
```

sudo iptables -t nat -A PREROUTING -i eth0 --dport 80 -j DNAT --to-destination 192.168.0.1:80
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```

The first rule takes traffic arriving on eth0 for port 80 and sends it unmangled to port 80 on 192.168.0.1.  See if that helps.

---

### Post by ApEkV2 on 2010-10-26
The first command you listed doesn't work, it says unknown option --dport.
I fixed it with what I think you meant.
```
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 192.168.0.1:80
```
It still doesn't work though, I'm still able to access the Internet from the server, but not the other way around.
But thanks for your reply.

---

### Post by ApEkV2 on 2010-10-28
2nd day bump. I need to get this to work.

---

### Post by ryanczak on 2010-10-28
I have a large iptables script that does a lot of port forwarding to various internal servers. 

Something like this works in my configuration:

```
$IPTABLES -t filter -A FORWARD -p tcp -d 192.168.1.105  -j ACCEPT
$IPTABLES -t filter -A FORWARD -p tcp -s 192.168.1.105  -m state --state ESTABLISHED,RELATED -j ACCEPT
 
$IPTABLES -t nat -A PREROUTING -i $INTERNETIF -p tcp -d $INTERNETIP --dport 80 -j DNAT --to-destination 192.168.1.105:80

```

You need to have NAT working for the internal server but it sounds like you do already. 

Also make sure ip forwarding is enabled:

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

---

