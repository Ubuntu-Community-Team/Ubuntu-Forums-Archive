---
title: "Logitech Quickcam Not working/ Unable to cam/upload video on websites"
date: 2008-12-02
forum: Multimedia Software
---

### Post by toddrobb on 2008-12-02
Ok
Heres the problem; since I stalled Ubuntu 8.10 shockwave or flashplayer (which ever recognizes input from my cam) wont cant find my cam. I know my cam is working. I installed camerama and other programs to view my cam and they work. But Skype, Webdate, Tokbox, and other sites where i can use my cam to chat with others wont work. I dont know what to do. Please can someone help me. 
thank you

---

### Post by aquamammal on 2008-12-21
Same problem.

Any one??

---

### Post by Hello_World on 2008-12-21
u might try this one. helped for logitech and trust webcam, so good luck ;)

[http://www.atokar.net/index.php?topic=236.msg464;topicseen#msg464](http://www.atokar.net/index.php?topic=236.msg464;topicseen#msg464)

---

### Post by lnxpwr on 2008-12-21
used the script from the link and works like charm !!! thanx a lot for this hint !

```

#! /bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

```

---

