---
title: "tangerine and itunes share"
date: 2012-11-30
forum: Multimedia Software
---

### Post by chet9119 on 2012-11-30
Hi all:

I'm trying to setup an Ubuntu (11.10) share with tangerine.  Itunes on the Winows 7 PC shows the shared directory but not the files inside.  I installed Banshee on the widows machine, but that does not even display the shared ubuntu directory.

I previously tried forked-daapd, which was able to show and play files in Itunes, but would stop playing after about 5 minutes.  It appears that I broke something when removing that package.

Any ideas would be appreciated.

---

### Post by svennegan on 2013-01-06
Hi chet9119,
i'm also struggling with forked-daapd. I didn't find any solution for that. This doesn't work for me -> [http://www.mmacleod.ca/blog/2012/05/patching-forked-daapd-so-it-actually-works/](http://www.mmacleod.ca/blog/2012/05/patching-forked-daapd-so-it-actually-works/)

/var/log/forked-daapd.log says:

> [2013-01-04 23:21:59]    httpd: Connection closed; stopping streaming of file ID 29
[2013-01-04 23:21:59]    httpd: Connection failed (fd 22)

iTunes still stops playing after 5  minutes.

Now i try tangerine. i had the same problem. I can see the share, but no songs. After i read the log-file (.tangerine-log) i changed the name of the share. Initially it was something like "svennegan's Music". I changed it to "svenneganMusic" (no apostrophe, no blank). Now it works.

Hope it helps

---

### Post by Stephen_at on 2013-03-09
forked-daap is broken for serveral linux media players and Itunes - there seems to be a fix for it but it doesn't seem to have made it over to Ubuntu. Its a complete pain to be honest. The original mt-daapd was far from perfect but the forked version is a pale imitator and is much slower and has a lot less features.

---

