---
title: "Internet doesnt work in ubuntu"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by Alex01 on 2009-03-09
Hey everybody. Ive been trying to fix this problem for a while and i almost give up so i decided to join in.
:)

Also i just installed ubuntu 8,10 on my laptop HP L200 and i have no idea of how this thing works. 

So the problem is that i cant connect to an wired ethernet connection on my lap, it detetcs it then try to connect and nothing. Disconnected.
Do anybody have any idea of what could be wrong?

---

### Post by 3Miro on 2009-03-09
> **Alex01 said:**
> Hey everybody. Ive been trying to fix this problem for a while and i almost give up so i decided to join in.
:)

Also i just installed ubuntu 8,10 on my laptop HP L200 and i have no idea of how this thing works. 

So the problem is that i cant connect to an wired ethernet connection on my lap, it detetcs it then try to connect and nothing. Disconnected.
Do anybody have any idea of what could be wrong?

I understand wired connection. Maybe a driver issue?

Go to a terminal and type "ifconfig", post the result.

Are you using DHCP or static IP?

---

### Post by Iowan on 2009-03-09
That problem pops up periodically. Network Manager doesn't always play nice, and drivers in laptops may need upgrading/replacement.  In a terminal:
```
ifconfig -a
```post results.  Might also post results of ```
lshw -C network
```

---

### Post by fragos on 2009-03-09
Without the obvious is it connected via Ethernet to a modem I'd next left click the Network Management icon in the upper applet bar toward the right side. There you can see what network connection is selected e.g. eth0 or perhaps wlan0. For wired network you want eth0.

---

### Post by bapoumba on 2009-03-10
Moved to Networking.

---

### Post by jigsaws on 2009-03-10
First of all, check your ethernet link, try:
sudo ethtool eth0

---

### Post by bogart_2003 on 2009-03-10
hi to everyone. just like the thread starter, i'm new to ubuntu, and i installed 8.04 a few days ago, dual boot with windows xp using wubi. 

my internet connection works fine in windows, yet i can't get it to work in ubuntu. i tried reading some forums, and tried the "sudo pppoeconfig" command, and the message that appeared was

"Sorry, I scanned 2 interfaces, but the Access concentrator of your provide did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem"

I've seen this message occur to other users as well in different forums, but i can't find the right solutions for me. i know the ubuntu community is very friendly, and any response will be highly appreciated.

---

