---
title: "Hamachi Problems"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by kexus on 2011-07-12
I'm having trouble connecting to people through Hamachi.  It was working fine yesterday, but today I was trying to join a server on Minecraft, and it stuck while trying to connect, and when to ping it, the console just returns "ping: sendmsg: Operation not permitted" until I kill it.  I get the same result when trying to ping anyone else on Hamachi, but not when pinging anything/anyone else.  Does anyone know what the problem is?

---

### Post by kexus on 2011-07-19
bump

---

### Post by kexus on 2011-07-19
Here is some information if that helps. The Hamachi interface is ham0.
Here is the output for "ifconfig ham0" :

Link encap:Ethernet  HWaddr 8e:d2:7e:91:38:13  
          inet addr:5.61.147.35  Bcast:5.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::8cd2:7eff:fe91:3813/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1404  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:6435 (6.4 KB)

And here is the output from "route -n"

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
5.0.0.0         0.0.0.0         255.0.0.0       U     0      0        0 ham0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by Fyrius on 2011-08-25
Bump...

I seem to be having the same problem. :(
I can connect to my friends' network and see everyone, but when I ping any of them I get the same result as Kexus: 'ping: sendmsg: Operation not permitted'. 
They don't have the same problem with each other. However, the one other person who uses Linux (who has a dual boot, unlike me) seems to have the same problem when running from Linux. 
Still, other people seem to be using Hamachi without such problems. What's going on?

I use the Haguichi front-end application thing now, but I had the exact same problem when I ran Hamachi from the command line earlier.

---

### Post by Fyrius on 2011-08-25
Oh hey. I think I've found the solution. ^^ With the help of [http://www.ubuntu-forum.de/artikel/55821/hamachi-ping-problem.html](http://www.ubuntu-forum.de/artikel/55821/hamachi-ping-problem.html)

Well, it's the fire wall. It blocks Hamachi traffic. Turn it off and pinging works fine.

(Edit: And Terraria multiplayering works fine, too.)

---

