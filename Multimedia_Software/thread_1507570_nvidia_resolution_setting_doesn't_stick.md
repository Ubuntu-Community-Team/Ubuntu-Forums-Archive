---
title: "nvidia resolution setting doesn't stick"
date: 2010-06-11
forum: Multimedia Software
---

### Post by starbuckk on 2010-06-11
Ubuntu 10.04, nVidia GeForce 9400, driver ver 195.36.15.

When I log in, the system always comes up in 800x600 mode. I went into the NVIDIA X Server Settings page and changed it to my preferred setting of 1152x864. I hit Apply, then Save to X Configuration File (with correct root password).

All is well until restarting. Then it reverts back. The update doesn't stick. How can I make this the permenant setting?

---

### Post by xc3RnbFO8P on 2010-06-11
Did you try System> Preferences> Monitors, choose No and change the resolution?

---

### Post by uhhman on 2010-12-26
Dears,
I have a similar problem as my settings are lost every boot!
Any suggestion on how to fix it?
I have nvidia geforce 4 400go and downloaded fresh nvidia drivers..and what drives me crazy is that log in page of ubuntu is with correct resolution, while desktop is wrong!

Any help?

Thx!

---

### Post by bakegoodz on 2010-12-26
Ringi suggestion worked! Apparently it only reads the changes made with the built-in Gnome Monitor app on start-up.

---

