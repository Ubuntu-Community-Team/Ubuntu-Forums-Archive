---
title: "DVD ripper"
date: 2011-09-13
forum: Multimedia Software
---

### Post by mattpl1981 on 2011-09-13
what is the best software to rip DVD's??

---

### Post by howefield on 2011-09-13
Depends what you want to rip to, I'd suggest Handbrake if you want a gui or vobcopy on the command line.

---

### Post by mattpl1981 on 2011-09-13
i just want to be able to copy and burn dvd's

---

### Post by mattpl1981 on 2011-09-13
im not finding handbrake in the software center.

---

### Post by howefield on 2011-09-13
You would need to add the repository to get Handbrake.

Easiest way is to copy/paste the following commands in to a terminal, one at a time and follow the prompts.

```
sudo add-apt-repository ppa:stebbins/handbrake-releases
```

```
sudo apt-get update
```

```
sudo apt-get install handbrake-gtk
```

---

### Post by dniMretsaM on 2011-09-13
Doesn't Handbrake also have a CLI version?

---

