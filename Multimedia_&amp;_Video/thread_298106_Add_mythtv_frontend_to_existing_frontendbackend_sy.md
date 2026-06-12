---
title: "Add mythtv frontend to existing frontend/backend system"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by Lem on 2006-11-12
I have a combined frontend/backend system that works fine. However, I'd like to be able to run a mythfrontend from my desktop machine into the same machine. (Ideally I'd like to not have to change my username on this machine to mythtv)

I'm running 0.20  from the repositories. Everything is currently set to point at 127.0.0.1 , but if try to change this to 192.168.1.5 I lose my exisiting frontend/backend connection even if I point the frontend to the same address.

Anyway, it's sunday morning and I have a hangover, so if anyone has done this before I'd be extremely grateful for some information!

My head hurts..

---

### Post by superm1 on 2006-11-12
You have to make sure your mysql server isn't only configured to listen on 127.0.0.1.

check /etc/mysql/my.cnf for a bindaddress line.  Just comment this out and restart mysql server.

---

### Post by Lem on 2006-11-20
Sorted.. thank you!

---

