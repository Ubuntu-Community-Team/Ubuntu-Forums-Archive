---
title: "n00b wireless help request"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by IT1rB on 2011-04-18
Hi people, I'm sure this has come up here a few hundred times but I need help setting up my wireless connection.
I've tried work-around after work-around and I'm at the stage where I've lost the plot with it and don't know what else to do.
I've had the same problems with other distros (slax, centos) and managed to get them working but can't get ubuntu to work, not sure if it's a linux thing or I just have the worst wireless card around lol.

Anywho, my wireless card is Intel ipw2200. I could probably provide more info but don't know what.

Thank you

*EDIT: I have progressed with my wireless connection, sort of. I can connect to the network and then a few seconds later it disconnects. Does anyone have any idea what this could be?

---

### Post by chili555 on 2011-04-19
Please confirm that the ethernet cable is detached as you try to connect. Network Manager will default to wired if it's available.

Next, in a terminal, run and post:```
rfkill list all
dmesg | grep ipw
```What kind of computer is it? Brand and model, please.

---

