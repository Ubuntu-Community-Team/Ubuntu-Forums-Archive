---
title: "globalmenu no longer works with qt programs?"
date: 2011-02-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by portis on 2011-02-20
I noticed that all qt programs (including goldendict, qterm, virtualbox, smplayer) don't show their menus either in the globalmenu or in their own window, even launched with UBUNTU_MENUPROXY="".

I remember that sometime ago qt programs had no problem showing their menus in the globalmenu.

Can anyone confirm it?

---

### Post by mc4man on 2011-02-20
> Can anyone confirm it?
They stopped using the gm quite some time ago, whether this is a bug or something that requires a qt app's developer's attention not sure (leaning towards latter

(myself am ok with, previously was switching it off on the couple of qt4 apps i use (smplayer, vlc, ..

---

### Post by portis on 2011-02-21
But the strange thing is, even UBUNTU_MENUPROXY="" won't get menus back.

---

### Post by mekmar on 2011-02-21
I confirm. There's probably some kind of regression. I'll try to fill bug report if necessary, later. There's little disorder, when it comes to packages' versions. Maybe after the next update everything will go back to normal.

---

### Post by portis on 2011-02-25
There's a new version of libdbusmenu-qt
[https://launchpad.net/libdbusmenu-qt/trunk/0.8.0](https://launchpad.net/libdbusmenu-qt/trunk/0.8.0)

It's not yet packaged.
I compiled it and now all qt menus are back.
Great!

---

