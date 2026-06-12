---
title: "How to set up ufw to make transmission working?"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by tanoloco on 2010-12-13
Hello guys! :D

could anyone explain me how to set up ufw in order to have transmission working?

> 
$ sudo ufw status verbose

State: enabled
Log: on (low)
Default: deny (in), deny (out)
New profiles: skip

To                         Action      From
-                          ------      --
51413/udp                  ALLOW IN    Anywhere
51413/tcp                  ALLOW IN    Anywhere

53/udp                     ALLOW OUT   Anywhere
80,443,8080/tcp            ALLOW OUT   Anywhere
110/tcp                    ALLOW OUT   Anywhere
25/tcp                     ALLOW OUT   Anywhere
20,21/tcp                  ALLOW OUT   Anywhere
2628/tcp                   ALLOW OUT   Anywhere
51413/tcp                  ALLOW OUT   Anywhere
51413/udp                  ALLOW OUT   Anywhere

I did a port forwarding in my router allowing in 51413 port tcp and udp
and check if ubuntu saw the port as opened as suggested here:
[http://ubuntuforums.org/archive/index.php/t-879334.html](http://ubuntuforums.org/archive/index.php/t-879334.html)
```
$ nc -z -v -w2 192.168.1.2 51413
Connection to 192.168.1.2 51413 port [tcp/*] succeeded!

```but still: It doesn't work! 

here they suggest to use other tools instead of transmission:
[http://ubuntuforums.org/showthread.php?t=1604833&highlight=transmission+ufw](http://ubuntuforums.org/showthread.php?t=1604833&highlight=transmission+ufw)

I would like to stay closer as possible to the official release .. and official suggestions.
As transmission is good for me I would like to use it.

Any of succeeded at setting up things properly in order to have transmission working?

Thank you for any help

---

### Post by tanoloco on 2010-12-13
I answer to myself, if this can be helpful to someone else in the future:

1. you have to open port 51413 tcp (or the port you specified in transmission preferences) 
in ufw firewall and in the router (port forwarding) .. the udp is not needed.

for ufw the code is:
```
sudo ufw allow in 51413/tcp
```2. I noticed that transmission (and maybe any other torrent client) needs to communicate freely through many out ports, so you have to allow it.
you have to default deny incoming traffic and default allow outgoing traffic
```

sudo ufw default deny incoming
sudo ufw deafult allow outgoing
```so my lists are:
> $ sudo ufw status verbose
State: enabled
Log: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                          Action      From
-                          ------      --
51413/tcp                  ALLOW IN    Anywhere

53/udp                     ALLOW OUT   Anywhere
80,443,8080/tcp            ALLOW OUT   Anywhere
110/tcp                    ALLOW OUT   Anywhere
25/tcp                     ALLOW OUT   Anywhere
20,21/tcp                  ALLOW OUT   Anywhere
2628/tcp                   ALLOW OUT   Anywhere
Personally, I prefer to deny outgoing traffic, so I decided: when I need to use transmission I allow outgoing traffic, and when I finish with it I deny outgoing traffic.

It would be nice to do it automatically:
when you open transmission, this runs a script which allow outgoing traffic; and when you exit transmission, this runs a second script which deny outgoing traffic.

But I don't know how to do it: any suggestion would be appreciated :P

---

### Post by aleoo on 2011-11-09
> **tanoloco said:**
> I answer to myself, if this can be helpful to someone else in the future:

1. you have to open port 51413 tcp (or the port you specified in transmission preferences) 
in ufw firewall and in the router (port forwarding) .. the udp is not needed.

for ufw the code is:
```
sudo ufw allow in 51413/tcp
```2. I noticed that transmission (and maybe any other torrent client) needs to communicate freely through many out ports, so you have to allow it.
you have to default deny incoming traffic and default allow outgoing traffic
```

sudo ufw default deny incoming
sudo ufw deafult allow outgoing
```so my lists are:
Personally, I prefer to deny outgoing traffic, so I decided: when I need to use transmission I allow outgoing traffic, and when I finish with it I deny outgoing traffic.

It would be nice to do it automatically:
when you open transmission, this runs a script which allow outgoing traffic; and when you exit transmission, this runs a second script which deny outgoing traffic.

But I don't know how to do it: any suggestion would be appreciated :P

..and if it's inactive?
```
$ man ufw
$ sudo ufw status verbose
Status: inactive
$ nc -z -v -w2 192.168.1.2 51413
nc: connect to 192.168.1.2 port 51413 (tcp) timed out: Operation now in progress
$ nc -z -v -w2 192.168.2.1 51413
nc: connect to 192.168.2.1 port 51413 (tcp) failed: Connection refused
$ sudo ufw allow in 51413/tcp
Rules updated
Rules updated (v6)
$ nc -z -v -w2 192.168.2.1 51413
nc: connect to 192.168.2.1 port 51413 (tcp) failed: Connection refused
```

---

### Post by aleoo on 2011-11-09
Now the port is open: I put a wrong IP, 192.168.2.1 (that is the one to configure the router) instead of 192.168.2.2

Anyway it's really slow (30-50 kb)..it's the first time I use it, how can I speed it up?

Sorry for the off topic

---

