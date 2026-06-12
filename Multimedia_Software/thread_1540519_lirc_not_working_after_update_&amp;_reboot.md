---
title: "lirc not working after update &amp; reboot"
date: 2010-07-27
forum: Multimedia Software
---

### Post by mythtv42 on 2010-07-27
I did the recomended updates and rebooted now the IR transcever no longer works
I get unknown remote

$ irsend SEND_ONCE DCT2000 OK
irsend: command failed: SEND_ONCE DCT2000 OK
irsend: unknown remote: "DCT2000"
$ ps -ef|grep lirc
root      1119     1  0 21:17 ?        00:00:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --driver=commandir --device='' '' --listen
root      1126     1  0 21:17 ?        00:00:00 /usr/sbin/lircd --output=/var/run/lirc/lircd1 --device=/dev/lircd --connect=localhost 8765 --pidfile=/var/run/lirc/lircd1.pid
root      1128  1119  0 21:17 ?        00:00:00 /usr/sbin/lircd --output=/var/run/lirc/lircd --driver=commandir --device='' '' --listen
root      2641  2605  0 21:20 pts/5    00:00:00 grep --color=auto lirc
$

How  to debug?

---

