---
title: "problem with port 21 and proftpd"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by dvirdc on 2009-09-02
after i found this:
[http://www.uluga.ubuntuforums.org/showthread.php?p=7883453](http://www.uluga.ubuntuforums.org/showthread.php?p=7883453)

and waited 24hrs for an answer, ive decided to repost it.

can anyone help please?

thank you guys

---

### Post by dvirdc on 2009-09-03
HEY
[SOLVED]

so here's what i did:
1) logged in as root and netstat -tlnp (you must be root to see the PID and process name)
2) kill the PID that uses the port (21).
3) restart proftpd and check that it uses port 21 :)
4) go to /etc/inetd.conf (inetd was the process that uses port 21 on my machine)
5) "#" on the FTP line
6) restart and enjoy the netstat -tlnp

thanks

---

