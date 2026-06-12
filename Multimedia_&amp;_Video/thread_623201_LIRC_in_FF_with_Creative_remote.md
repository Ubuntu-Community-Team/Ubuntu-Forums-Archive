---
title: "LIRC in FF with Creative remote"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by Araj on 2007-11-25
I'm trying to run LIRC on (K)ubuntu Feisty to support a Creative CIMR 100 remote receiver on com1 of my trusty old Thinkpad T22. The idea is to get the remote to control Amarok.

Can anyone give me a walkthrough? I've been trying to get it going for 2 days with no success.

At the end of installing, I got the message "You will have to use the suitable kernel driver to access /dev/ttyS0" - erm, which "suitable kernel driver" ?

I've tried the LIRC documentation and countless howtos but no joy so far. The only way I can get any response from irw is by running with the --nodaemon option, which returns

root@araj-laptop:/home/araj# lircd --nodaemon
lircd: lircd(creative) ready
lircd: accepted new client on /dev/lircd
lircd: readlink() failed for "/dev/lirc"
lircd: No such file or directory
lircd: could not create lock files
lircd: caught signal
Terminated

It's true there's no /dev/lircd directory - but if there's meant to be, why wasn't this created in the install? I tried 2 new compile/configuration/installs but no /dev/lircd directory is created. Do I need to create it manually? And what's supposed to be in it?

irexec returns

root@araj-laptop:/home/araj# irexec
irexec: could not connect to socket
irexec: Connection refused

I'm pretty new to Ubuntu and Linux in general, so please forgive me if I'm missing the obvious - but point it out ;-)

Thanks in advance for any help !

---

