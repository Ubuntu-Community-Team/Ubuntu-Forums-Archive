---
title: "Setting a Static IP in Jaunty"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by JagDragon on 2009-08-03
Hey everyone,

I was wondering about the best way to go about setting a static IP in Ubuntu 9.04 (Jaunty). At the moment I have set a static IP interface (my only interface) using network-manager (as in going through the menus by clicking the top-right screen network icon), and I have a static IP which is working.

But.

As network-manager only activates when I log in, I cannot have my computer sitting on the login screen and have an IP (I need this for ssh and such). 

Is it possible to set a static IP in /etc/network/interfaces that does not access the internet, and an IP using network-manager that does access the internet?

Thanks,
Jag

---

### Post by jamest09 on 2009-08-03
```
auto eth0
iface eth0 inet static
        address 192.268.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255

```

---

### Post by JagDragon on 2009-08-03
I'm asking to have a static IP that is not connected to the internet that loads when my computer does, and a dynamic IP that loads when I log in, via network-manager. What you have given me there is an always-on internet static IP...

---

### Post by Qu4rk on 2009-08-04
> **JagDragon said:**
> At the moment I have set a static IP interface (my only interface) using network-manager (as in going through the menus by clicking the top-right screen network icon), and I have a static IP which is working.

Jag...can you explain how you did this?  I'd like to add another eth0 that is static so I can switch between static & DHCP via menu.  

Thanks

---

