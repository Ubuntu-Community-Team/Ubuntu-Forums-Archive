---
title: "using iptables to change a destination port but keep the ip the same."
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by leftler on 2010-03-23
I am playing around with transparent proxies, The current way I am doing things is the program makes a request  to a computer on port 80, I use
```
iptables -t nat -A OUTPUT -p tcp --destination-port 80 -j REDIRECT --to-port 1234
```
to redirect to my proxy that I am playing with. the proxy will send out a request to port 81 (as all outbound port 80 are being fed back in to the proxy) so I want to do something like
```
iptables -t nat -A OUTPUT -p tcp --destination-port 81 -j DNAT --to-destination xxxx:80
```
The problem lies with the xxxx part. How do I change the destination port without changing changing the destination ip? Or am I doing this setup completely wrong, I am learning after all and constructive criticism is definitely appreciated.

---

### Post by heatblazer on 2010-03-23
Interesting... thank you for the sharing.

---

### Post by leftler on 2010-03-23
I was not sharing a solution, I was asking a question. What do i put in the xxxx part to make this work?

---

