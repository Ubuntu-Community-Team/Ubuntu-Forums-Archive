---
title: "Pulseaudio doesn't work after some time"
date: 2010-06-08
forum: Multimedia Software
---

### Post by just_another_user on 2010-06-08
Hi,

during recent days I have sound problem at my laptop with Ubuntu 10.04.

After some time of working sound is just stops working. Don't do anything special, once I was watching youtube videos, another time just leave my laptop for 6-8 hours and after returning I found that sound doesn't work.

Response to 
```
cat /var/log/syslog | grep pulse
```
is empty

in messages there are lines:
```

(/var/log) miro-laptop $ cat messages | grep pulse
Jun  6 12:05:12 miro-laptop pulseaudio[1623]: ratelimit.c: 261 events suppressed
Jun  6 21:44:50 miro-laptop pulseaudio[1623]: ratelimit.c: 726 events suppressed
Jun  7 14:20:55 miro-laptop pulseaudio[1606]: ratelimit.c: 2 events suppressed
Jun  7 23:45:41 miro-laptop pulseaudio[1606]: ratelimit.c: 436 events suppressed
Jun  8 00:04:50 miro-laptop pulseaudio[5975]: ratelimit.c: 2 events suppressed
Jun  8 07:44:00 miro-laptop pulseaudio[1613]: ratelimit.c: 2 events suppressed


```

After logging off and then on doesn't help, after rebooting everything works fine.

Tried to kill pulseaudio 
```
killall pulseaudio
```
it was killed successfully and restored itself with new pid, but still didn't work.

Also tried to reinstall pulseaudio without any success.

Laptop: compaq presario cq61 with Ubuntu 10.04 x64

this problem appeared only recently, some recent updates are:


```

Commit Log for Thu Jun  3 13:08:12 2010


Upgraded the following packages:
libsnmp-base (5.4.2.1~dfsg0ubuntu1-0ubuntu2) to 5.4.2.1~dfsg0ubuntu1-0ubuntu2.1
libsnmp15 (5.4.2.1~dfsg0ubuntu1-0ubuntu2) to 5.4.2.1~dfsg0ubuntu1-0ubuntu2.1
linux-headers-2.6.32-22 (2.6.32-22.33) to 2.6.32-22.35
linux-headers-2.6.32-22-generic (2.6.32-22.33) to 2.6.32-22.35
linux-image-2.6.32-22-generic (2.6.32-22.33) to 2.6.32-22.35
linux-libc-dev (2.6.32-22.33) to 2.6.32-22.35
snmp (5.4.2.1~dfsg0ubuntu1-0ubuntu2) to 5.4.2.1~dfsg0ubuntu1-0ubuntu2.1


```

```

Commit Log for Fri Jun  4 10:12:20 2010


Upgraded the following packages:
linux-headers-2.6.32-22 (2.6.32-22.35) to 2.6.32-22.36
linux-headers-2.6.32-22-generic (2.6.32-22.35) to 2.6.32-22.36
linux-image-2.6.32-22-generic (2.6.32-22.35) to 2.6.32-22.36
linux-libc-dev (2.6.32-22.35) to 2.6.32-22.36


```

```

Commit Log for Tue Jun  8 08:14:28 2010


Upgraded the following packages:
indicator-appmenu (0.0.3-0lucid1) to 0.0.4-0ubuntu1
openoffice.org-base-core (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-calc (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-common (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-core (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-draw (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-emailmerge (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-gnome (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-gtk (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-impress (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-math (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-style-human (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-writer (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
python-uno (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
ttf-opensymbol (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
uno-libs3 (1.6.0+OOo3.2.0-7ubuntu4) to 1.6.0+OOo3.2.0-7ubuntu4.1
ure (1.6.0+OOo3.2.0-7ubuntu4) to 1.6.0+OOo3.2.0-7ubuntu4.1

Installed the following packages:
bamfdaemon (0.2.26-0ubuntu1)
libbamf0 (0.2.26-0ubuntu1)


```

What else may be done to solve such a problem?

thanks

---

