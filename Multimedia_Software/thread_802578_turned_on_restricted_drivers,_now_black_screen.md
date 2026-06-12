---
title: "turned on restricted drivers, now black screen"
date: 2008-05-21
forum: Multimedia Software
---

### Post by Frijole on 2008-05-21
I turned on the Nvidia restricted drivers (I don't know why, I just had to try it) and now I get a black screen on startup, how can I reset it back to its original settings?

---

### Post by overdrank on 2008-05-21
> **Frijole said:**
> I turned on the Nvidia restricted drivers (I don't know why, I just had to try it) and now I get a black screen on startup, how can I reset it back to its original settings?

Hi and you can try the keys, ctrl, alt,F1 and this will bring you to the command prompt then reconfigure your xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then sudo reboot
If you can not reach the command line then you can try from recovery mode.

---

### Post by Frijole on 2008-05-21
ok, so I should just boot up and sign in etc. without seeing anything? or do I do this earlier in the process?

---

### Post by overdrank on 2008-05-21
> **Frijole said:**
> ok, so I should just boot up and sign in etc. without seeing anything? or do I do this earlier in the process?

Hi and when you reach the login screen just use the keys to reach the command line.

---

### Post by Frijole on 2008-05-21
thanks, I'll give that a try.

---

### Post by Frijole on 2008-05-21
that was it, thanks again.

---

### Post by overdrank on 2008-05-21
> **Frijole said:**
> that was it, thanks again.

Great good luck! :popcorn:

---

