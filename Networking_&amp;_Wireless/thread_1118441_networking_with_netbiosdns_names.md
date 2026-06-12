---
title: "networking with netbios/dns names"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by Miles_Prower on 2009-04-07
after setting up a few servers and playing around with remote administration, I've noticed that the 'names' I give each of my computers ```
tails@tornado:~$ echo this\ one\ is\ called\ 'tornado'
this one is called tornado

```
cannot be consistently used to reference the machine. Commands like ```
tails@tornado:~$ ssh 192.168.1.69

```
Will just about always work, but commands like this ```
tails@tornado:~$ ssh lava-reef

```
often give errors about not being able to resolve host 'lava-reef' (or whatever the name of the computer I'm trying to hit is)


As far as I know, these are netbios names, right? Or are they DNS names? What handles these name resolutions for ubuntu? Samba?

---

