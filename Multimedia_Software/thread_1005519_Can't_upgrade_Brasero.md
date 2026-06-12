---
title: "Can't upgrade Brasero"
date: 2008-12-08
forum: Multimedia Software
---

### Post by notquitestr8t on 2008-12-08
I bought a new DL DVD writer. The current version of Brasero does not support DL. I tried to upgrade to 8.0.3 but I'm not sure how. The apt-get install only gives me the old version. Package manager doesn't allow me to mark Brasero for an upgrade. I've downloaded the new version but not sure how to get it to install. Running Ubuntu 8.0.4. I'm a newbie so hopefully this is just something I need to learn.

---

### Post by barisurum on 2008-12-08
First of all are you sure the newest version of brasero supports your hardware? If not it is pointless to upgrade at all.
You can find the ubuntu packages of newest versions here: [http://www.getdeb.net/search.php?keywords=brasero](http://www.getdeb.net/search.php?keywords=brasero)
Download the package, check to see if its the same architecture as your computer ie. 32 bit or 64 bit and install it by double clicking.
If this doesn't solve the problem I recommend giving k3b a chance. It's a bigger app with lots of features. Install it using synaptic.> Package manager doesn't allow me to mark Brasero for an upgrade
The newest versions of programs don't allways be in the software repos. This way malfunctioning apps are kept to a minimum as new features may mean new bugs.
I hope this solves your problem.

---

### Post by binbash on 2008-12-08
[http://www.getdeb.net/app/Brasero](http://www.getdeb.net/app/Brasero)

---

### Post by notquitestr8t on 2008-12-08
Thanks for your help! That did the trick!

---

### Post by JPorter on 2008-12-08
> **notquitestr8t said:**
> I bought a new DL DVD writer. The current version of Brasero does not support DL. I tried to upgrade to 8.0.3 but I'm not sure how. The apt-get install only gives me the old version. Package manager doesn't allow me to mark Brasero for an upgrade. I've downloaded the new version but not sure how to get it to install. Running Ubuntu 8.0.4. I'm a newbie so hopefully this is just something I need to learn.

Have you considered upgrading to the current OS?  Ubuntu 8.10 has Brasero 0.8.2 in the repos, which is the latest (announced) stable release according to the Brasero project site at [http://projects.gnome.org/brasero/](http://projects.gnome.org/brasero/).  That version was only released in September so the adoption into repos was very rapid.

0.8.3 is apparently in a release state as of Nov 9 on the Gnome.org ftp.  The changelog doesn't indicate anything about dual-layer compatibility in the last few releases though.


[edit]  Oops! Just saw you got the GetDeb version. Good stuff.

---

