---
title: "gmusicbrowser stuck on shuffle"
date: 2014-02-28
forum: Multimedia Software
---

### Post by r.stiltskin on 2014-02-28
Isn't there any way to turn off "shuffle queue" on gmusicbrowser 1.1.10? 

At the bottom of the window I turned off shuffle/random so it now shows a -> z but that doesn't seem to have any effect on what's playing, and the shuffle button at the bottom of the queue panel seems dead.

Alternatively, what other music players do you like on Xubuntu systems?  I've always like Amarok, but installing that brings along a huge entourage of KDE programs & I'd rather try to keep this box "relatively pure" xfce.

---

### Post by Yellow Pasque on 2014-03-01
Before giving up on gmusicbrowser, you can try resetting the configuration (perhaps something got corrupted?):

```
cd ~/
tar czf gmbrbackup.tar.gz .config/gmusicbrowser/*
rm -r ~/.config/gmusicbrowser/*
gmusicbrowser
```

If you find that resetting does not fix your issue and you want to go back to your old config, restore the old files:
```
cd ~/
rm -r ~/.config/gmusicbrowser/*
tar xzf gmbrbackup.tar.gz
gmusicbrowser
```

---

### Post by r.stiltskin on 2014-03-01
Thanks.  Actually this was a clean new installation of Xubuntu 13.10 and I have gmusicbrowser only because it was part of the distro.  I hadn't done any configuration to it.  I did try dpkg-reconfigure anyway, and when that didn't help I completely removed and installed gmusicbrowser again.  So I really have no investment in this program, and first impression was that it's unnecessarily cluttered-up anyway.

With a little googling I found Clementine and decided to try it.  It's a fork of Amarok but strangely it installs with just a small handful of dependencies, unlike the 100-or-so packages that apt wants to install with Amarok.  I like it.  It doesn't cook dinner, but it seems to do whatever a music player needs to do.

---

### Post by Yellow Pasque on 2014-03-01
Yes, Clementine is a good one and it moved away from KDE-specific technology to just plain Qt. I personally use Audacious, but that's a bit too minimal for some.

---

