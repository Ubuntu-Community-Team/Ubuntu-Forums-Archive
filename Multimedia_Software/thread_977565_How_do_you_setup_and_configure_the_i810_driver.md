---
title: "How do you setup and configure the i810 driver"
date: 2008-11-10
forum: Multimedia Software
---

### Post by Philip Hammer on 2008-11-10
Can anyone help me with setting up the i810 driver. with the intel driver I can not use programs with 3d graphics so... I thought maybe the i810 driver will work, but when I tried to setup the i810 driver my computer would not boot and I had to reconfigure x.org (which setup the intel driver again). I am running 8.04.

---

### Post by psyke83 on 2008-11-10
> **Philip Hammer said:**
> Can anyone help me with setting up the i810 driver. with the intel driver I can not use programs with 3d graphics so... I thought maybe the i810 driver will work, but when I tried to setup the i810 driver my computer would not boot and I had to reconfigure x.org (which setup the intel driver again). I am running 8.04.

Don't use the "i810" driver, it's obsolete. It was only kept in the repositories due to modesetting bugs in the "intel" driver, which now appear to be resolved. Using the "intel" driver, post your /var/log/Xorg.0.log and output from the "glxinfo" command.

---

