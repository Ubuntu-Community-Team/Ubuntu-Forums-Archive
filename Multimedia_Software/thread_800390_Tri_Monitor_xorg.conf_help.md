---
title: "Tri Monitor xorg.conf help"
date: 2008-05-19
forum: Multimedia Software
---

### Post by Chris_Robb on 2008-05-19
Hi all, I', just new to this forum, and it certainly seems like a helpfull place. I've just recently finished upgrading my computer, and with it I though I'd give the new Ubuntu a try and see how it feels. After using a few distro's in the past I must say it certainly is impressive even just with the included packages without much tinkering! The one thing that is stopping me using it 24/7 though is that I cannot get my three monitor setup to work in xorg.conf :(

I have spent considerable time playing about and reading up on different people's similar problems trying to piece together something that will work but keep failing. I'm using 2 Radeon HD3450's and have the fglrx drivers working fine with hardware accelleration for the first card with one monitor running. I can also get both monitors working and setup for dual desktop setup using

aticonfig --initial=dual=head,
and then aticonfig dtop=horizontal

The most successefull so far seems to be to set this up, then looking at the two device entries in xorg.conf (one for each monitor output on PCI 1:0:0) if I change the second one (screen 1) to PCI 2:0:0 (the location of my other card [found using lspci) then when I reboot all three screen lights come on but only blank screens.

Can anyone offer any suggestions? I can post my current xorg.conf that puts the three of them on but not displaying anything, and also my lspci list along with anything else, and if someone is willing to help I'd really appreciate it.

Chris

---

### Post by Chris_Robb on 2008-05-20
This is the official Ubunutu forums, surely someone is willing to help?

---

### Post by Chris_Robb on 2008-05-21
Bump, surely someone must be able to help?

---

### Post by Chris_Robb on 2008-05-26
Ttt

---

### Post by Chris_Robb on 2008-05-27
TTT again.

---

