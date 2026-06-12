---
title: "Static IP in computer lab"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by gforster on 2009-08-12
OK. . .I think I almost have this, but need a little help.

I am putting the finishing touches on our computer lab for school. One of the areas I am having a little trouble with is static ips. I have ~30 computers running 9.04. Right now, they are DHCP (just the default when I set them up). There is a W2K3 server that assigns a domain of lab.org and DNS of 10.0.***.* I have also found the proper gateway address. 

What I want is for computer #1 to have an IP of 10.0.***.101, computer #2 to have an IP of *.102, etc. This way, with my pub/priv keypairs it will make it easier to manage everything. 

The problem I have is that when I assign *.101 to computer 1, because of the DHCP, the computer that had *.101 is still active and computer 1 doesn't connect to the internet. 

What am I missing? My guess is that it is something quite simple. Usually is with me.

---

### Post by jonobr on 2009-08-12
What has the task of assigning the IP addresses?

That device needs to be able to reserve the IP addresses used for static allocation.
Once thats done you need to get the computer with allocated static IP to reboot and get another IP that is not in your static IP pool.

If whatever is doing your DHCP does not have the ability to restrict IPs from being handed out, then you need to reduce your scope where eg DHCP allocates from 10.10.1.2 to 10.10.1.100 and this is defined in your DNS and then 101 to 254 are statics that are used on your static machines.

If your reduce your scope size you may still need the other computers to reobtain an IP address thats in the pool

I do however feel I may have misunderstood the requirement

---

### Post by gforster on 2009-08-12
Yes, you did miss what I was asking for, but your informative post really helped me overcome a hurdle along the way - thank you. 

However, I have (for the most part) accomplished my goal! I have one other problem,  but will start a new thread so as not to get anything confused.

---

### Post by jonobr on 2009-08-12
Hello


Good to hear, 
Ill watch for your other post, , misread that and comment on it to.

:-)

---

### Post by Iowan on 2009-08-12
Probably too late for inclusion, but a *static lease* based on MAC address would probably work... assuming the DHCP server is capable.

Guess I'll look for the next thread.

---

### Post by jonobr on 2009-08-12
Good point also Iowan.

In DHCP3 server and in microshafts DHCP implementation you can assign the mac to an IP to make sure its always given to the same machine, however, would it be right to say that it is still DHCP and not a statically assigned IP address at that point

---

### Post by lisati on 2009-08-12
> **Iowan said:**
> Probably too late for inclusion, but a *static lease* based on MAC address would probably work... assuming the DHCP server is capable.

Guess I'll look for the next thread.

That's similar to what I was thinking. I normally have my main router to assign IP addresses that are associated with a particular MAC address. It might be necessary to do what Windows would call ipconfig /relase and ipconfg /renew if you change the allocation while the machine is connected. (The Ubuntu equivalent eludes my memory at the moment, aaargh!)

---

### Post by jonobr on 2009-08-12
hello

to release the lease its 

```
sudo dhclient -r
```

to renew its

```
sudo dhclient
```

---

### Post by Iowan on 2009-08-12
> **jonobr said:**
>  however, would it be right to say that it is still DHCP and not a statically assigned IP address at that point It's managed by DHCP server, so I call it a "lease" although it's also "static". If DHCP server fails, the machine won't get an address. (maybe arguable...). A static lease also benefits by retrieving DNS server info, gateway, etc., from DHCP server... just like other DHCP clients.

It's also worth mentioning that a static lease address should be *outside* the DHCP server's address pool.

---

