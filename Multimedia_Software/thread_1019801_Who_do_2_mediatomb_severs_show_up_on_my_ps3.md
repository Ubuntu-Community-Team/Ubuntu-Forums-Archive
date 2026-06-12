---
title: "Who do 2 mediatomb severs show up on my ps3"
date: 2008-12-23
forum: Multimedia Software
---

### Post by Kedster on 2008-12-23
so i wanted to stream music and pics and some movies to my ps3 so installed mediatomb. I went and started it to see what i had to do, i added a bunch of stuff ans then went on my playstation 3 and went to watch a video and it wouldn't let me, so i looked up how to fix it by following this [tutorial]("http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/"). then re-add the music and movies,But now on my ps3 i have 2 different "mediatomb" severs how can i get rid of the one that doesn't work

---

### Post by damis648 on 2008-12-23
Go to "Search for Media Servers". Once it only finds one, it will correct itself. If not, then you have two instances running on your computer. To fix that, press Alt+F2 and type in
```
killall mediatomb && mediatomb
``` and then search for servers once again.

---

### Post by Kedster on 2008-12-23
thats doensn't seem to have worked

---

### Post by Kedster on 2008-12-23
i noticed that if i try and open the gui part of mediatomb form the aplications menu it brings me to the one that does not work, so i am un able to add stuff or change anything in my database on the good one. when I run sudo mediatombin terminal i get this  ```
kedster@kedster:$ sudo mediatomb
[sudo] password for kedster: 

MediaTomb UPnP Server version 0.11.0 - http://mediatomb.cc/

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2008-12-23 14:33:26    INFO: Loading configuration from: /home/kedster/.mediatomb/config.xml
2008-12-23 14:33:26    INFO: Checking configuration...
2008-12-23 14:33:26    INFO: Setting filesystem import charset to UTF-8
2008-12-23 14:33:26    INFO: Setting metadata import charset to UTF-8
2008-12-23 14:33:26    INFO: Setting playlist charset to UTF-8
2008-12-23 14:33:26    INFO: Configuration check succeeded.
2008-12-23 14:33:26    INFO: Initialized port: 49153
2008-12-23 14:33:26    INFO: Server bound to: 192.168.1.101
2008-12-23 14:33:27   ERROR: SQLITE3: (5) database is locked
Query:UPDATE "mt_autoscan" SET "touched"=0 WHERE "persistent"=1 AND "scan_mode"='timed'
error: database is locked

```

---

### Post by damis648 on 2008-12-23
Why sudo it? Try killing it first:
```
sudo killall mediatomb
```
and then run as your normal user:
```
mediatomb
```

---

### Post by Kedster on 2008-12-23
sorry```
kedster@kedster:~$ mediatomb

MediaTomb UPnP Server version 0.11.0 - http://mediatomb.cc/

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2008-12-23 14:50:37    INFO: Loading configuration from: /home/kedster/.mediatomb/config.xml
2008-12-23 14:50:37    INFO: Checking configuration...
2008-12-23 14:50:37    INFO: Setting filesystem import charset to UTF-8
2008-12-23 14:50:37    INFO: Setting metadata import charset to UTF-8
2008-12-23 14:50:37    INFO: Setting playlist charset to UTF-8
2008-12-23 14:50:37    INFO: Configuration check succeeded.
2008-12-23 14:50:37   ERROR: Error while accessing sqlite database file (/home/kedster/.mediatomb/mediatomb.db): Permission denied
kedster@kedster:~$ 


```

---

### Post by damis648 on 2008-12-23
Ah ok sorry, never mind it looks like your config file is owned by root. Your problem is interesting. Have you tried restarting your computer and PS3?

---

### Post by Kedster on 2008-12-23
Ok sorry for the wait had to work, i shutdown twice and it worked sorta, they both turned off. but now i would like to figure out how to start mediatomb on start up

---

