---
title: "NIS client setup ok, login bad"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by pmatos on 2010-02-11
Hi,

I have set up karmic to be a NIS client of my company NIS servers. However, I cannot manage to login correctly. 

I can yptest and it passes all tests. I can
```
$ sudo ypcat passwd.byname | grep pm18
pm18:FGSZSXSDqUUVQ:2197:100:Paulo Matos:/home/pm18:/bin/bash
```

and my user shows up but then:
```
$ su pm18 
Password: 
su: Module is unknown
```

GDM also mentions that module is unknown but 'what module?'

[EDIT]
Managed to find that in fact I was just missing some required pam modules.
[/EDIT]


PMatos

---

### Post by pmatos on 2010-02-11
Hi,

I configured my karmic to connect to the company NIS server. However, even though I can ypcat the user database and see my user there when I actually try to login with my company username and password it says "Permission Denied".

I am out of idea on where to look for answers. I am also configuring Kerberos so it might have something to do with either of these. 

Any suggestions on where to look ?

PMatos

---

### Post by Iowan on 2010-02-11
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?
Congrats on finding a solution!

---

### Post by cariboo on 2010-02-11
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by pmatos on 2010-02-12
> **cariboo907 said:**
> Please don't create multiple threads on the same subject. I have merged your two threads.

But they do not actually pertain to the same subject. The issue is not completely different. Don't understand why the merge. Even though both are about NIS they are not about the same problem. Or do you also go around merging all threads about KDE?

---

