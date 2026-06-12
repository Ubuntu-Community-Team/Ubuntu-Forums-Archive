---
title: "K3b allocates 8 GB instead of 4.4 while burning DVD"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by mibadt on 2007-05-07
Hi,
I'm on a fully updated Kubuntu Feisty. While trying to burn a 4.4 GB (4.7 GB media) using K3b (ver 3.5.6), I've noticed that K3b displays the existing volume (at the bottom of screen) as "xxx out of 8 GByte", rather than 4.4 GB as usual.

Hoe come? How can I fix it?

TIA


Michael Badt

---

### Post by Endolith on 2008-04-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/155375](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/155375) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Related bug report?

---

### Post by tubasoldier on 2008-04-13
One reason may be that if you go over 4.4 GB it will automatically assume you have a dual-layer disk. Or, if it does it by default it may be related to the afformentioned bug.

---

