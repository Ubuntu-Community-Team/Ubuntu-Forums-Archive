---
title: "Internet on LAN"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by Skia_42 on 2006-06-09
Okay, I have a Local Access Network (ethernet connection) and have been trying to get internet on my box running Ubuntu. I am new to Linux and am not sure how to get internet up and running with my LAN. Could anyone tell me how to configure the Network Settings?

---

### Post by CameronCalver on 2006-06-09
Ok first just a tip

Ok when you post you have to be more specific or none will be able to help you
So if your computer you want internet on windows or ubuntu and is it dial up or though router  ok now answer those questions and i migh be able to help you

---

### Post by glotz on 2006-06-09
Do you use DHCP or manual static IP? 

Set your settings in System > admin > network

---

### Post by CameronCalver on 2006-06-09
try in the terminal ping 192.168.1.1

---

### Post by Skia_42 on 2006-06-09
[QUOTE=CameronCalver]Ok first just a tip

Ok when you post you have to be more specific or none will be able to help you
So if your computer you want internet on windows or ubuntu and is it dial up or though router  ok now answer those questions and i migh be able to help you[/QUOTE]

I am trying to get internet up and running on my g3 iMac running Ubuntu. I am getting internet on my other computers through a router. (I have DSL) Does that answer your question(s)?

I set it up for DHCP, enabled it, and the interface eth0 is active but I am still not getting internet.

When I ping 192.168.1.1 I get the following output:
> 
PING 192.168.1.1 (192.168.1.1): 56 data bytes
64 bytes from 192.168.1.1: icmp_seq=0 ttl=64 time=1.212 ms
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.885 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.06 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.868 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.913 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.945 ms


---

### Post by Jason_25 on 2006-06-09
Looks like your IP is set right.  What does 
```

cat /etc/resolv.conf

```
show?  For some reason your DNS may not have been assigned correctly during the  DHCP process.  In that case, you can add your ISP's dns server's addresses or just your router at 192.168.1.1 to that file.

---

### Post by Skia_42 on 2006-06-09
oops, sorry. On my computer running Ubuntu I do not get the output of:
64 bytes from 192.168.1.1: icmp_seq=0 ttl=64 time=1.212 ms
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.885 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.06 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.868 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.913 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.945 ms

I ran the command on the wrong computer, the real output for:
PING 192.168.1.1 (192.168.1.1) is:
> 
From 192.168.0.100 icmp_seq=2 Destination Host Unreachable
From 192.168.0.100 icmp_seq=3 Destination Host Unreachable
From 192.168.0.100 icmp_seq=4 Destination Host Unreachable
From 192.168.0.100 icmp_seq=5 Destination Host Unreachable
From 192.168.0.100 icmp_seq=6 Destination Host Unreachable
From 192.168.0.100 icmp_seq=7 Destination Host Unreachable
From 192.168.0.100 icmp_seq=8 Destination Host Unreachable

> cat /etc/resolv.conf does not give me and output

---

### Post by Skia_42 on 2006-06-10
I found the "Wired Ethernet Troubleshooting Process" and now I think know what I am looking for. I need to add a Parallel line interface to my list of interfaces but there is no "Add" or "Delete" buttons in my Connections Window.
Does anyone know how to add an interface by some other means?
My GNOME version is 2.12.1 and I have Breey Badger 5.10 if that helps.

---

### Post by Iowan on 2006-06-12
Uh-oh, something here doesn't look kosher... >  I ran the command on the wrong computer, the real output for:
PING 192.168.1.1 (192.168.1.1) is:

Quote:
From 192.168.0.100 icmp_seq=2 Destination Host Unreachable
From 192.168.0.100 icmp_seq=3 Destination Host Unreachable
From 192.168.0.100 icmp_seq=4 Destination Host Unreachable
From 192.168.0.100 icmp_seq=5 Destination Host Unreachable
From 192.168.0.100 icmp_seq=6 Destination Host Unreachable
From 192.168.0.100 icmp_seq=7 Destination Host Unreachable
From 192.168.0.100 icmp_seq=8 Destination Host Unreachable
 Subnets aren't the same...

---

### Post by aldegaz on 2006-06-12
I have the same problem

---

### Post by Iowan on 2006-06-13
Check this thread and the associated bug report:
[http://www.ubuntuforums.org/showthread.php?p=1128313#post1128313]("http://www.ubuntuforums.org/showthread.php?p=1128313#post1128313")

---

