---
title: "opening collaboration port 443"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by spoilingmyself on 2009-08-05
hi 
i am a new user of ubuntu 8.04 hardy and i dont know how to open the collaboration port 443 for communication... please tell me
thanks in advance

---

### Post by Crafty Kisses on 2009-08-05
It might go something like this:
```
iptables -A INPUT -p tcp -s 0/0 --sport 443 -d $SERVER_IP --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
```
That's how your iptables configuration should look like if you want port 443 open.

---

### Post by spoilingmyself on 2009-08-06
> **Codename said:**
> It might go something like this:
```
iptables -A INPUT -p tcp -s 0/0 --sport 443 -d $SERVER_IP --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
```That's how your iptables configuration should look like if you want port 443 open.
hey thanks but when i wrote this command on the terminal it said bad argument 1024:65535. can u pls explain what all changes i should make to have it work.:confused:

---

### Post by spoilingmyself on 2009-08-07
> **spoilingmyself said:**
> hi 
i am a new user of ubuntu 8.04 hardy and i dont know how to open the collaboration port 443 for communication... please tell me
thanks in advance
i wanted to tell you all that ie6 on the same machine is working absolutely fine and shows that port 443 is open but ff shows it is closed and the page continuously keeps logging in and is not able to connect. one more thing the page is not https. other https pages are displayed properly. i have tried opening port 443 using the iptables command but it doesnot help. 
iptables -A INPUT -p tcp --dport 443 -j ACCEPT

any help will highly appreciated...

---

### Post by cariboo on 2009-08-07
Do you have apache2 setup and running?

---

### Post by spoilingmyself on 2009-08-09
> **cariboo907 said:**
> Do you have apache2 setup and running?
no i dont have apache running.

---

