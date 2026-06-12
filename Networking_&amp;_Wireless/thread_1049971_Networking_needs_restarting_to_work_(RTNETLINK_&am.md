---
title: "Networking needs restarting to work (RTNETLINK &amp; SIOCDELRT)"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by matt91 on 2009-01-25
I have recently restored an ubuntu backup since my old root drive died. This is now working fine except from networking.

When I start up the machine connections to/from it don't work, I have to restart networking for it to then work, this is what i get upon doing this:

```
server@localhost:~$ sudo /etc/init.d/networking restart
[sudo] password for server: 
 * Reconfiguring network interfaces...                                          
RTNETLINK answers: No such process
SIOCDELRT: No such process
                                                                         [ OK ]
server@localhost:~$ 
```

I thought this was just going to happen on startup but this morning I could not connect to the server and had to restart networking again, not ideal when it runs headless.

Any thoughts on what's causing this?

---

### Post by BigrThn666 on 2010-02-10
Similar thing happens to me.  I have two NIC cards in my machine (I am running Ubuntu Server 9.10) and both have static IP addresses assigned to them.

Ideally, I would like to only use wlan0 for my connection.  That way, I can move it to any place in my home and still be connected.  If I have wlan0 up and running with the static IP, everything appears to work just fine.  But if I leave it alone for a given amount of time (like when I'm sleeping) and I then return to it, my laptop fails to connect via ssh or even ping wlan0.  If I hop on the physical machine, I can ping google.com and the router just fine, but any machine (including the router) will not get relies back.

The situation is strange.  But if I get any answers, I will gladly let you know.  I hope that you may do the same :)

---

### Post by Iowan on 2010-02-10
Assuming you're on a server without Desktop/Network Manager, what's in */etc/network/interfaces*? **ifconfig -a** probably won't show much, but **lshw -C network** should show info on your interfaces.

---

