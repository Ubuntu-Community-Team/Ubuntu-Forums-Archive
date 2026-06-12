---
title: "Which ports need to be open in order to &quot;network browse&quot; ?"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by uncle-c on 2009-10-12
My Ubuntu is connected to an XP box and a Fedora machine; Fedora being the samba server. I can access files from Ubuntu with both machines with no problems.However, when I try to browse the network ( on Ubuntu) using PLACES --> NETWORK I am getting nowhere; neither XP or Fedora icons show up in the browse. When I disable the Ubuntu firewall, I can browse and see both XP and Fedora share icons in the browser. Obviously this must be a firewall issue. I have 137-138 udp as well as 139 tcp open on my Ubuntu but still cannot browse. So which other ports need to be opened ? I've tried 135 tcp and 445 tcp but no luck.

c

update----

I've checked /var/log/messages and I get this :

```

Oct 12 17:29:06 Ubuntu8-10 kernel: [16680.193662] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=*:*:*:*:*:*:*:*:*:*:*:*:*:* SRC=192.168.*.* DST= UBUNTU IP ADDRESS LEN=102 TOS=0x00 PREC=0x00 TTL=128 ID=7535 PROTO=UDP SPT=137 DPT=38698 LEN=82 

```

[UFW BLOCK INPUT] on port 137 UDP

But :

```


unclec@Ubuntu8-10:~$ sudo ufw status
Status: loaded

To                         Action  From
--                         ------  ----
***/tcp                     ALLOW   192.168.0.0/24
***/tcp                   ALLOW   192.168.0.0/24
***/udp                    ALLOW   192.168.0.***
***/tcp                   ALLOW   192.168.0.***
137/udp                    ALLOW   192.168.0.0/24


```

which allows access to on Ubuntu port 137 UDP  ???!!!!
Any find out what is happening ???


***update****

Apparently there was a bug in UFW for 8.10 

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1364574.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1364574.html)

You have to change the ufw rules from 

```

$ sudo ufw allow proto udp from 192.168.0.0/24 to any port 137

```

to
```

$ sudo ufw allow from 192.168.0.0/24 port 137 proto udp

```

ufw status now becomes 

```

unclec@Ubuntu8-10:~$ sudo ufw status
Status: loaded

To                         Action  From
--                         ------  ----
***/tcp                     ALLOW   192.168.0.0/24
***/tcp                   ALLOW   192.168.0.0/24
***/udp                    ALLOW   192.168.0.***
***/tcp                   ALLOW   192.168.0.***
Anywhere                   ALLOW   192.168.0.0/24 137/udp


```

Network browsing now works fine.


cheers
C

---

