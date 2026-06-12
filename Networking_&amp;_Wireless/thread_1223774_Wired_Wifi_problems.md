---
title: "Wired/ Wifi problems"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by TridentCrash on 2009-07-26
Hi. Ive heard/ read many things about linux and i really wanted to try it out. so i downloaded a live cd. i seem to have a bit of a problem tho... when ever i try to connect to either wired or wireless internet the network manager or whatever the program was called dosnt dectect anything!! i dont kno what to do saying im new to linux and all. any help would be greatly appreciated!

Im running live cd off of a dell inspiron 1501 with all factory installs still also running windows XP

---

### Post by ajgreeny on 2009-07-26
I am amazed that the wired ethernet does not work!  that is usually a certain way of getting connected. What sort of modem or router are you using?

---

### Post by TridentCrash on 2009-07-26
not exactly sure this is what your askin for but here goes...

Linksys Wireless-G Broadband Router
2.4 GHz   802.11g
W/ Speed Booster

---

### Post by Newfoundlander on 2009-07-26
Within the last 72 hours, there seems to be something breaking Ubuntu 9.04 systems relating to DSN.

Open your terminal and try the following:

```
ping www.google.com
```

My guess is you'll get an error saying "ping: unknown host www.google.com"

Next try:

```
ping 74.125.79.99
```

If the first one does not work but the second one does then you are in the same boat as me and the growing number of users posting here.

---

### Post by TridentCrash on 2009-07-26
i guess eiter i mis-spoke or you understood. either way idc. lol

in order to ping google through terminal i would of corse have to have internet connection shouldnt i? i of corse dont have internet cause i cant see any of them? plus my network is also password protected. ill try this anyways. im not to technical so i may just be confusing myself

---

### Post by Iowan on 2009-07-26
> **TridentCrash said:**
> Hi. when ever i try to connect to either wired or wireless internet the network manager or whatever the program was called dosnt dectect anything!! Does the machine get an IP address? Check (post) **ifconfig -a** and **lshw -C network**. If no valid (not avahi) addresses show, post results of **dhclient**.

---

