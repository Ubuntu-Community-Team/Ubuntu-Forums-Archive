---
title: "Problems installing Gstreamer plugins on 7.04 32bit version"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by darrellfjohnson on 2007-04-23
I've tried to download them both from inside MPlayer, and in the Add/Remove menu and I get the same error message which says:

```
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
```

Are the servers down, or is there something wrong with my system?

Thanks in advance for any help.

---

### Post by darrellfjohnson on 2007-04-23
bump

---

### Post by lars.vaerland on 2007-04-23
> **darrellfjohnson said:**
> I've tried to download them both from inside MPlayer, and in the Add/Remove menu and I get the same error message which says:

```
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
```

Are the servers down, or is there something wrong with my system?

Thanks in advance for any help.

im trying to find a solution to this too. anybody got a hint?

---

### Post by darrellfjohnson on 2007-04-28
I'm still having a problem with this, even after I've made a new sources file with that thing online that will help you.

Are the servers just down or getting hit heavily because of the new release or something?

---

### Post by darrellfjohnson on 2007-04-28
A cool forum staff member called Taurus fixed my problem.  Here is what he told me to do:

First run this in the terminal.

```
gksudo gedit /etc/apt/sources.list
```

and remove the us. from all your repos. Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

