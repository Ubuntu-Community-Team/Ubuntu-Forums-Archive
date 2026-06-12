---
title: "Mirror some folders between two ubuntu servers"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by couper on 2013-03-08
Hi
I have two server in different locations, they have internet connection.
Server A is the real server. Server B is for back-up.
I want to one-way mirror A to B some of the folder like var/www etc.
How can I do it?
Thanks

---

### Post by vanadium on 2013-03-08
rsync -av <source> <destination>

where both source and destination can also be remote locations, e.g.

rsync -av /home/user/data [email]user@remoteserver.com[/email]:/home/user/

The remote computer must be accessible with ssh. rsync uses an ssh connection.

---

### Post by couper on 2013-03-11
is there any program uses http connection?
My remote server has 80 port open only.

---

