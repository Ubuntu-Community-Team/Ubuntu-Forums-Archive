---
title: "No internet on belkin router"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by Andy218 on 2008-12-27
Hiya. Well you know my problem. No internets on ubuntu.

Before you bombard me with reasons as to why it isn't working, let me help you rule some out.

There is realy only one thing i can think of, and that is that i have a card in the back of my comp with an antenna. It has a green light That is on even when my comp is off. I boot linux, boop, light goes out. its like a 802.11g or sumtin.:guitar:

Although i have seen many other problems relating to this, they are very user specific.

At the moment i am reburning for the 5th time the live cd which hasnt been booting.:(

This thing happens both on live cd and install.:confused:

Also, i have no encription on the connection. Its just open.

I have xbox live. That shouldnt be relevant though.
um..


I think thats all i know...
Do i need a driver or sumtin?




uh...
>.>

<.<

o.o

Can somebody get me a diet chery vanila coke?

---

### Post by pytheas22 on 2008-12-27
Please open a terminal from the Applications>Accessories menu, run the following commands and post the output:
```

sudo iwlist scan
lshw -C Network
lspci -nn
lsusb
uname -rm
```

We need that information to know how to get your card working.

---

