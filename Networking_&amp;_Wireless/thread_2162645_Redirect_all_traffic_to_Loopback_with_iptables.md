---
title: "Redirect all traffic to Loopback with iptables"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by altaf123 on 2013-07-15
Hello ALL.......!

I am trying to redirect the traffic on the tun0 interface to loopback and I request you to guide me.

I have a tun0 interface and a when a client with an IP of 192.168.254.2 (coming from tun0) wants to access the Internet I do 

$ iptables -A POSTROUTING -s 192.168.254.2 -t nat -o wlan0 -j MASQUERADE

and the client successfully connects to the Internet over WIFI.


Now instead of wlan0 I want to redirect all traffic coming from tun0 to Loopback on which I am running a BIND DNS server and also a lighttpd Webserver. I tried with few rules but failed to do so. Can you guide me with the right rule.

regards,

Altaf

---

### Post by Joe Ker1086 on 2013-07-15
I am not positive if this will work.... but give it a try. Be sure to make a backup of your iptables.

```
iptables -I POSTROUTING -o tun0 -s 127.0.0.1 -j MASQUARADE
```

---

### Post by altaf123 on 2013-07-16
> **Joe Ker1086 said:**
> I am not positive if this will work.... but give it a try. Be sure to make a backup of your iptables.

```
iptables -I POSTROUTING -o tun0 -s 127.0.0.1 -j MASQUARADE
```


Thank you fr your reply..But it didnt work..

It says  " iptables: No chain/target/match by that name."

I have the tun0 up and running.


regards,

Altaf

---

### Post by newbie-user on 2013-07-16
> **altaf123 said:**
> 
It says  " iptables: No chain/target/match by that name."


Remember to specify which table to insert into:
```
iptables -I POSTROUTING -t nat -o tun0 -s 127.0.0.1 -j MASQUARADE
```

---

### Post by SeijiSensei on 2013-07-16
I'm not sure if you can redirect the entire interface, but you can redirect specific ports like this:

```

/sbin/iptables -t nat -A PREROUTING -i tun0 -p udp --dport 53 -j REDIRECT
/sbin/iptables -t nat -A PREROUTING -i tun0 -p tcp --dport 80 -j REDIRECT

```

By default, REDIRECT sends traffic to 127.0.0.1 and the same port as specified in the rule.  See "man iptables" for details.

---

