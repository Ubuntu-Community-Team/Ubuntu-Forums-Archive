---
title: "enable v-sync"
date: 2010-01-02
forum: Multimedia Software
---

### Post by swappo1 on 2010-01-02
Hello, 

How do I enable v-sync?  I have a nvidia card, however, I don't have a Display icon under the preferences menu to access display features.  Thanks

---

### Post by Artemis3 on 2010-01-03
It's not under Preferences, but under Administration (if you used distro/ppa packages). The package is called nvidia-settings.

You could also set the environment variable (append to /etc/environment): __GL_SYNC_TO_VBLANK=1

---

