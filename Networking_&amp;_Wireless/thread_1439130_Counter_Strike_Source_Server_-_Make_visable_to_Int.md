---
title: "Counter Strike Source Server - Make visable to Internet"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by geoffmcc on 2010-03-25
Ok. Ubuntu Server 1, Ubuntu Server 2 & Windows 7

Internet connected to uplink of hub
Ubuntu 1 [IP from ISP dhcp setup Local network eth0:1- static]
Ubuntu 2 [static IP address configured - 192.168.x.x]
Windows  [static IP address configured - 192.168.x.x]

All computers have a working internet connection threw Ubuntu 1

I want my counterstrike server to be ran from Ubuntu 2. I have done some browsing and was able to get my server to show up on the internet tab so it is join-able by anyone on the web but it shows up at least 20 times.  I ran

```

iptables -A PREROUTING -t nat -i eth0 -p udp --dport 27015 -j DNAT --to 192.168.10.2:27015 

```

```

iptables -A INPUT -p udp -m state --state NEW --dport 27015 -i eth0 -j ACCEPT 

```

Is the problem with my iptables do you think? I guess what i am asking is if you were trying to accomplish this what would you do.

also, could it be possible that for some reason it is showing on all these times on my screen but not to anyone else?

---

### Post by zerkig on 2010-03-25
Hi 

I am not an expert. However I did something similar with another game server with that server I had to 
1)forward the listening port on the router to the game server 
2)configure the game server to create client connections in a specific range of ports (I used 60000-60100)
3)forward that range from the router to the game server

Hope that helps.

---

### Post by geoffmcc on 2010-03-25
i was able to resolve using

```
iptables -t nat -A PREROUTING -p udp -d mydomain.com -i eth0 --dport 27015 -j DNAT --to-destination 192.168.10.2:27015
```
and
```

iptables -A FORWARD -p udp -m state --state NEW --dport 27015 -i eth0 -j ACCEPT
```

---

