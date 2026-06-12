---
title: "using ssh to remotely access my system thru LAN"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by abhigyan91 on 2009-10-26
hey evry1, 
suppose i have two ubuntu machines on the same network, like say in a cybercafe, how can i access 1 machine thru the other asuming i know the ip address, username and password of both machines?

i tried using ```
ssh username@ip
``` and it says connection refused. I think there may be some firewall or something. If so how can i change my iptables settings to enable remote access?

```

iptables -A INPUT -j ACCEPT -p ssh --dport 22 -s ip_of_remote_system
```

is this the correct code that i shud add to the "system to be accessed"?

also is there any way to use telnet? port 23 i think.. what changes should i do to the above command to use telent?

also in RHL, the iptables file is saved in /etc/sysconfig/iptables, but i cant find a similar file in ubuntu.. where is this file saved?

wow.. i kno thats a lot of questions n sum of them prob trivial but plz excuse me :P me n00b :D

also can i make ubuntu a server? i want to run a web server (apache), a DNS server, a webmail server all on my system.. is there any site which can help me step by step from the starting?

---

### Post by linorics on 2009-10-26
Every time I've setup an ssh server on ubuntu it works. Make sure the server is running. Try to connect to the server from the server.

```
ssh uname@localhost
```

---

### Post by Iowan on 2009-10-26
If the machine is a server, chances are, it came with SSH-server - otherwise, you will (probably) need to load it on the host machine(s).  The SSH client should already be there.

---

