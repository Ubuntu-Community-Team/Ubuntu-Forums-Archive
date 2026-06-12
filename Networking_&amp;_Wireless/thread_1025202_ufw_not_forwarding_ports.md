---
title: "ufw not forwarding ports"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by luca662 on 2008-12-29
Hello, 

I am having problems with ufw opening ports for other machines. I want to have port 6113 open on my xp machine. I know for a fact that I do not have a software firewall because the port is open when I plug in linksys router instead of my ubuntu router. My set up is: 
DSL modem--->Ubuntu router(eth0)-->eth1 connects to switch---> switch connects to computers. 

```
root@ubuntu:/home/luca662# ufw status
Status: loaded

To                         Action  From
--                         ------  ----
22/tcp                     ALLOW   Anywhere
22/udp                     ALLOW   Anywhere
6112/tcp                   ALLOW   Anywhere
6112/udp                   ALLOW   Anywhere
6113/tcp                   ALLOW   Anywhere
6113/udp                   ALLOW   Anywhere

root@ubuntu:/home/luca662#


```

As you can see port 22 and 6113 are open, but on my xp machine it is still shows it as closed.  Port 22 is open for sure because I can use ssh on my xp machine(which is on the lan) and on my phone. (through the internet). It seems like the ports are only open for the ubuntu router and not the other computers in the network. Do I have to add a line to my iptables to do this? The only thing I did to my ip tables is I put these two lines in /etc/rc.local

```

/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o ppp0 -j MASQUERADE

```

Any help would be appreciated.

---

