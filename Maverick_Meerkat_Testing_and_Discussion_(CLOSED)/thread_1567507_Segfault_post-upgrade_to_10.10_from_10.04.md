---
title: "Segfault post-upgrade to 10.10 from 10.04"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by thndrkat on 2010-09-03
Help!

I just ran upgrade-manager -d to update to 10.10.  Something happened, but running synaptic package manager corrected the issue, then I finished the upgrade.  After reboot, various programs do not launch:

update manager
software center
(others)

Here's what the error looks like:

Sep  3 19:40:19 loki kernel: [  248.569437] update-manager[1680]: segfault at aaaaaaaa ip 012492d9 sp bfb45cc0 error 4 in libgtk-x11-2.0.so.0.2107.0[fae000+40a000]

Sorry if that's too much information.  Any help is greatly appreciated.

---

### Post by thndrkat on 2010-09-04
Update:

Okay, so I was able to get this fixed.  Not 100% sure...sorry.  I was able to get Synaptic Package Manager to run, and I clicked on the Marked for Upgrades button, which selected something like, 200+ packages.  Ran that.  An error popped up, but at that point, Upgrade Manager could run.  It reinstalled the erroneously-installed package, then after a long reboot, things seem to be working smoothly.

Man, what did I get myself into???

---

