---
title: "How do I findout my Gateway?"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by babujbf on 2009-11-10
Hey guys, I am installing DesktopBsd to have a dual boot. I remember I installed it once before and the DHCP thing didn't work so I had to put in the info such as Ip address, Subnet mask manually... Those were easy to find but how do I find out what gateway I am on if anyway. I just have a plain wireless connection. And its a modem/router just one piece not separate.

Thanks

---

### Post by Iowan on 2009-11-10
If you're typing on an Ubuntu machine, check **route** - the last line should show the default gateway (usually flagged "UG").

---

### Post by ThaSwCh on 2009-11-10
If you are connected to your router, open a terminal on your PC and enter the following:

ip route

Then look for the line that looks like the one below:

default via 48.24.88.5 dev wlan0  proto static

---

### Post by theozzlives on 2009-11-10
Set all that to auto. Then setup your IP address in your router. Your router should be able to act as a DHCP server and assign your private IPs for the individual machines.

---

### Post by running_rabbit07 on 2009-11-11
[SIZE=3]I[/SIZE][SIZE=3]f your system is connected, enter```
netstat -r
``` This will work with Linux or [/SIZE][SIZE=1]Windows[/SIZE].

[SIZE=3]If you are using a linksys and you haven't set a different default gateway, then it should be 192.168.1.1[/SIZE]

---

