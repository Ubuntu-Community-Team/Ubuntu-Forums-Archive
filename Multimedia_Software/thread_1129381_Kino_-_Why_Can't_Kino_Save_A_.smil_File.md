---
title: "Kino - Why Can't Kino Save A .smil File?"
date: 2009-04-18
forum: Multimedia Software
---

### Post by umechanism on 2009-04-18
[B]Ubuntu 8.10
Dell Studio Desktop
Kino 1.3.3
Raw1394 Enabled via sudo chmod 777 /dev/raw1394[/B]

I'm using Kino for video capture from my Sony Hi8 / Digital8 camcorder.  I've noticed that any of the tapes recorded in Digital8 format are captured by Kino without any problems but those tapes recorded in Hi8 format are prone to crashing - often.  Also, when I do finally get a Hi8 tape transferred, and I try to save the project, Kino tells me that "The SMIL File Could Not Be Saved".

What is going on here?  Is there a Kino setting that I need to use for Hi8 tapes versus Digital8 formats?

Thanks!

---

### Post by cariboo on 2009-04-18
Are you running Kino as root? There is a problem with kino being compiled wrong, and you need to be root to do anything:

```
gksu kino
```

Jim

---

### Post by umechanism on 2009-04-18
Thank you for the fast reply.

No, I'm not running as root.  I've tried that in the past and it made downstream video editing and/or moving/deleting the files a bit of a pain.  Is that the solution?  Running as root?  

...but why do I not have this problem with Digital8 formats?

---

### Post by Ferrat on 2009-05-16
Well could be because D8 and Hi8 are different standards and even though your camcorder does record to Hi8 it really wants D8 because the D8 gives much more data, I'm guessing you are using the camcorder? 
Because specially in that case it would be like having a highway and only using one lane.
Say a traffic analyst was checking traffic patterns and with a D8 then all lanes are full of cars and so on the nothing weird about that, but the day after he comes back to the same highway and there is a single lane Hi8 in use?
Then he starts looking for the problem causeing the other lanes to be empty but since there is no cause they just arn't in use he keeps looking for the lost cars forever :P 

A bit messy descriptsion but you get the idea the camcorder probably sends all out but some parts are just white noise so when kino tries to put it all together it doesn't match like it should with parts missing or doing weird stuff = freeze

Just an idea

---

### Post by umechanism on 2009-05-16
Thanks for the reply.  Your explanation makes sense but I think my problem was that my hard drive was full.  duh!!

---

