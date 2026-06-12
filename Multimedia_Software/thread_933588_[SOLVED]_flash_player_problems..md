---
title: "[SOLVED] flash player problems."
date: 2008-09-29
forum: Multimedia Software
---

### Post by tacticalbread on 2008-09-29
when I first used Firefox, I used the "missing plugins" thing to install Gnash, and I restarted Firefox, but it didn't work. All I get is a blank box.

I tried various commands to install the other flash players, and it says they are installed, but I'm still only getting Gnash in Firefox.

probably an easy fix, but I don't know what to do. -_-

---

### Post by aysiu on 2008-09-29
Gnash seems to overpower the other plugins for some reason.

**Step 1**
Close Firefox

**Step 2**
Paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install --reinstall flashplugin-nonfree
```

**Step 3**
Start Firefox again

---

### Post by gandaran on 2008-09-29
easy, open synaptic package manager, scroll down to gnash, mark for complete removal (check for swfdec too) then find **flashplugin-nonfree** (adobe flash) mark for install and click the apply button

---

### Post by tacticalbread on 2008-09-29
awesome, removing Gnash worked.

thanks guys. (:

edit: sound from flash isn't working for some reason?

---

### Post by gandaran on 2008-09-29
> edit: sound from flash isn't working for some reason?
you can either install **libflashsupport** for flash 9 or remove flash 9 and install flash 10

---

### Post by tacticalbread on 2008-09-29
awesome, installing libflashsupport fixed it.

thanks again. (:

---

### Post by gandaran on 2008-09-29
just one thing to remember, if you get firefox crashes with libflashsupport remove both flash 9 and libflashsupport and go for the flash 10

---

