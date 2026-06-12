---
title: "Issue With Restricted Driver"
date: 2009-05-09
forum: Multimedia Software
---

### Post by Generic Bond on 2009-05-09
I just upgraded my computer to 9.04. I had installed it normally and activated the recommended hardware driver. I restarted my computer and my screen was black. Anybody have a clue what the problem is?

I'm using Ubuntu 9.04 Jaunty Jackalope. The restricted driver I was recommended to activate was NVIDIA accelerated graphics driver (version 180).

---

### Post by Arup on 2009-05-09
> **Generic Bond said:**
> I just upgraded my computer to 9.04. I had installed it normally and activated the recommended hardware driver. I restarted my computer and my screen was black. Anybody have a clue what the problem is?

I'm using Ubuntu 9.04 Jaunty Jackalope. The restricted driver I was recommended to activate was NVIDIA accelerated graphics driver (version 180).

Remove the restricted driver. sudo apt-get install envyng-core

log out of GUI by ctrl+alt+F1 and then do a /etc/init.d/gdm stop

do a sudo envyng -t and install drivers from there.

---

### Post by Generic Bond on 2009-05-09
It's still doing the same thing.

---

### Post by Arup on 2009-05-09
Download latest driver from nvidia and then install after logging out and stopping gdm.

---

