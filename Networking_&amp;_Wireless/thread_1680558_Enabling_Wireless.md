---
title: "Enabling Wireless"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by mixt on 2011-02-02
Hello I am running 10.10, and i have gotten the necessary firmware, and drivers for my wireless card, and it still wont work, when i right click the notification icon. The 'Enable Wireless' option is disabled.

---

### Post by dineshs on 2011-02-03
Please see post #4 [here ]("http://ubuntuforums.org/showthread.php?t=1452464&highlight=hard+blocked") ie run ```
sudo rfkill unblock all
```and see if it works.If not please post the result of ```
rfkill list
``` and ```
sudo lshw -C network
```

---

