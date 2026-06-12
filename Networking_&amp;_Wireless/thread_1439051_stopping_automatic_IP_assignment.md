---
title: "stopping automatic IP assignment"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by jum1 on 2010-03-25
Hello,how do I stop my Kubuntu to set up an IP ? I tried this:
sudo ifconfig eth0 192.168.0.1
but in the following minutes it changes it!
how do I stop it?
jum1

---

### Post by chili555 on 2010-03-25
Isn't 192.168.0.1 the IP address of your router? I rather imagine your rooter is kicking you off. Or are you trying to make your computer into a router?

Is Network Manager installed and running?

---

### Post by jum1 on 2010-03-26
> **chili555 said:**
> Isn't 192.168.0.1 the IP address of your router? I rather imagine your rooter is kicking you off. Or are you trying to make your computer into a router?

Is Network Manager installed and running?

Im connected to my laptop only which has its own IP
I guess there is a network manager runing but I do not know how to interact with it.

---

### Post by chili555 on 2010-03-26
> Im connected to my laptop only which has its own IPIs your laptop connected by an ethernet cable to a router or a DSL modem or what?

---

### Post by jum1 on 2010-03-26
> **chili555 said:**
> Is your laptop connected by an ethernet cable to a router or a DSL modem or what?
I am only connected to my laptop there is nothing else, it two computer linked by an ethernet cable

---

### Post by chili555 on 2010-03-26
Please try:```
sudo /etc/init.d/network-manager stop
sudo ifconfig eth0 192.168.0.1 up
```

---

### Post by skidaddy on 2010-03-26
system-preferences-network connections
under the wired tab pick interface and edit

---

