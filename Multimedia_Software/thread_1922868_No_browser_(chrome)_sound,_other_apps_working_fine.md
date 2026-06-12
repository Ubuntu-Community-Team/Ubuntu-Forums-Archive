---
title: "No browser (chrome) sound, other apps working fine?"
date: 2012-02-09
forum: Multimedia Software
---

### Post by e4xit on 2012-02-09
Hi,

Still a bit of a(n?) Ubuntu n00b so forgive me if it's obvious.

I am running 12.04 (stable alpha) after upgrading from 11.10.  I *had* everything working.  Now, however my browser is directing its sound out of my laptop speakers, whereas all the other applications I run are able to use my behringer UCA202 USB soundcard.

I presume that they work with it proves I have it installed correctly; chrome just isnt sending the sound to the right place!>?

I have tried to google, but most results turn up using:
pauvcontrol
alsamixer
a few others I've forgotten, which according to terminal I don't have installed and don't particularly want to install because I feel that having many sound drivers/control systems might be unstable.

If anyone has any ideas or needs any more info to help I would be most grateful.

Thx

Ubuntu love
x

edit: other notable factors - 11.10 used banshee rather than rhythmbox, perhaps this has affected it? I am using chrome NOT chromium (i believe)

---

### Post by e4xit on 2012-02-09
also, chrome does not show up in "sound settings" as an application using sound on either internal soundcard (through which it plays sound) or external soundcard...

might be noteworthy

---

### Post by Yellow Pasque on 2012-02-09
Try updating your packages. It's probably this bug: [https://bugs.launchpad.net/bugs/928980](https://bugs.launchpad.net/bugs/928980)

---

