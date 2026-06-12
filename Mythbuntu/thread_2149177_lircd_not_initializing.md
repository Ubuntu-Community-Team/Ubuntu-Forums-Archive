---
title: "lircd not initializing"
date: 2013-05-27
forum: Mythbuntu
---

### Post by bleve on 2013-05-27
I think I finally got everything recording and working as it should by adding the mythtv repos and doing an update.  Now that the video is recording this broke lirc.  After a reboot I notice that lirc_zilog is not loaded and I can add it back with modprobe but /dev/lircd is missing:

> root@mythtv01:/dev# modprobe lirc_zilog
root@mythtv01:/dev# /etc/init.d/lirc restart
root@mythtv01:/dev# lsmod |grep lirc
lirc_zilog             22066  0 
lirc_dev               18701  1 lirc_zilog
root@mythtv01:/dev# irsend LIST "" ""
irsend: could not connect to socket
irsend: No such file or directory

root@mythtv01:/dev# dpkg -l |grep lirc
ii  liblircclient0                               0.9.0-0ubuntu1                                     infra-red remote control support - client library
ii  lirc                                         0.9.0-0ubuntu1                                     infra-red remote control support
ii  mythbuntu-lirc-generator                     0.26-0ubuntu1                                      Mythbuntu Lirc Configuration Generator


So, what happened?  After a reboot the zilog driver is missing again.

---

### Post by bleve on 2013-05-28
This one is solved.  The update had wiped out my /etc/lirc files.  Well it copied them luckily .old.  So I just needed to copy them back and restart lirc.  Another thing the update did is it reinitialized my "my.cnf" for mysql to listen using localhost.  So none of my FEs could connect.  

Ok, back to testing.

---

