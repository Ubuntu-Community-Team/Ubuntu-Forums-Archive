---
title: "Wireless works, but quits after a few minutes?"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by PunchALunch on 2013-04-30
So, I'm currently running Ubuntu 11.10 on a Toshiba Satellite. 

Whenever I log into Ubuntu, my wifi connection comes on and I get to browse the Internet or download things like normal, (except for when the connection is horribly slow. As in 17kbps slow.)

Then after a random amount of time, the connection cuts off. It constantly tries:

1) Reconnecting,

2) Loading,

3) Asking for my WEP key

I've already ran (sudo apt-get upgrade), and apparently that didn't fix it, (pardon my noobiness)

How do I get my wifi connection to connect a decent amount of the time at a good speed?

---

### Post by PunchALunch on 2013-04-30
(Bump because at class and need laptop connection)

---

### Post by PunchALunch on 2013-05-01
Bump

---

### Post by PunchALunch on 2013-05-01
Bump

---

### Post by PunchALunch on 2013-05-01
Bump

---

### Post by steeldriver on 2013-05-01
What kind of wireless device is it? if it's USB, open a terminal (Ctrl-Alt-t) and type

```
lsusb
```

and post the results. Otherwise, run

```
lspci -nn | grep -E '(\[0200\])|(\[0280\])'
```

You can also use

```
sudo lshw -C network
```

to get more detailed hardware + driver info. We'll start there.

---

### Post by PunchALunch on 2013-05-01
It's a 

Realtek RTL8188CE 802

---

### Post by PunchALunch on 2013-05-02
thump hump bump

---

### Post by PunchALunch on 2013-05-04
Bump

---

