---
title: "Frontend cannot find backend"
date: 2008-07-17
forum: Mythbuntu
---

### Post by bt224 on 2008-07-17
Ok, I just installed MythTV. Everything seemed to go just fine. I have another machine that I installed a frontend. I keep getting an error message saying No UPnP backends found. I enabled SQL etc in the setup. Any ideas?

---

### Post by klc5555 on 2008-07-18
In addition to setting the database on the backend for remote access rather than standalone, (what I assume you meant by "SQL etc.") the ip addresses used for the backend on the server hosting the backend have to be changed all from the default 127.0.0.1 (localhost) to the actual ip address in whichever ip addressing scheme your LAN is using for the backend server (something from 192.168.0.x, or 10.0.2.x range, most likely). This ip address then also has to be entered into the frontend's General Setup screen where it asks for the location of the database (in place of the default 127.0.0.1), along with the myth user password from the backend. 

And then you should be in business, unless there are odd routing issues because one of the machines are on a different subnet of your LAN, or some such.

Good luck!:)

---

