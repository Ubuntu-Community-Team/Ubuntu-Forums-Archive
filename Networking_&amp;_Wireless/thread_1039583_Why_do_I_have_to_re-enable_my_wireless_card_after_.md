---
title: "Why do I have to re-enable my wireless card after reboot?"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by BreadLust on 2009-01-14
Hello all,

Thanks again for helping me get my wireless card working. Although I have gotten it to work, I need to go into the terminal and enter:

sudo modprobe ndiswrapper

... after each reboot before the wireless card can be accessed. Why is this? I've even entered the sudo ndiswrapper -m command, and I still lose it after reboot.

Thanks in advance for your advice!

---

### Post by Ayuthia on 2009-01-14
Have you added ndiswrapper to /etc/modules:
```
echo ndiswrapper|sudo tee -a /etc/modules
```

---

### Post by BreadLust on 2009-01-15
That looks like it did the trick! Thanks a bunch!:D

---

