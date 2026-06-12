---
title: "List used IP numbers in the LAN"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by MockY on 2009-02-24
How can I list used IP number in my LAN via terminal?

---

### Post by chili555 on 2009-02-24
Try this:```
fping -g 192.168.1.100 192.168.1.150
```Substitute your IP range as needed. The command:```
ifconfig
```will tell you whether your range is 192.168.0.x or 192.168.1.x. You will get something like this:> chili@LAPTOP40:~$ fping -g 192.168.1.100 192.168.1.150
192.168.1.100 is alive
192.168.1.101 is alive
192.168.1.105 is alive
192.168.1.108 is alive
192.168.1.116 is alive
192.168.1.118 is alive
192.168.1.121 is alive

---

### Post by cariboo on 2009-02-24
I created a script with this line it it to to check which computers were up on the network:

```
sudo nmap -PR -sP 192.168.1.0/24j
```

Jim

---

### Post by MockY on 2009-02-25
Thanks for your responses.
 
fping creates an infinite loop. Once all ip numbers in that subnet is checked, it is checked again. It would be nice if it could stop after one round, and only output the active addresses.

nmap does what I wanted it to, as in only outputting used addresses. However, only a fraction of used addresses are detected (running it as root as suggested fixes this, though I don't understand why). Furthermore, what I wish it could do is listing the hostname. Right now, only a few computers are listed with their host name. However, the NIC vendor is listed, which is pretty neat.

---

### Post by kriom on 2013-04-16
I think fping is a good solution :

install :
[FONT=&quot][COLOR=#666666][COLOR=#38761d]sudo apt-get install fping[/COLOR][/COLOR][/FONT]

then use it :
[FONT=&quot][COLOR=#38761d]fping -a -g [COLOR=#b45f06]192.168.1.0/24[/COLOR] 2> /dev/null[/COLOR][/FONT]
[FONT=&quot][COLOR=#3d85c6]192.168.1.10
192.168.1.20[/COLOR][/FONT]

source :
[http://kriom.blogspot.fr/2013/01/howto-find-hosts-on-lan-if-they-respond.html](http://kriom.blogspot.fr/2013/01/howto-find-hosts-on-lan-if-they-respond.html)

---

### Post by Iowan on 2013-04-16
Closed - old thread.

---

