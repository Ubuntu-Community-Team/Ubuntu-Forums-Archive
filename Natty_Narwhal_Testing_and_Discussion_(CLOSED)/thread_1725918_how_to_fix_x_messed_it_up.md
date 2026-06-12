---
title: "how to fix x messed it up"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-04-10
was messing with nvidia drivers and ran this command from terminal
sudo nvidia-xconfig and then restarted x. problem is now is the only way i can load natty is boot into recovery, drop down to the failsafe graphics modes and then hit restart x. if i do this everything works great. any idea how to fix./tks

---

### Post by rburkartjo on 2011-04-10
note spm shows i have no broken packages

---

### Post by dino99 on 2011-04-10
let the kernel doing its job without this weird xconfig, dkms need to be installed

sudo rm /etc/X11/xorg.conf

---

### Post by rburkartjo on 2011-04-10
most appreciated dino will do/tks

---

### Post by rburkartjo on 2011-04-10
that did the trick

---

### Post by dino99 on 2011-04-10
> **rburkartjo said:**
> that did the trick

good to know :)

---

