---
title: "Gigabit networking issues"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by CodeRedOnly on 2009-05-17
I'm currently running Ubuntu 8.04 server edition.  About a week ago, I bought a gigabit switch to speed up internal network transfer speeds.  All of the other computers work fine through the gigabit switch, but my Ubuntu server does not.  When I try to ping my router, I get "Destination Host Unreachable" responses.  If I put my old 10Mbps switch back in place, everything works O.K., but it drops about 1/3 of the packets.

This weekend, I bought a gigabit nic, figuring I something was wrong with the old card, but this one works exactly the same.  Any ideas?

---

### Post by puppywhacker on 2009-05-17
you can check (or set) the line speed
```
sudo mii-tool eth0
```

any kernel messages about your nic should be logged to the messages file
```
tail -50 /var/log/messages
```
or
```
dmesg
```

then also investigate the type of card you have and which driver you are using (it may need some parameters)
```
lspci
lsmod
```

---

### Post by superprash2003 on 2009-05-18
you probably just not getting an ip address.. post an output of ifconfig fromt the terminal

---

