---
title: "Help - stand alone install pointing at wrong computer??"
date: 2010-12-01
forum: Mythbuntu
---

### Post by dabone on 2010-12-01
I've got 3 mythbuntu systems in the house all configured as standalone systems, but when I went to my bedroom today, I had no guide data, so I was trying to update.
I went and installed the repos and did a upgrade, but it seems that it pulled the ip address for another one of my mythboxes.

(Ok, edit it seems by putting my ip address in instead of using 127.0.0.1 it decided to become a slave backend, now I need it stand alone again)

I'm on 10.04

My machine that is broken that I need up is 192.168.2.19
The older broken install that it decided to point to is 192.168.2.13.
Everytime I start mythfrontend it changes the config.xml to read 192.168.2.13...

And when I run mythtv-setup it seems to be looking at the wrong machine.

How do I correct this???
Help please. I also just tried to install phpmyadmin and selected the wrong webserver. (Can't seem to uninstall that and select apache2)

Thanks, 
dabone
```
2010-12-01 21:05:39.868 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2010-12-01 21:05:39.886 MythBackend: Starting up as the master server.
2010-12-01 21:05:39.904 New DB connection, total: 2
2010-12-01 21:05:49.638 Connected to database 'mythconverg' at host: 192.168.2.13
2010-12-01 21:05:49.665 New DB connection, total: 3
2010-12-01 21:05:59.639 Connected to database 'mythconverg' at host: 192.168.2.13
2010-12-01 21:06:01.590 New DB scheduler connection
2010-12-01 21:06:09.904 Connected to database 'mythconverg' at host: 192.168.2.13
2010-12-01 21:06:11.717 Main::Registering HttpStatus Extension
2010-12-01 21:06:11.759 Enabled verbose msgs:  important general
2010-12-01 21:06:11.793 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-12-01 21:06:14.715 Reschedule requested for id -1.
2010-12-01 21:06:14.857 Scheduled 2 items in 0.1 = 0.03 match + 0.11 place
2010-12-01 21:06:14.882 Seem to be woken up by USER

```(p.s. I'm hoping for a quick resolution to this before my wife kills me.)

---

### Post by tgm4883 on 2010-12-01
If you want stand alone systems, why did you stop using 127.0.0.1?

---

