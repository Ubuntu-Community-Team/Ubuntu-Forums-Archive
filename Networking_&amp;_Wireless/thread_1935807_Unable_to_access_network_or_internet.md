---
title: "Unable to access network or internet"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by petey1993 on 2012-03-05
This one has thrown me in a true loop.
I have been assigned all of my stuff via DHCP, I have check, rechecked, checked again, and again.  It's all there.

I cannot even ping my router, yet if I boot into windows I can get on perfectly.

Any thoughts?
Give me the commands to crunch if needed.

---

### Post by athampan on 2012-03-05
What are the outputs of 
```

$cat /etc/network/interfaces
$ifconfig
$cat /etc/resolv.conf

```

---

### Post by Bucky Ball on 2012-03-05
Can you get online with an ethernet cable or is that what you are attempting?

Also provide output of:

```
sudo lshw -C network
```

... release you are using and machine. Thanks.

PS: Have you checked the details you have in Network Manager against the details you have in the, working, Windows network setup???

---

