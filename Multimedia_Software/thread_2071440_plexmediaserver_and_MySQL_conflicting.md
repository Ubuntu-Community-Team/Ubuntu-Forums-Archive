---
title: "plexmediaserver and MySQL conflicting?"
date: 2012-10-15
forum: Multimedia Software
---

### Post by chadwickm on 2012-10-15
Hello,

I'm trying to build my first HTPC and am new to Linux. I'm learning by checking out various tutorials online. Everything went great in the process of setting up Plex Media Server, but now I've moved on to the second phase of my project: setting up a web server on this same PC.

I'm attempting to install MySQL and phpMyAdmin. I installed MySQL by running:

```
apt-get install mysql-client mysql-server
```

However, when I went in to edit "/etc/init.d/mysql", it is a copy of "/etc/init.d/plexmediaserver". So whenever I try to run MySQL, Plex Media Server starts up.

I'm using the latest version of Plex (v0.9.6.9) and Ubuntu Desktop 12.04.

Could I just find a default copy of "/etc/init.d/mysql", paste it on top of mine, and all would be well?

Chad

---

