---
title: "Update Nvidia Driver Question"
date: 2013-03-30
forum: Multimedia Software
---

### Post by EchoTech on 2013-03-30
I just upgraded my video card (GEForce GTX 650 Ti) and monitor (Samsung 23"). I'm using Additional Drivers "nvidia-current-updates" and Nvidia-settings shows "Version 304.51", which is the same as my previous setup.  Should/could I update my video driver?

  I see in Additional Drivers  there is a Version 310 Experimental. Is that a stable driver or ...... ?

  PS. I'll be back in about 24 hours.

---

### Post by carl4926 on 2013-03-30
Best way to install nvidia driver is

```
sudo apt-get install nvidia-current
```

---

### Post by carl4926 on 2013-03-30
It's all horror stories doing anything else

---

### Post by Yellow Pasque on 2013-03-30
Generally, if it ain't broke, don't fix it. If breakage is okay with you (i.e. you feel confident in your ability to recover from a terminal), check out xorg-edgers ppa for nvidia 313.xx driver

---

### Post by LuisGMarine on 2013-03-30
I have a 680 GTX running that 310 experimental drivers and I'm not having any issues.  Some games on steam might crash, but that's very rare and its based on the game not steam.  As for desktop use I have 12.04, and honestly I have not encountered one single system crash due to anything video related.

---

### Post by EchoTech on 2013-03-31
What I've got, driver version 304.51, seems to be working fine so I'll stick with it.

PS:  Where did the mark "Solved" go? It isn't under thread tools.

---

### Post by bogan on 2013-03-31
> **EchoTech said:**
> What I've got, driver version 304.51, seems to be working fine so I'll stick with it.

PS:  Where did the mark "Solved" go? It isn't under thread tools.You have to use;Edit>Advanced & edit the Prefix to "Solved", then Save Changes.

Chao!, **bogan**.

---

### Post by EchoTech on 2013-04-01
Thanks.

---

