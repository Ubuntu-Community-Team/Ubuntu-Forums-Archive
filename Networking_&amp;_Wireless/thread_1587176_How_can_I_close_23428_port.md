---
title: "How can I close 23428 port?"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by kg356 on 2010-10-03
Hi, I have lots of  blocked connections in firestarter on 23428 port. Sometimes there was 2 blocked connections per second, then firestarter can use 100% cpu. I was downloading  lots of data yesterday via bittorrent, but I don't have any bittorrent client running at the moment. Now, when I'm writing this post, there has been no attack on this port from 15 minutes to now on. (I was trying to reconnect, cuz update-"something"-xapi started to use 100% cpu. I don't remember full name of this process). Does anyone know how to close this port/service or how to close it via sysv-rc-conf (what's the name of this service).

---

### Post by pytheas22 on 2010-10-03
If you were running a torrent client, that's probably what was causing the connections on that port: it's very unlikely anything you need to worry about.  But if you really want to block it, you can do so easily via [ufw]("https://help.ubuntu.com/community/UFW") with the command:

```
sudo ufw enable
sudo ufw deny 23428

```

You should also be able to do it through Firestarter if you want a GUI.

Note also that other hosts may have been making connections on that port even after you closed your torrent client, because they might have been trying to share torrent files with you.  They weren't "attacking"; they just didn't know you no longer had the torrent client open.

---

