---
title: "[SOLVED] NVidia Installation: Envy or Synaptic?"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Zeotronic on 2008-04-28
Back in 7.04 I installed NVidia through Synaptic, unaware of Envy. In 7.10 installing NVidia through Synaptic didn't have the correct results, and I subsequently discovered Envy. Now (8.04), I know I could install it through Synaptic... (previous install) but which would have better results installing it with?

---

### Post by jocko on 2008-04-28
Restricted-manager is probably the best (easiest and most reliable) way (it automatically configures xorg to use the driver).
Envy still gets the driver directly from nvidia/ati instead of from the repos, right?
That's good if you really need the latest driver, but sooner or later you will get a kernel update which breaks the driver.
Better to stay with the repo version, unless you are comfortable with the command line and know what to do when the driver needs to be reinstalled.

---

### Post by Zeotronic on 2008-04-28
While I'm sure I could handle it, I'll just stick to the restricted driver manager then.

---

