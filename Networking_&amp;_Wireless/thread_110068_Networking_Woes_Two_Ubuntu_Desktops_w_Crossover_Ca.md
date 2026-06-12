---
title: "Networking Woes: Two Ubuntu Desktops /w Crossover Cable"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by flight_master on 2005-12-30
Hello All!

I'm a recent convert to Ubuntu (used to run Mandrivia / XP boxes) Anyway... all hardware was auto-detected (what a refreshing change!). I set up my dialup internet connection on Desktop 1 (Let's call it Box A). The modem is a hardware modem, connected to ttyS14. Box A has no trouble going on the net. I've been reading on how to setup NAT, but still having trouble.

Box A has 192.168.0.1 assigned to it as it's IP Address. The subnet mask is 255.255.255.0, Gateway address is blank, and Config is "Static IP address".

Box B has 192.168.0.2 assigned to it as it's IP Address. The subnet is the same as Box A. So is the gateway / config.

I can Ping Box A -> Box B and Box B-> Box A with 0% loss. However, browsers, mail, chat, irc, etc. don't work on Box B. I also setup Firestarter on Box A and enabled Internet Connection Sharing.

Still, no-go.

What am I doing wrong here?

Thanks!
Christian

---

### Post by M_berglund on 2005-12-30
Try set the gateway on B to 192.168.0.1 so it knows where to look for the internet. :P

---

### Post by davidsrsb on 2005-12-30
What is the output from the route command?

---

### Post by Lambert on 2005-12-30
On box A you you need to turn on ip forwarding.

```
sudo gedit /etc/sysctl.conf
```

I believe this line is commented out but it might also be =0. change it so it looks exactly like this.

net.ipv4.ip_forward=1

---

### Post by flight_master on 2005-12-30
Thanks all for your answers... setting the gateway, and adding that line to sysctl.conf (that file is blank except for a few comments on my system) everything is up and running.

Cheers!

---

