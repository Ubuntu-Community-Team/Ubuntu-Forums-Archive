---
title: "network problem on 8.10 and 8.04"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by i-freaker on 2009-02-20
I have two computer running behind router. One is ubuntu 8.04 server version and another one is 8.10. If I turn on the computer with 8.04 for 1 or 2 days, the network starts to get strange. I cannot access any google site. I find that I can tracert, ping google, and the address can be resolved too, but in the web browser (elinks, firefox, and even wget), I can't go to google. I checked the with route -n, and it has the correct table. After reboot, it is normal again.

For the 8.10 desktop version, the network just stop working after a day or more. After reboot, it will become normal too.

Please help me, and if you need any more information, just tell me. :p

---

### Post by superprash2003 on 2009-02-20
do you put your computer to sleep(suspend)?

---

### Post by i-freaker on 2009-02-20
I never put them into suspend or sleep mode. I just locked the screen. And after a day or so, if I move the mouse, it asked my password, and I can login directly.

---

### Post by i-freaker on 2009-02-22
So, any idea?
Thanks.

---

### Post by sgosnell on 2009-02-22
Sounds like a router problem.  It may have something to do with the settings, and those can be very different from brand to brand.

---

### Post by i-freaker on 2009-02-23
I have a TP-LINK WR340G v5 router, and my windows xp behind it has no problem in networking at all.

Also, to restore the normal networking of the ubuntu 8.04 and 8.10, I have to reboot the computers, not the router.

... Is there suggestion that I can check where is the problem?

---

### Post by sedawk on 2009-02-23
Instead of rebooting you can try to "reset" the interfaces with
```

sudo ifdown eth0
sudo ifup eth0

```
and check if that fixes the problem.

If your computer get their IP via DHCP you can also try to
run
```

sudo dhclient eth0

```
to ask the router for a (new) valid IP.

I

---

### Post by i-freaker on 2009-02-23
Those commands ain't working.

---

### Post by i-freaker on 2009-02-24
I guess the problem is too complicated... or too strange to be solved?

---

### Post by i-freaker on 2009-03-05
Sorry, can any one give me some direction on the issue? It's very annoying, since it needed to be rebooted in 1 to 2 days.
If it still can't be solved, I think I may have another linux distro installed.

---

