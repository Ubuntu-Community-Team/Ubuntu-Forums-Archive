---
title: "openSSH: No route to host"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by roband915 on 2011-12-14
My network at home is extremely basic. A router(Asus rt-n56u) and a server(Ubuntu server 11.10). All i did was installing Ubuntu server from scratch. Then I installed openSSH and that's it! Now here's the problem. When I use a laptop to connect to the server from inside the network everything works fine. But when I try to connect to the server externally I get "No route to host". I've tried everything and nothing works! Does anybody have any idea what the problem can be?

/Robert

---

### Post by jonobr on 2011-12-14
Are you port forwarding ssh on your router to the openssh server?

Can you ping or tracert to get to your own router from outside?

A lot of providors block port 22, but I get the feeling thats not happening in your case.

---

### Post by roband915 on 2011-12-14
Yes the port forwarding is done so shouldn't be a problem.
I tried traceroute but got a !H which means the host is unreachable?
I think the problem is on the server. It acts like it doesn't accept anything that comes outside the network. Iptables has no rules yes so it shouldn't be a problem I guess? The weird thing is this. If I fire upp my old nas(Seagate blackarmor 220) and try access it externally it works fine. 
Can it be a hardware issue with the network-card on the server?

---

### Post by jonobr on 2011-12-14
open a terminal on the server

type 
```
sudo tcpdump -i any -vvv -s 1600 port 22
```

It will monitor network packets at this point./

Do your ssh'ing.

If you get output above its hitting

if you get a packet going back its replying

---

### Post by roband915 on 2011-12-14
I get nothing I'm afraid. What does this mean? Does it mean that my router doesnt't work correctly or can it still be the server?

---

### Post by roband915 on 2011-12-14
I got it! I didn't know that ssh needed port 23?! But when I forwarded port 23 it worked!

---

### Post by hyper2hottie on 2011-12-14
Just a thought.  Are you using your external ip address to try ssh or are you using the one the router assigned to your server.  You will need the external ip.

---

### Post by jonobr on 2011-12-14
Hey just to correct you, if I could

ssh uses port 22,

telnet uses port 23

SSH is the secure form of telnet and replaces it,.

If your connecting via 23, your telnetting and its not secure, unless you change d the port for telnet

---

### Post by roband915 on 2011-12-14
That's what I thought also. All I did was forward ports "22:23" to my server. Then it worked. I still ssh to the server on port 22. I'm not understanding this at all... How can I connect to a computer using port 22 and tell my router to forward this port and nothing works until i also forward port 23....Which isn't in use!

---

### Post by CharlesA on 2011-12-14
Port 22 could be blocked by your ISP.

---

### Post by roband915 on 2011-12-15
Let's assume that port 22 is closed by my ISP. Does this mean that putty automatically tries port 23 when 22 is failing? 

I still don't see how this really is possible. I can connect to my server but I don't know how.

---

### Post by Lars Noodén on 2011-12-15
You can test if your ISP is blocking port 22 with tools like this one:
[http://canyouseeme.org/](http://canyouseeme.org/)

---

### Post by CharlesA on 2011-12-15
> **roband915 said:**
> Let's assume that port 22 is closed by my ISP. Does this mean that putty automatically tries port 23 when 22 is failing? 

I still don't see how this really is possible. I can connect to my server but I don't know how.

Putty only connects to whatever port you tell it to connect to.

---

### Post by roband915 on 2011-12-15
Well the port 22 seems to be open. It must be the router then I guess. Thanks for the help!!

---

