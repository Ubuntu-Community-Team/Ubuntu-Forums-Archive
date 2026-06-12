---
title: "No internet on new install"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by axel4401 on 2011-04-06
Hey all, I just installed Ubuntu 10.10. I first want to say I am very new to Linux, so pardon if my questions are ridiculous. 

Basically, I bought a whitebox server, installed Ubuntu 10.10 and cannot get an internet connection. In the interfaces file I have a static IP setup under eth0 and vibr0. Before I did this however, the internet was not working as well. I can post anything needed to solve the issue. Thanks in advance for any suggestions/help.

:confused:

---

### Post by axel4401 on 2011-04-06
bump for help

---

### Post by Iowan on 2011-04-06
Your questions are not ridiculous. I'm not really familiar with vibr0 (virtual bridge???) You might post contents of */etc/network/interfaces*. How many interfaces is the machines *supposed* to have?

(As a side note - one bump/24 hours is generally adequate).

---

### Post by axel4401 on 2011-04-07
There are 2 ethernet ports in the back, and here is what the current setup looks like: linux.jpeg


Here is my interfaces file as of now:

"
auto lo eth0
iface lo inet loopback

iface eth0 inet dhcp"

my ifconfig is:

54.jpg

---

### Post by axel4401 on 2011-04-10
anyone?

---

