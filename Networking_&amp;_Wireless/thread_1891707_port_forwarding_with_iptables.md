---
title: "port forwarding with iptables"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2011-12-06
I've got network address translation set up with IPTables:
```
   iptables -t nat -A POSTROUTING -o eth4 -j MASQUERADE

```

How do I go about forwarding port 80 from the external IP address to one of the internal ones?

---

### Post by Lars Noodén on 2011-12-08
Bump

---

### Post by Lars Noodén on 2011-12-08
I figured it out finally.

```

iptables -t nat -A PREROUTING -p tcp -i $EXTIF -d $EXT  \
     --dport 80 --sport 1024:65535 -j DNAT --to $INT:80

iptables -I FORWARD -p tcp -i $EXTIF -o $INTIF -d $INT \
    --dport 80 --sport 1024:65535 -m state --state NEW -j ACCEPT

iptables -I FORWARD -t filter -o $EXTIF -m state \
         --state NEW,ESTABLISHED,RELATED -j ACCEPT

iptables -I FORWARD -t filter -i $EXTIF -m state \ 
         --state ESTABLISHED,RELATED -j ACCEPT

```

From [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables)

---

