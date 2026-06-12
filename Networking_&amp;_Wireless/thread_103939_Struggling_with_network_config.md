---
title: "Struggling with network config"
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by catfox on 2005-12-15
I have a server with two nics - 1 wired and one wireless.
the wired one is connected to a router, and the wlan is in ad-hoc mode, on a different subnet.
the problem is, from the client, i can see the ESSID, and i can ping the servers eth0 card, but nothing else. i'm completely stuck here, so any help would be great!
i've drawn a diagram of my setup - if anyone could take a look, thatd be great!
[http://www.currentlyfabulous.com/net.png]("http://www.currentlyfabulous.com/net.png")

---

### Post by alamba on 2005-12-15
Run a traceroute to 192.168.1.1 and see where the packets drop. Post the result. 

Akshay

---

### Post by Lambert on 2005-12-15
Also check your routing table with the command [FONT=Arial]*route. *You may need to set up a gateway.[/FONT]

---

### Post by catfox on 2005-12-15
running route on my server shows this:
but i can't really tell where things are going wrong. after getting in from work, i can no longer connect to the server box from the laptop at all. 

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 wlan0
loopback        *               255.0.0.0       U     0      0        0 lo
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

on the client box, route gives this:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0        *                 255.255.255.0   U        0        0      0   wlan0
default           192.168.2.12   0.0.0.0               UG     0         0     0   wlan0

```

---

### Post by Lambert on 2005-12-15
On the server, do you have ip forwarding turned on? I believe it's in the /etc/sysctl.conf file.

Before:

 

# Disables packet forwarding 
net.ipv4.ip_forward=0

 

After:

 

# Enables packet forwarding 
net.ipv4.ip_forward=1

---

### Post by catfox on 2005-12-15
thanks for the reply. the server is now port forwarding. the problem is, i still can't connect to it from the client.
when i scan for wireless networks on the client and add a new connection with the ubuntu network tool, but there's still no way of contacting the server from the client, i cant ping either the eth0, wlan0 or router on the server side.

i'm completely stumped.

---

### Post by Lambert on 2005-12-15
Check to make sure the wireless card on the server is still in ad-hoc mode.
Also bring the inteface down and then back up once to see if it solves it. Your first thread said you were connected to server, not sure what happened.

---

