---
title: "Firefox and its addons"
date: 2010-07-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by awam66 on 2010-07-02
Since installing Maverick on my external usb drive for testing Firefox does not show the add ons such as adblock and Xmarks. In fact none of the add ons work even though they show in the tools>add-ons menu which always states that firefox needs a restart which of course does nothing.
Any one else seen this.
Firefox 3.6.6 AMD Athlon 64 (running 32 bit OS) Dell Dimension C521 1GB memory.

---

### Post by dino99 on 2010-07-02
hm works here

try: metacity -replace &

---

### Post by awam66 on 2010-07-02
> **dino99 said:**
> hm works here

try: metacity -replace &

Tried that (needs two --) but still no luck.

---

### Post by awam66 on 2010-07-05
Has anyone any ideas about this problem. None of the add-ons work!

---

### Post by dino99 on 2010-07-05
you can rename .gconf and .gnome2 then reboot in case they are corrupted, and/or remove then reinstall the broken addons

---

### Post by awam66 on 2010-07-05
> **dino99 said:**
> you can rename .gconf and .gnome2 then reboot in case they are corrupted, and/or remove then reinstall the broken addons

OK tried that and it made no difference. I have also tried uninstalling and re installing the add-ons and none of them work. They appear under the tools menu and in the add-ons window it always says "Restart Frefox to complete your changes", but restarting makes no difference. I am at a complete loss.

---

### Post by FuturePilot on 2010-07-05
> **dino99 said:**
> hm works here

try: metacity -replace &
The window manager has nothing to do with Firefox addons.

> **dino99 said:**
> you can rename .gconf and .gnome2 then reboot in case they are corrupted, and/or remove then reinstall the broken addons

Firefox does not store its settings in either of those directories. If you want to reset Firefox to the default settings rename ~/.mozilla which is what I would suggest for this problem.

---

### Post by cariboo on 2010-07-05
A better thing to try is:

```
firefox -Profilemanager
```

---

### Post by awam66 on 2010-07-05
> **cariboo907 said:**
> A better thing to try is:

```
firefox -Profilemanager
```

Thanks, I tried that, deleted the profile and now all is well.:D

---

