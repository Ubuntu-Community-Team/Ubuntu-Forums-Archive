---
title: "slow slow download speeds 400 bytes per second!"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by namluc on 2009-04-29
Running 8.10 on a hp mini 1000, trying to upgrade and install other software but cant' owing to terrible download speeds. i have tried three things so far, all with no tangible improvement

1,
 [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

I have done this. no speed improvement

2,
[http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

i followed the steps in this but i don't seem to have disabled ipv6:

luke@luke-laptop:~$ ip a | grep inet6
    inet6 ::1/128 scope host 

3,
[http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)

i got my interfaces file, but it looked very spartan, and was missing the all important lines, having just these two,

auto lo
iface lo inet loopback

and so i haven't altered this one

many many thanks for your help in advance

---

