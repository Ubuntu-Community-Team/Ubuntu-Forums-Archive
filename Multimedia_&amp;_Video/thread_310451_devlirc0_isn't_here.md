---
title: "/dev/lirc0 isn't here"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by christooss on 2006-12-01
[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

A have followed the wiki howto and I hope this is the right place to ask

> christooss@ubuntu:~$ sudo /etc/init.d/lirc start
##################################################
## LIRC IS NOT CONFIGURED                       ##
##                                              ##
## read /usr/share/doc/lirc/html/configure.html ##
##################################################
Starting lirc daemon:.


I have copyed lirc.conf for my remote file to /etc/lirc

when I try to run irw it say
> connect: Connection refused

if I run

sudo irrecord -d /dev/lirc0 lircd.conf

the out put is
> 
irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not init hardware (lircd running ? --> close it, check permissions)

And /dev/lirc0 isn't present on my system

And thoughts?

I have pinnacle system remote

---

### Post by canzi on 2007-11-12
bump, im working on the same issue, it was fine in feisty

---

