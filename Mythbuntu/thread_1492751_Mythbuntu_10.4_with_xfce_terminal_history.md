---
title: "Mythbuntu 10.4 with xfce: terminal history"
date: 2010-05-25
forum: Mythbuntu
---

### Post by Michael3007 on 2010-05-25
Hello,

I am running Mythbuntu 10.4 with xfce and the terminal doesn't keep the history of commands. Everytime I close the terminal the history is gone. I used Mythbuntu 9.10 before and that terminal remembers all my entered commands even when I shut down the computer.

I am still a linux beginner and so I have to look up the syntax of commands quite often. So the terminal history has been very helpful to me.

Is it possible to configure the behavior of the terminal history?

Thanks for your help!

Regards,

Michael

---

### Post by arrange on 2010-05-25
I'm not sure about *xfce* and *Mythbuntu*, but please post your *.bashrc* file for review, f.e.```
grep '^[^#]' ~/.bashrc
```

---

### Post by nickrout on 2010-05-25
check ownership of ~/.bash_history

I think I ran my first command as root (ie sudo) and root owned the history file.

---

### Post by Michael3007 on 2010-05-26
Thanks for your help!! The advice of nickrout solved the problem.

---

