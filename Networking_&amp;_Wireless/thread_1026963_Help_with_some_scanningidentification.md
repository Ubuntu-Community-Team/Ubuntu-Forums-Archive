---
title: "Help with some scanning/identification"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by nausicaavow on 2008-12-31
Hello,
I have enabled the iptables front-end ufw, and am doing some poking around. Can someone help me with some questions? Here is what I am looking at...

[FONT="Lucida Console"]root@ubuntu:~# ufw status[/FONT]
[SIZE="1"]Status: loaded

To                         Action  From
--                         ------  ----
22/tcp                     ALLOW   Anywhere
5353/udp                   ALLOW   Anywhere[/SIZE]

[FONT="Lucida Console"]root@ubuntu:~# netstat -an | egrep 0.0.0.0[/FONT]
[SIZE="1"]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN
udp        0      0 0.0.0.0:42766           0.0.0.0:*
udp        0      0 0.0.0.0:5353            0.0.0.0:*[/SIZE]

[FONT="Lucida Console"]root@ubuntu:~# nmap -sS -sU  -p [SIZE="1"]U:5353,42766,T:22 192.168.1.200[/FONT]

Starting Nmap 4.62 ( [http://nmap.org](http://nmap.org) ) at 2008-12-31 18:10 EST
Interesting ports on 192.168.1.200:
PORT      STATE         SERVICE
22/tcp    open          ssh
5353/udp  open|filtered zeroconf
42766/udp open|filtered unknown[/SIZE]

So on to the questions...
1) Is the netstat command I used guaranteed to identify ALL the listening udp/tcp ports? ( 0.0.0.0 is the external internet? )

2) By using the host IP address (not localhost), nmap is scanning from the perspective of the network? ( like the scan is being run from a different machine on the local network? )

3) So if my firewall is accepting traffic for port 22/tcp and 5353/udp, why isn't nmap reporting port 5353 as open? And, why is it reporting port 42766 at all?

4) How can I determine which service is listening on udp port 42766?

Thanks!

---

### Post by nausicaavow on 2008-12-31
> **nausicaavow said:**
> 1) Is the netstat command I used guaranteed to identify ALL the listening udp/tcp ports? ( 0.0.0.0 is the external internet? )

2) By using the host IP address (not localhost), nmap is scanning from the perspective of the network? ( like the scan is being run from a different machine on the local network? )

3) So if my firewall is accepting traffic for port 22/tcp and 5353/udp, why isn't nmap reporting port 5353 as open? And, why is it reporting port 42766 at all?

4) How can I determine which service is listening on udp port 42766?

Ok I found that netstat can report the program, it is avahi-daemon. I would still like to confirm questions 1, 2, and 3?

Also, since I run both Pidgin and Banshee, I am not sure if zeroconf and avahi-daemon are necessary or not. Can someone tell me if either program actually uses these services, and if it would cause any issue to disable them?

---

