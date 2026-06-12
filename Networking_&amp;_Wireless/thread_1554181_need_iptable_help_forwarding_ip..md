---
title: "need iptable help forwarding ip."
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by ulao on 2010-08-16
I have a eth0 ( outside ip ) with a eth0:1 ( lan ip/192.168.0.x ) I want to take all 8080 traffic from out side and direct it to 192.168.0.21:8080

I tried

```
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 8080 -j DNAT --to 192.168.0.21:8080

```
and figured I may need 

```
iptables -A FORWARD -p tcp -i eth0 -d 192.168.0.21 --dport 8080 -j ACCEPT
```

but its not working. What did I do wrong?

---

### Post by ulao on 2010-08-16
I have a eth0 ( outside ip ) with a eth0:1 ( lan ip/192.168.0.x ) I want to take all 8080 traffic from out side and direct it to 192.168.0.21:8080

I tried

```
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 8080 -j DNAT --to 192.168.0.21:8080

```
and figured I may need 

```
iptables -A FORWARD -p tcp -i eth0 -d 192.168.0.21 --dport 8080 -j ACCEPT
```

but its not working. What did I do wrong?

----- is there a trick to get this to post in  
"Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories  > Networking & Wireless" , it does not show up?-----

---

### Post by ulao on 2010-08-16
Sorry about the category but networking will not show my posts?
---------------------------------------------------------------




I have a eth0 ( outside ip ) with a eth0:1 ( lan ip/192.168.0.x ) I want to take all 8080 traffic from out side and direct it to 192.168.0.21:8080

I tried

```
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 8080 -j DNAT --to 192.168.0.21:8080

```
and figured I may need 

```
iptables -A FORWARD -p tcp -i eth0 -d 192.168.0.21 --dport 8080 -j ACCEPT
```

but its not working. What did I do wrong?

---

### Post by cariboo on 2010-08-16
Merged 3 threads on the same subject

---

