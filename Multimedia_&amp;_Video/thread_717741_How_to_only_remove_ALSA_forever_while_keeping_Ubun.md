---
title: "How to only remove ALSA forever while keeping Ubuntu-minimal?"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by krylon on 2008-03-07
Every time I try to apt-get remove alsa-base I lose ubuntu-minimal. I then proceed to apt-get install ubuntu-minimal and it installs ALSA again :mad::mad::mad:

I want to manually install alsa from source (to get the latest version).  How can I keep aptitude from installing alsa while installing a desktop environment?

---

### Post by krylon on 2008-03-10
bump

---

### Post by krylon on 2008-03-13
A lost cause?

---

### Post by RawMustard on 2008-03-13
Ubuntu Minimal is a meta package that pulls in alsa amongst other things, you cannot install Ubuntu Minimal and not have alsa.

The only thing you can do is install seperately what ubuntu minimal installs leaving out alsa.  You'll probably find it very hard to have an ubuntu system with no alsa as many programs require it in some way or another.

---

