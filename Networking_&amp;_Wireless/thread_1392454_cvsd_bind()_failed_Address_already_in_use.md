---
title: "cvsd: bind() failed: Address already in use"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by pullmoll on 2010-01-28
I wanted to run cvsd on my Ubuntu 9.10 64bit installation. All I get is the error message from the subject, regardless which port I configure in /etc/cvsd/cvsd.conf. And of course the port is not in use before I try to /etc/init.d/cvsd start.

Any ideas?

DUH! Searching helps :)

---

### Post by scarf on 2010-03-12
what were your findings?  i am getting a similar error with bootp:

bootpd: error(3):  bind: Address already in use

---

### Post by Sugi on 2010-12-26
Sorry to bring up an old thread, but definitely pullmoll, you should post to the link to your findings for other people that are having the same problem.

Check what port are being used:
netstat -tapl

Find whatever program is using that port, and shut it down.
killall -9 XXXXX

Reference:
[http://www.linuxquestions.org/questions/solaris-opensolaris-20/bind-address-already-in-use-messages-474165/](http://www.linuxquestions.org/questions/solaris-opensolaris-20/bind-address-already-in-use-messages-474165/)
[http://www.cyberciti.biz/faq/apachehttpdaddress-already-in-use-make_sock-could-not-bind-to-port-80-or-443/](http://www.cyberciti.biz/faq/apachehttpdaddress-already-in-use-make_sock-could-not-bind-to-port-80-or-443/)

Ubuntu Maverick x64

Sugi

---

### Post by dioukf on 2011-07-06
I solved this problem changing the "*" on the listen parameter by the server ip address.

---

