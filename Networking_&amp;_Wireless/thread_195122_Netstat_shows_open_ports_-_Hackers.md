---
title: "Netstat shows open ports - Hackers?"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by bond00 on 2006-06-12
I run a web and ssh server. I like to think I secure my box down pretty tight, but when I do a:

netstat -an|more

at the terminal it shows port 443 open on a few connections to ip addresses I'm unfamiliar with (someone back East). What's weird is that I'm behind a router that uses NAT so all ports without port forwarding should be blocked. I only forward 80 and 22. The results from netstat vary and the connections do not always appear. How are these connections being made and how can I stop them? Thanks in advance...

---

### Post by mscman on 2006-06-12
Netstat shows open ports on *your computer*, not necessarily what is viewed from outside of your router.  If you have any secure connections using TLS/SSL connections, port 443 is used.  This port is probably open on your local machine, even though it is being blocked by your NAT firewall on the router.  Chances are that your computer can make an outbound connection using this port, it just won't accept inbound activity.

Please note that I'm not a security expert, nor do I claim to be.  I'm simply offering my opinion on this matter, and I could be wrong.  If I am, and anyone can correct me, please do so :D

---

### Post by mscman on 2006-06-12
One other thing.  If you'd like to see what ports are currently viewable from the oustide, you may want to try a security scan from [Sygate]("http://scan.sygatetech.com/").  This is the site I use to test stealth of my computers at home and in the lab.

---

### Post by bond00 on 2006-06-12
I don't use SSL. Netstat shows the open ports on my computer and 443 isn't even listed. For example, for SSH and HTTP it reads,

127.0.0.1:22 
127.0.0.1:80

There is no listening service associated with port 443 which is why I'm concerned. How can they make a connection to that port if I don't even a listening service on it?

---

### Post by davidsxls on 2006-06-12
add -p to netstat argument to show the process to which those "open ports" pertain

---

### Post by nanotube on 2006-06-12
[QUOTE=bond00]I run a web and ssh server. I like to think I secure my box down pretty tight, but when I do a:

netstat -an|more

at the terminal it shows port 443 open on a few connections to ip addresses I'm unfamiliar with (someone back East). What's weird is that I'm behind a router that uses NAT so all ports without port forwarding should be blocked. I only forward 80 and 22. The results from netstat vary and the connections do not always appear. How are these connections being made and how can I stop them? Thanks in advance...[/QUOTE]
443 is https port. probably shows you browsing some ssl-ed websites. are you sure its the port opened on Your computer, rather than the port you are connected to on the foreign machine?
just post the output of 
```
sudo netstat -plantu
```
here, and we will take a look.

---

