---
title: "Mythbuntu 9.04 RC1 default mysql root pw?"
date: 2009-04-22
forum: Mythbuntu
---

### Post by whosmatt on 2009-04-22
I've searched all over for the answer -- fresh install 9.04 RC1.  I cannot login to mysql as root - blank password does not work, the mythtv user password of course works, but not for root....

what is the default root password?

-thanks,
matt

---

### Post by tgm4883 on 2009-04-22
Did you set a root password? 

IIRC, you can reset the root password by doing

```
dpkg-reconfigure mysql-server
```

---

### Post by whosmatt on 2009-04-22
I didn't set one; this is a completely fresh install and I never was prompted for mysql root pw. 
```
dpkg-reconfigure mysql-server
``` didn't do anything; it ran but was completely non-verbose

> **tgm4883 said:**
> Did you set a root password? 

IIRC, you can reset the root password by doing

```
dpkg-reconfigure mysql-server
```

---

### Post by whosmatt on 2009-04-22
nm, i figured it out.  it was my user password, the one for the user i set up during ubuntu install.

---

### Post by dannyboy79 on 2009-06-13
> **whosmatt said:**
> nm, i figured it out.  it was my user password, the one for the user i set up during ubuntu install.

thank gosh you posted this because I would've goggled for hours trying to figure this out. I think mythbuntu should leave it blank to start out with.

the root password for mysql after a fresh install of mythbuntu jaunty is the usernames password.

---

### Post by nasha on 2009-06-13
Its a fitting scenario for Ubuntu, since there is no root account...
In order to do something with root privs, you use sudo, and your sudo password is the same as your user password :)

---

### Post by dannyboy79 on 2009-06-13
> **nasha said:**
> Its a fitting scenario for Ubuntu, since there is no root account...
In order to do something with root privs, you use sudo, and your sudo password is the same as your user password :)

i am sorry but I completely disagree! We're talking about the root password for mysql not the root user password. This is by far from obvious expecially since this was different in previous versions of installing Mythtv.

Anyway, I digress.

---

