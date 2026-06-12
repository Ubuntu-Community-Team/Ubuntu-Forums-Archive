---
title: "K3B:  How to rip to mp3 versus ogg?"
date: 2010-12-19
forum: Multimedia Software
---

### Post by tinker123 on 2010-12-19
I'm on Ubuntu 10.10

I was using K3B the other day and could not find an option to rip a CD to mp3 files instead of ogg.  How can I do this?

Thanks in advance

---

### Post by I'mGeorge on 2010-12-19
make sure you have installed ```
libk3b6-extracodecs
``` either. Search for it with synaptic, and install it if not.

---

### Post by tinker123 on 2010-12-20
> **I'mGeorge said:**
> make sure you have installed ```
libk3b6-extracodecs
``` either. Search for it with synaptic, and install it if not.

Already have it installed, thanks anyway.

---

### Post by I'mGeorge on 2010-12-20
try this
```
sudo apt-get install lame
``` I believe you would need to install lame.

---

### Post by tinker123 on 2010-12-21
That did the trick, thanks!

---

