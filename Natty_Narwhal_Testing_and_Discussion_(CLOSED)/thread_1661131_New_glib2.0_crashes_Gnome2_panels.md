---
title: "New glib2.0 crashes Gnome2 panels"
date: 2011-01-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-01-06
After the recent upgrade of glib2.0 2.27.5 to 2.27.90 all Gnome2 panels crash each time I click on any launcher applet on any panel.
As workaround I downgraded the glib2.0 packages.

I made a bug report (698131) about this.
[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/698131](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/698131)

---

### Post by dino99 on 2011-01-06
dont get this problem on i386 with nvidia 8500gt & 260.19.21-0ubuntu3

---

### Post by Gladk on 2011-01-06
Same crash for me, I have Dell Mini 10v.

---

### Post by gnomeuser on 2011-01-06
Should be fixed now:
[https://lists.ubuntu.com/archives/natty-changes/2011-January/004856.html](https://lists.ubuntu.com/archives/natty-changes/2011-January/004856.html)

---

### Post by Harry33 on 2011-01-07
> **gnomeuser said:**
> Should be fixed now:
[https://lists.ubuntu.com/archives/natty-changes/2011-January/004856.html](https://lists.ubuntu.com/archives/natty-changes/2011-January/004856.html)

Confirming, the update to 2.27.90-0ubuntu2 fixed this.

---

