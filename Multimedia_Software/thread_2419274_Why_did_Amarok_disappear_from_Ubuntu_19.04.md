---
title: "Why did Amarok disappear from Ubuntu 19.04?"
date: 2019-05-19
forum: Multimedia Software
---

### Post by iyagicom on 2019-05-19
Amarok disappeared and wrote other things, but I could not find anything better.
What is the reason?


Why do you delete a program you are using well?

How do I install Amarok?

[COLOR=#000000][FONT=Helvetica]put in the following.[/FONT][/COLOR]
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main universe

---

### Post by PaulW2U on 2019-05-19
> **iyagicom said:**
> Amarok disappeared and wrote other things, but I could not find anything better.
What is the reason?
Amarok was a Qt 4 application and for that reason it was removed from Ubuntu. All applications that do not use the Qt 5 toolkit are also being removed from Ubuntu (and Debian).

See the following links for further information:

[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/1757590](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/1757590)
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=874811](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=874811)
[https://wiki.debian.org/Qt4Removal](https://wiki.debian.org/Qt4Removal)

---

### Post by PaulW2U on 2019-05-19
> **iyagicom said:**
> [COLOR=#000000][FONT=Helvetica]put in the following.[/FONT][/COLOR]
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main universe
You edited your post after I posted.  :)

Mixing release repositories in that way might cause you more problems than you solve.

You could look for a PPA. [https://launchpad.net/~joe-yasi/+archive/ubuntu/amarok-kde5](https://launchpad.net/~joe-yasi/+archive/ubuntu/amarok-kde5) is just one I found specifically for the Disco release. There is always a risk in using such PPAs but it'll much safer than the method you might have already implemented.

---

### Post by SeijiSensei on 2019-05-19
Clementine was the official KDE successor to Amarok. You might try that.

```
sudo apt update; sudo apt install clementine
```

---

### Post by Yellow Pasque on 2019-05-20
> **SeijiSensei said:**
> Clementine was the official KDE successor to Amarok.

Clementine was a fork of Amarok 1.x from the KDE3 days. IIRC, it was not officially a part of KDE4 (Amarok 2.x was the successor).

Nowadays, I use strawberry (a Qt5 fork of Clementine): [https://www.strawbs.org/](https://www.strawbs.org/)
Clementine never officially released a Qt5 version, so it looks like Ubuntu 19.04 is using a git snapshot of Clementine with Qt5 support so they didn't have to remove it from the repo.

---

### Post by deadflowr on 2019-05-20
> Nowadays, I use strawberry (a Qt5 fork of Clementine): [https://www.strawbs.org/](https://www.strawbs.org/)
I see they have it snapified (made up that word, I guess) already:
[https://snapcraft.io/strawberry]("https://snapcraft.io/strawberry")

---

