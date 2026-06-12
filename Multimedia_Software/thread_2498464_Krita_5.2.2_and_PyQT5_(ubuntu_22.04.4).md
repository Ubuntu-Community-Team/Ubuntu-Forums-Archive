---
title: "Krita 5.2.2 and PyQT5 (ubuntu 22.04.4)"
date: 2024-06-14
forum: Multimedia Software
---

### Post by trenien2 on 2024-06-14
Hi all,
I'm trying to use krita with its stable diffusion module, but I'm having unexpected troubles. It worked at first (standard ubuntu repository), but the module then disappeared for no apparent reasons. At that point, I tried to reinstall a more recent version of Krita (5.2.2) using an external PPA, but still no luck : the menu to load scripts just doesn't come up.
I've finally realised that there are problematic error messages when starting Krita :

```
krita.scripting: "Traceback (most recent call last):"krita.scripting: "  File \"/usr/lib/x86_64-linux-gnu/krita-python-libs/krita/__init__.py\", line 11, in <module>"
krita.scripting: "    from .api import *"
krita.scripting: "  File \"/usr/lib/x86_64-linux-gnu/krita-python-libs/krita/api.py\", line 15, in <module>"
krita.scripting: "    from PyKrita.krita import *"
krita.scripting: "ModuleNotFoundError: **No module named 'PyQt5.QtCore**'"
krita.scripting: "Could not import krita"

```

I've looked around but couldn't find anything specific related to that problem. As far as I'm able to see, the proper libraries are installed. I'm stumped

---

### Post by #&amp;thj^% on 2024-06-14
You have not mentioned weather this is installed or not.."pyqt5"

---

### Post by trenien2 on 2024-06-14
Well, yes, it is (hence my writing 'all the libraries are installed)

---

### Post by currentshaft on 2024-06-15
Try the Flatpak? [https://flathub.org/apps/org.kde.krita](https://flathub.org/apps/org.kde.krita)

---

### Post by #&amp;thj^% on 2024-06-15
> **trenien2 said:**
> Well, yes, it is (hence my writing 'all the libraries are installed)

A simple "Yes" or "No" would have sufficed, I can't tell you how many times a user has swore up and down something was installed when it wasn't...

Anywho, I find the appimage to work nicely on my end.

[https://mirrors.mit.edu/kde/Attic/krita/5.2.0/krita-5.2.0-x86_64.appimage](https://mirrors.mit.edu/kde/Attic/krita/5.2.0/krita-5.2.0-x86_64.appimage)

---

### Post by trenien2 on 2024-06-15
Well, sorry for cheekiness, then.
Apart from that, I tend to want to avoid flatpack (or any other similar ways to distribute software). The few times I tested any of them, they used a significant amount of ressources beyond that of a repository version.

Well, if anyone has any idea on how to make it known to krita that, yes, that specific library is indeed installed...

---

### Post by #&amp;thj^% on 2024-06-15
No worries.
Sadly both work here, both .deb krita and appimage.
I checked for "py mods" and found these were needed:
```
&#9492;&#9472;> apt policy python3-pyqt5 python3-pyqt5.sip
python3-pyqt5:
  Installed: 5.15.10+dfsg-1build6
  Candidate: 5.15.10+dfsg-1build6
  Version table:
 *** 5.15.10+dfsg-1build6 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status
python3-pyqt5.sip:
  Installed: 12.13.0-1build3
  Candidate: 12.13.0-1build3
  Version table:
 *** 12.13.0-1build3 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status

```
Krita version:
```
apt policy krita
krita:
  Installed: 1:5.2.2+dfsg-3build2
  Candidate: 1:5.2.2+dfsg-3build2
  Version table:
 *** 1:5.2.2+dfsg-3build2 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status

```
And sometime a simple --reinstall helps:
```
sudo apt install --reinstall python3-pyqt5 python3-pyqt5.sip
```

Please Note this was on 24.10 oracular

---

### Post by trenien2 on 2024-06-15
I didn't think of the reinstall. I'll give it a try, thanks.

---

### Post by currentshaft on 2024-06-16
> **trenien2 said:**
> Well, sorry for cheekiness, then.
Apart from that, I tend to want to avoid flatpack (or any other similar ways to distribute software). The few times I tested any of them, they used a significant amount of ressources beyond that of a repository version.

So you want to avoid an efficient way to package applications with their dependencies, because you once had an ambiguously poor experience with another application.

You have to ask yourself, is this position honestly even logically tenable?

---

### Post by trenien2 on 2024-06-17
Well, the reinstall did work.

Apart from that, the "efficient" way you're talking is, at the very least, a waste of space. When used for a majority of applications on a majority of PC, that is NOT minor. And since I've read here and there my 'once poor experience' was far from unique, I'll keep dong things as I have so far.

---

### Post by #&amp;thj^% on 2024-06-17
> **trenien2 said:**
> Well, the reinstall did work.



Thanks for the update, enjoy. ;)

---

### Post by currentshaft on 2024-06-17
> **trenien2 said:**
> Well, the reinstall did work.

Apart from that, the "efficient" way you're talking is, at the very least, a waste of space. When used for a majority of applications on a majority of PC, that is NOT minor. And since I've read here and there my 'once poor experience' was far from unique, I'll keep dong things as I have so far.

A terrabyte SSD is less than $100.

Frankly your argument against Flatpak is untenable.

---

