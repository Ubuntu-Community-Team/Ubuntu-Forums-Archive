---
title: "redirect web traffic from a specific IP to 8118 using iptables"
date: 2012-03-23
forum: Networking &amp; Wireless
---

### Post by deadtom on 2012-03-23
I have a small home network with about 8 PCs. I have privoxy setup and running on the gateway machine. I want to do a transparent proxy with only two machines on the network.

So what I want to do is redirect traffic coming from a specific IP on the LAN, from port 80 to port 8118 so that it goes through privoxy.

I can't seem to find a clear explanation for how to do this. Here is what I have in iptables.rules, but it's not working.

```
-A PREROUTING -d 192.168.58.3/32 -p tcp -m tcp --dport 80 -j REDIRECT --to-port 8118 
```

Thanks!

---

### Post by deadtom on 2012-03-26
Bump?

---

### Post by cybpabeofm on 2012-03-26
bump

Could you give us more info? Do both of the machines run linux? Whats their hardware and what drivers are you using?

---

### Post by collisionystm on 2012-03-26
You need to paste ALL of the following into your iptables.

```
*nat
:PREROUTING ACCEPT [0:0]
-A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8118
COMMIT
```


should work like a charm.


EDIT:

Stupid smiley. Its a colon : and a capital P where the smiley is.

---

### Post by deadtom on 2012-03-26
> **collisionystm said:**
> You need to paste ALL of the following into your iptables.


I do have :PREROUTING [0:0] and COMMIT in there. Also, I just want this to apply to traffic coming from a specific IP inside the network, not the entire network.

---

### Post by collisionystm on 2012-03-26
> **deadtom said:**
> I do have :PREROUTING [0:0] and COMMIT in there. Also, I just want this to apply to traffic coming from a specific IP inside the network, not the entire network.


*nat
:PREROUTING ACCEPT [0:0]
-A PREROUTING -s 192.168.1.5 -p tcp --dport 80 -j REDIRECT --to-port 8118
COMMIT


Replace 192.168.1.5 with whatever the IP is. Enjoy.

---

### Post by collisionystm on 2012-03-26
Just noticed your original line...

-A PREROUTING -d 192.168.58.3/32 -p tcp -m tcp --dport 80 -j REDIRECT --to-port 8118

you have here that 192.168.58.3 is the destination IP... thats what the -d indicates. It needs to be the -s meaning its the source.

---

### Post by deadtom on 2012-03-26
> **cybpabeofm said:**
> Could you give us more info? Do both of the machines run linux? Whats their hardware and what drivers are you using?

Well they are both running Ubuntu, all of the PCs in the house are however, their configurations are completely irrelevant. I'm wanting to make changes to the firewall that these machines go through to get out to the internet.

---

### Post by deadtom on 2012-03-26
> **collisionystm said:**
> Just noticed your original line...

-A PREROUTING -d 192.168.58.3/32 -p tcp -m tcp --dport 80 -j REDIRECT --to-port 8118

you have here that 192.168.58.3 is the destination IP... thats what the -d indicates. It needs to be the -s meaning its the source.

This fixed it. Thanks!

---

### Post by collisionystm on 2012-03-26
> **deadtom said:**
> This fixed it. Thanks!



No problemo dude.

Not sure what firewall you are using, UFW is pretty easy.

You just add your custom rule, such as this one, to /etc/ufw/before.rules

UFW is nice.

---

