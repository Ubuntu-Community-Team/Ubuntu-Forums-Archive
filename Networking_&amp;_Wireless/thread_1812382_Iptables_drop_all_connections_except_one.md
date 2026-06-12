---
title: "Iptables drop all connections except one"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by fakevilg on 2011-07-26
Hey ! 

Can some1 help with iptables rules , ive got netbook with gsm modem .. i need to block all connections except one domain .

//edit


iptables -P INPUT DROP 
iptables -A INPUT -s [www.example.org](www.example.org) -j ACCEPT 


is it right ?

---

### Post by newbie-user on 2011-07-27
Iptables rules are executed top to bottom, so your drop rule should be last.  I've never tried iptables with domains, though, so I'm not exactly sure how to specify the domain.  See the two lines that follow:

   iptables -A INPUT -p tcp -s [www.example.org](www.example.org) -j ACCEPT
   iptables -A INPUT -i [gsm modem interface] -j DROP


iptables is the command, -A means to append, INPUT means incoming connections, -p tcp specifies tcp protocol, -s is from what source, -j is what iptables does with the packet if it matches the rule, and ACCEPT/DROP is accept or drop packet.

---

### Post by fakevilg on 2011-07-27
hmmmmm ive blocked whole internet when i run this in script :P 

any1 has any suggestions ? :)


//edit 

i found solution - redirect all http request to my host :)

```
 iptables -t nat -A OUTPUT -p tcp -j DNAT --to 22.22.22.22 
```

---

