---
title: "Mplayer Removal"
date: 2010-03-27
forum: Multimedia Software
---

### Post by poroian on 2010-03-27
I downloaded mplayer, but not completely installed, using the command line:

svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

on the mplayer website. It created a new directory, but didn't install anything that I can run from command line. The folders this created are locked for root so I can't change permissions. How do I remove these files?

---

### Post by coolcaseley67 on 2010-03-27
Hi 

-try removing it use spc manger  in System , admin 
- what folder is it install in ??


hope it helps

---

### Post by andrew.46 on 2010-03-27
Hi poroian,

> **poroian said:**
> I downloaded mplayer, but not completely installed, using the command line:

svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

on the mplayer website. It created a new directory, but didn't install anything that I can run from command line. The folders this created are locked for root so I can't change permissions. How do I remove these files?

It would only be owned by root if you appended the *sudo* command to the svn checkout command, or perhaps have you started the *./configure / make* process as sudo as well? In either case you can navigate to the directory containing the exported MPLayer source code and run this command:

```
sudo chown -R username:username
```

where you will have to change *username* to your own username, if you are unsure exactly what this is on your machine the following will reveal it:

```

echo "$USER"

```

Then you can delete the directory containing the exported svn MPLayer source code and all the files it contains as an ordinary user.

Andrew

---

