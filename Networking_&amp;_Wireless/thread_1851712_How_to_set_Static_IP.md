---
title: "How to set Static IP"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by parkerskouson on 2011-09-28
Couldint find anything that made sense. How do you make a static ip on 11.04. The gateway is 192.168.2.1. 
Any help appreciated 

Parker

---

### Post by dankdave on 2011-09-28
> **parkerskouson said:**
> Couldint find anything that made sense. How do you make a static ip on 11.04. The gateway is 192.168.2.1. 
Any help appreciated 

Parker

Someone chime in if I'm completely wrong, but doesn't this depend on your router?

---

### Post by dankdave on 2011-09-28
> **dankdave said:**
> Someone chime in if I'm completely wrong, but doesn't this depend on your router?

Sorry about that hasty response.  Look at /etc/network/interfaces.  You can read the man pages with 'man interfaces', and add a line such as

```

iface eth0-home inet static
            address 192.168.1.1
            netmask 255.255.255.0

```

---

### Post by parkerskouson on 2011-09-28
ya. but dont i have to edit the wireless connection

---

### Post by daniel.p on 2011-09-28
> **parkerskouson said:**
> ya. but dont i have to edit the wireless connection

Are you talking about editing router settings? You shouldn't have to. The only thing I've ever done when it comes to assigning a static IP is log in to my router's settings page, figure out what IP will most likely never be assigned automatically by the router (i.e. 192.168.0.169), and then use that. Everything else was done from the PC itself.

---

