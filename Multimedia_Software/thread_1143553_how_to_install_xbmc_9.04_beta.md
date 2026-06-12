---
title: "how to install xbmc 9.04 beta?"
date: 2009-04-30
forum: Multimedia Software
---

### Post by northwestuntu on 2009-04-30
i've been trying to get xbmc the latest release in to the repos to install with no luck.

[https://launchpad.net/~team-xbmc/+archive/ppa](https://launchpad.net/~team-xbmc/+archive/ppa)

deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) jaunty main

i add them and reload and they don't appear?

can anyone tell me how to get them in there?

---

### Post by kpkeerthi on 2009-04-30
After adding the repository entries, you need to
1. Import the PPA's keys to your system. Click on the link "Follow these instructions" on [https://launchpad.net/~team-xbmc/+archive/ppa]("https://launchpad.net/~team-xbmc/+archive/ppa") and scroll down to the section "Adding the keys using Gnome" and import the keys applicable for xbmc PPA as instructed.

2. After the key is imported successfully, run this command:
```
sudo apt-get update
``` *it should not complain about any GPG key errors.

3. Now you can search for xbmc from Applications -> Add/Remove and install it.

---

### Post by northwestuntu on 2009-04-30
thanks! i'll give that a try.

---

### Post by ercey on 2009-05-04
to view the xbmc package, I had to;

sudo update-apt-xapian-index

---

### Post by mac79 on 2009-05-09
> **ercey said:**
> to view the xbmc package, I had to;

sudo update-apt-xapian-index
confirmed

thank You

---

### Post by northwestuntu on 2009-05-11
what does this mean?

sudo update-apt-xapian-index

---

