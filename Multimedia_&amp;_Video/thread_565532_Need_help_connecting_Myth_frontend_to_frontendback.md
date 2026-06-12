---
title: "Need help connecting Myth frontend to frontend/backend"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by roazena on 2007-10-02
I have a front/backend that's been running fairly reliably for some time now. I recently purchased a cheap 800MHz PIII Dell GX150 with 256Mb/10Gb and set it up as a desktop install with the mythtv-frontend packages. 

It keeps giving "Could not connect to the backend" errors after configuring, even though every instance of mysql.txt seems to have the correct IP/username/password info.

The backend has had its config changed to the IP, the "127.0.0.1 bind" line in mysql.cnf has been commented out and the MySQL server restarted, but I'm at a loss as to what else needs doing.


I have another question. The living room frontend/backend is our master backend. Once the bedroom frontend is working, we want to put a PVR-150 into it and use it to watch live TV as well as pull recordings off the master backend. Has anyone here had success doing this?

---

### Post by tgm4883 on 2007-10-02
> **roazena said:**
> I have a front/backend that's been running fairly reliably for some time now. I recently purchased a cheap 800MHz PIII Dell GX150 with 256Mb/10Gb and set it up as a desktop install with the mythtv-frontend packages. 

It keeps giving "Could not connect to the backend" errors after configuring, even though every instance of mysql.txt seems to have the correct IP/username/password info.

The backend has had its config changed to the IP, the "127.0.0.1 bind" line in mysql.cnf has been commented out and the MySQL server restarted, but I'm at a loss as to what else needs doing.


I have another question. The living room frontend/backend is our master backend. Once the bedroom frontend is working, we want to put a PVR-150 into it and use it to watch live TV as well as pull recordings off the master backend. Has anyone here had success doing this?

Hmm, don't know the answer to your first questions.

But to your second question, you need to set up your bedroom system as a frontend/backend (secondary backend).  Then it will function just as the other backend does, allowing it to both watch tv and record.  Shows will stream between the two when needed.

---

### Post by roazena on 2007-10-02
Some googling indicates the bedroom machine needs to be configured as a slave backend. I'll cross that bridge when I come to it, but I'm still perplexed as to what hasn't been configured properly to get the bedroom frontend to talk to the living room master backend.

---

