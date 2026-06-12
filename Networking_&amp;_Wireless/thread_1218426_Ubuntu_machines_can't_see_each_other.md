---
title: "Ubuntu machines can't see each other"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by marshmallow1304 on 2009-07-20
Modem Router: Zyxel 660 (192.168.2.1)
Access Point: TRENDnet TEW-652BRP DHCP (192.168.2.1)
Machine 1: Desktop connected to router via eth, Jaunty 32, DHCP (192.168.2.4)
Machine 2: Laptop connected to router via wlan, Jaunty 64, Static (192.168.2.76)
Other: Nintendo Wii, DHCP (192.168.2.3)

I can ping from one to the other (IP address only), but they can't find each other and neither remote desktop or filesharing work (IP address or domain name).


Machine 1:
```
benn@bennhome:~$ nmap -sP 192.168.2.1-255

Starting Nmap 4.76 ( http://nmap.org ) at 2009-07-21 02:34 EDT
Host 192.168.2.1 appears to be up.
Host 192.168.2.2 appears to be up.
Host 192.168.2.4 appears to be up.
Nmap done: 255 IP addresses (3 hosts up) scanned in 1.43 seconds
```

Machine 2:
```
benn@system76-pc:~$ nmap -sP 192.168.2.1-255

Starting Nmap 4.76 ( http://nmap.org ) at 2009-07-21 02:31 EDT
Host 192.168.2.1 appears to be up.
Host 192.168.2.2 appears to be up.
Host 192.168.2.3 appears to be up.
Host 192.168.2.76 appears to be up.
Nmap done: 255 IP addresses (4 hosts up) scanned in 14.79 seconds
```

---

### Post by utnubuuser on 2009-07-20
try giving a little more info, such as are the services actually installed/enabled?

What have you tried?

---

### Post by marshmallow1304 on 2009-07-21
Thanks for replying.

I've edited my original post due to major changes in my setup due to (ultimately unsuccessful attempts at port forwarding).  Basically, I've configured my wireless router to act as a simple access point to let the modem/router take care of DHCP and forwarding.

From nmap, I can see that:
1. The desktop (machine 1) can see itself, the modem/router, and the access point.
2. The laptop (machine 2) can see itself, the modem/router, the access point, and the Wii.


I have tried file sharing and remote desktop with the desktop (1) as the server and the laptop (2) as the client.  I did make sure to enable both of those on the server-side.  I also tried using Giver, but that was unsuccessful as well.

I'll try booting the desktop from a Live CD so I can use the default settings; it very well could be some bad settings.

---

### Post by marshmallow1304 on 2009-07-21
> **marshmallow1304 said:**
> I'll try booting the desktop from a Live CD so I can use the default settings; it very well could be some bad settings.

I booted the desktop (machine 1) from the 8.04 live CD.  After doing so, I got the no change in nmap from the desktop; however, nmap from the laptop did show the desktop.

I tried Remote Desktop from the laptop to the desktop and it worked.  I'll probably just end up doing a fresh install on the desktop as I've been meaning to for a while.

I've also just gotten sharing working with the Live CD.

---

### Post by superprash2003 on 2009-07-21
do you use firestarter or ufw? could be something blocking

---

### Post by marshmallow1304 on 2009-07-21
> **superprash2003 said:**
> do you use firestarter or ufw? could be something blocking

It could have very well been firestarter.  I'll pay attention to what happens before and after I install firestarer when I to a fresh install.

---

