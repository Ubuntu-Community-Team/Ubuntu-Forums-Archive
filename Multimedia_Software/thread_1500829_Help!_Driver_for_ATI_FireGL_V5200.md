---
title: "Help! Driver for ATI FireGL V5200"
date: 2010-06-03
forum: Multimedia Software
---

### Post by ewigtreter on 2010-06-03
Hello there,

I just installed 10.4 Lucid. Jockey won't detect a driver for my graphics card: ATI FireGL V5200. When I load it, it lists no drivers. I also have 8.4 Hardy installed, and this detected my card fine.

What should I do? Please help. 

Thanks, Richard

---

### Post by Yellow Pasque on 2010-06-04
Newr versions of Catalyst don't support your card, so you should just use the open-source drivers that are pre-installed.

---

### Post by 2hansen on 2010-08-06
I've just done a fresh install 64bit of 10.04 on a HP NW8440 - and it uses the "open-source drivers that are pre-installed". However, the screen is constantly flickering lightly (horizontal bands slowly moving upwards) - and if I try to change the screen resolution the screen becomes garbled and almost unusable - cannot revert without reboot.

Any suggestions?

---

### Post by voctemic on 2010-09-29
I'm having the same problem. I've also attempted to follow guides for installing the old catalyst drivers, but it seems the x.org has changed too much for me to get it right. Does anyone have a fix for this?

---

### Post by Mark Phelps on 2010-09-30
> **voctemic said:**
> I'm having the same problem. I've also attempted to follow guides for installing the old catalyst drivers, but it seems the x.org has changed too much for me to get it right. Does anyone have a fix for this?


Sorry, there is no real "fix" for this that will allow you to use the fglrx drivers anymore.  AMD dropped fglrx support for your card long ago.  The only drivers available now are the open-source drivers.

You can still FIND the older drivers, but they will not work with recent Ubuntu versions.

---

