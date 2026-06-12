---
title: "alsa mixer dosent save"
date: 2009-05-14
forum: Multimedia Software
---

### Post by lozanoa11 on 2009-05-14
im running linux mint 6(basicly intrepid) and i go to my alsamixer and turn it all the way up and press escape. then i go back to it and its back down to zero. what am i doing wrong.

---

### Post by lozanoa11 on 2009-05-14
bump

---

### Post by lozanoa11 on 2009-05-14
any one have any idea?

---

### Post by lozanoa11 on 2009-05-16
bump for the weekend crew im still haveing problems

---

### Post by kerry_s on 2009-05-16
set your settings then run> **sudo alsactl store**

---

### Post by lozanoa11 on 2009-05-16
that does not work. my capture settings will hold but the master will go right back down to 0 every time

---

### Post by lozanoa11 on 2009-05-16
some one has to have a solution for this

---

### Post by kerry_s on 2009-05-16
hmm, have you run **alsaconf**?

anyways the manual way of loading it is to put> **alsactl restore**
in /etc/rc.local

---

