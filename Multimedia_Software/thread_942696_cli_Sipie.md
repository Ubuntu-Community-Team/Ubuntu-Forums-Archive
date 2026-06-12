---
title: "cli Sipie"
date: 2008-10-09
forum: Multimedia Software
---

### Post by nixIT on 2008-10-09
greetings.

long time reader, first time poster.  I've been catching up on my reading about Sipie, and I have the gui version working.  However, I would like to get the cli version of sipie working but am having no luck.

Can anyone help me out?

tia

---

### Post by Bakon Jarser on 2008-11-25
Find the file named sipie.py (I'm too lazy to look for it right now) and edit it.

fourth line down
for gtk player:
player = Sipie.gtkPlayer

for wx player
player = Sipie.wxPlayer

for cli player
player = Sipie.cliPlayer

---

