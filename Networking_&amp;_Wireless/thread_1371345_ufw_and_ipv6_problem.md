---
title: "ufw and ipv6 problem"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by Thedjatclubrock on 2010-01-03
I'm trying to use ufw with a VPS. Using both 6to4 and a HE tunnel, ufw doesn't behave as expected. It behaves fine with ipv4, however.

IPv6 is enabled in /etc/default/ufw

When I set the default option to drop, ipv6 drops everything disregarding the rules (ipv4 works fine)

When I set the default option to accept, ipv6 allows everything, regardless of the rules I've set.

I am using the tun6to4 interface using [http://debian6to4.gielen.name/](http://debian6to4.gielen.name/)

---

### Post by Thedjatclubrock on 2010-01-03
HE Tunnel
[UFW BLOCK] IN=eth0 OUT= MAC=fe:fd:61:6b:8a:6f:00:d0:02:20:38:00:08:00 SRC=209.51.161.14 DST=xx.xxx.xxx.xxx LEN=100 TOS=0x00 PREC=0x00 TTL=23 ID=31372 PROTO=41
6to4
[UFW BLOCK] IN=eth0 OUT= MAC=fe:fd:61:6b:8a:6f:00:0e:39:6f:48:00:08:00 SRC=192.88.99.1 DST=xx.xxx.xxx.xxx LEN=86 TOS=0x00 PREC=0x00 TTL=244 ID=47185 PROTO=41

---

### Post by gombadi on 2010-01-03
PROTO=41 is the ipv6 in ipv4 tunnel packets. If you block ipv4 proto 41 packets then ipv6 will stop working.

Set a rule to allow ipv4 proto 41 packets through the firewall and then try the tests again.

---

### Post by Thedjatclubrock on 2010-01-03
> **gombadi said:**
> PROTO=41 is the ipv6 in ipv4 tunnel packets. If you block ipv4 proto 41 packets then ipv6 will stop working.

Set a rule to allow ipv4 proto 41 packets through the firewall and then try the tests again.
How? I get ERROR: Unsupported protocol '41' when I use ufw allow proto 41 from xx.xxx.xxx.xxx

---

### Post by gombadi on 2010-01-03
> 
How? I get ERROR: Unsupported protocol '41' when I use ufw allow proto 41 from xx.xxx.xxx.xxx 


Not sure how to do it in ufw - I bypass the middle man (ufw) and go straight to iptables. Off the top of my head it was -

iptables -A INPUT -p 41 -j ACCEPT

---

### Post by karit on 2010-12-18
What you want is ipv6 rather than 41 as the protocol

```
sudo ufw allow proto ipv6 from x.x.x.x
```

---

### Post by karit on 2010-12-18
I have a 6to4 and to get SSH port 22 available over ipv6

```

sudo ufw allow proto ipv6 to <the servers ipv4 address>
sudo ufw allow to <the servers ipv6 address> port 22

```

First ***mand allows ipv6 wrapped stuff to ***e in on the ipv4 address so the tunnel can see it
The second ***mand allows ipv6 to ssh. 

Also makes sure that SSH, Apache are listening on ipv6 as well. a netstat -an will show you if they are not

---

