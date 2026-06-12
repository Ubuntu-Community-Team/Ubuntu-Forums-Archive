---
title: "irexec will not run"
date: 2016-01-13
forum: Mythbuntu
---

### Post by rdege on 2016-01-13
[FONT=arial]I'm running mythbuntu 14.04.3 LTS (64bit).  LIRC is running with no issues, but I'm unable to get irexec to run:

# lircd -v && irexec -v
lircd 0.9.0
irexec 0.9.0


# sudo irexec /etc/lirc/lircrc
irexec: could not connect to socket
irexec: No such file or directory



The lircrc config file points to $USER/.lirc/mythtv

# ls -l /etc/lirc/lircrc
lrwxrwxrwx 1 root root 24 Jan 12 20:19 /etc/lirc/lircrc -> /home/rob/.lirc/mythtv



The only oddity that I notice is that there's two session of lirc running, with two pid files:
[/FONT]
[FONT=arial]# ps -aef | grep lirc[/FONT]
[FONT=arial]root      3356     1  0 21:29 ?        00:00:02 /usr/sbin/lircd --output=/dev/lircd --driver=devinput --device=phys=usb-0000:00:04.[/FONT][FONT=arial]0-1/input1 --listen --pidfile=/run/lirc/lircd1.pid[/FONT]
[FONT=arial]root      3358     1  0 21:29 ?        00:00:00 /usr/sbin/lircd --output=/dev/lircd --driver=devinput --device=phys=usb-0000:00:04.[/FONT][FONT=arial]0-3/input0 --connect=localhost 8765[/FONT]

---

### Post by rdege on 2016-01-13
The socket location was the problem. In /etc/lirc/hardware.conf, I set REMOTE_SOCKET="/dev/lircd". Even though /dev/lircd was a soft link to /var/run/lirc/lircd, irexec was failing since it wasn't following the sym link. I updated the REMOTE_SOCKET variable to point to /var/run/lirc/lircd, and now it works fine.

---

