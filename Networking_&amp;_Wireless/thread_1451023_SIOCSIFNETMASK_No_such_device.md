---
title: "SIOCSIFNETMASK: No such device"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by mikau16 on 2010-04-09
Hello!

I am having an odd problem with a program I'm trying to run which is supposed to connect to a network. The messages printed when I start up the program are: 

[FONT=Arial][SIZE=2][COLOR=#000000]SIOCSIFNETMASK: No such device
192.168.11.50: ERROR while getting interface flags: No such device
SIOCADDRT: File exists[/COLOR][/SIZE][/FONT]

One reason this is particularly odd is that the network itself appears to be working fine, otherwise. I can connect to the internet on my computer and everything, but the program is not able to connect to it, for whatever reason. I've tried tinkering with the settings but nothing worked.

Help would be appreciated!

---

### Post by Iowan on 2010-04-11
Which program are you running?

---

### Post by mikau16 on 2010-04-12
c2mincs. its an existing program at work we're developing extensions for.

---

### Post by Iowan on 2010-04-12
I'm not familiar with **c2mincs**, but I wonder if it is expecting to have interfaces defined in */etc/network/interfaces*?

---

