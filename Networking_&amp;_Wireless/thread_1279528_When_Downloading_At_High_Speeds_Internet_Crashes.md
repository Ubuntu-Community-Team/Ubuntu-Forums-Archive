---
title: "When Downloading At High Speeds Internet Crashes"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by jdorenbush on 2009-09-30
I've never had this problem with Windows, I only notice on Ubuntu.

When I am downloading large files at high speeds I frequently see my Internet connection crash. My downloads will drop to 0KB and my browser stops loading websites, etc. My networking icon in the tray still shows a connection, but I can not actually interact with anything on the Internet.

I usually have to wait awhile for things to "fix" themselves or reboot my modem/router to fix.

Any ideas what might be causing this?

---

### Post by _Narcisse_ on 2009-10-01
Maybe it's related to [my problem]("http://ubuntuforums.org/showthread.php?t=1278986"). Does it happen when you're using bittorrent ?
EDIT : Also, what's your router model ?

---

### Post by A_Fiachra on 2009-10-01
Dude!


You crashed the internet!!!!!

:P


Do a speed test --- google speed test

---

### Post by ApEkV2 on 2009-10-01
How long do you have to wait? It might be related to built in anti-DOS features in your modem or router. 
Some of those features are sensitive to high transfer speeds. How fast is your connection.

---

### Post by jdorenbush on 2009-10-01
Connection: Highspeed cable, 5MB-10MB download
Actual Download Speed: 500KB-1MB
Torrent Software: Transmission
Router: Netgear WGT624v2

> **ApEkV2 said:**
> How long do you have to wait? Maybe 5-10 minutes?

---

### Post by ApEkV2 on 2009-10-01
> 
Actual Download Speed: 500KB-1MB
Torrent Software: Transmission
Router: Netgear WGT624v2
Maybe 5-10 minutes?

Some routers can't handle more than 50 connected peers at a time, and having that kind of connection speed, Transmission probably gives you alot of peers.
The next time you torrent, maybe try limiting the maximum number of peers and see if the problem still happens.

---

### Post by jdorenbush on 2009-10-21
I think it was actually a bad router. I was using a 3-4 year old Netgear router and a technician said that routers usually only last a few years (not sure if this is actually true), but we got a new WRT310N Linksys router and so far I have experienced no connectivity problems.

---

