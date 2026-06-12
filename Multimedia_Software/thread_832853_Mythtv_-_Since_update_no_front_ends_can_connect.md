---
title: "Mythtv - Since update no front ends can connect"
date: 2008-06-18
forum: Multimedia Software
---

### Post by WhistlerUK on 2008-06-18
Since a critical update I ran last night on both backend and 1 frontend Hardy boxs both my hardy Frontend and Mac Front will no longer connect to the backend server.

Same Error on both frontends - "Cannot connect to backend server, is it running? Check IP"

I have checked over the backend server, port scan reveals SQL and myth ports are open, checked the passwords and database name these are fine.  I completely stumped at this as all that was done was a critical update.

Thinking of doing a fresh install on the myth backend box tonight, just wondered if any other Myth people have had problems with the lastest hardy updates?

UPDATE:  Started working again... think its because the update altered the listening IP back to the local loopback IP 127.*

---

