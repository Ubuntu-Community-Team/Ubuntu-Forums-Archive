---
title: "Hi, ive fiddled with my graphic card defenitions and now the screen is unreadable"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by test for echo on 2008-04-05
ive installed linux ubuntu  a couple of days ago .
 it ran well until ive decided to change my graphic card defenition and from that point my screen is all blurry and cant understand anything.

what should i do? (novice)](*,)

p.s.
good thing i made a duel boot :-)

---

### Post by tamoneya on 2008-04-05
look for a backup of your xorg.conf file.  These are located in /etc/X11/.  If the is a file by the name of xorg.conf.backup or  xorg.conf.1 or something of that nature replace xorg.conf with the backup file.  Also what are you system specs.  Specifically Nvidia or ATI.

---

### Post by test for echo on 2008-04-05
well, I'm an absolute beginner to Linux so i first i have to study all the CLI commands in order to do what you've suggested (unless theres another way maybe)

any way , my computer specs are:
AMD athlon 64 X2 6000+ 3.00GHZ
2GB ram
and yes... ATI RADEON HD3850

---

### Post by p_quarles on 2008-04-05
Moved to Multimedia & Video.

---

### Post by test for echo on 2008-04-16
> **tamoneya said:**
> look for a backup of your xorg.conf file.  These are located in /etc/X11/.  If the is a file by the name of xorg.conf.backup or  xorg.conf.1 or something of that nature replace xorg.conf with the backup file.  Also what are you system specs.  Specifically Nvidia or ATI.
worked like charm. thanx a lot!

---

