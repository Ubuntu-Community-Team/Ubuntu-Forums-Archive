---
title: "Looking for some multimedia software"
date: 2016-02-20
forum: Multimedia Software
---

### Post by jacatone on 2016-02-20
I'm using Ubuntu 14.04. I'm looking for some easy to use appz that'll combine video clips and convert clips to a playable DVD?

---

### Post by potato5 on 2016-02-20
My advice is to use kdenlive [https://kdenlive.org/](https://kdenlive.org/)

---

### Post by shane_faulkinbury2 on 2016-02-20
You might try Brasero or DeVeDe from the Ubuntu Software Center.

---

### Post by Linuxisfast on 2016-02-20
Try openshot 2.0 from its ppa @ [https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa](https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa)

---

### Post by Bucky Ball on 2016-02-20
Kino? Kdenlive drags in a HEAP of dependencies and KDE stuff. Bloaty.

Kino is in the repositories so Software Centre is the go. Just uninstall if you don't like. If you don't like KDEnlive, you will need to completely remove/purge using either Synaptics or Software Centre. With anything you've installed, once uninstalled, open a terminal and:

> sudo apt-get autoremove

... to kill any cruft. Kdenlive will probably leave plenty (of stuff related to KDE/Kubuntu which I don't think you're running and certainly won't need).

(Having said that, I'd give KDEnlive a shot if nothing else is working for you. It works fine but may not do what you are after.)

---

