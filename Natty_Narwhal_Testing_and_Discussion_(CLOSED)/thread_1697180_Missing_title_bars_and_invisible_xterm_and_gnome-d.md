---
title: "Missing title bars and invisible xterm and gnome-do windows"
date: 2011-02-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rebootme on 2011-02-28
Running the new nvidia driver with unity 3D.

Anyone else with this problem?

See attached screenshot to see the missing title bars.  Of course, a screenshot of the invisible windows was a little difficult!

---

### Post by cariboo on 2011-02-28
Have you tried:

```
unity --reset
```

in a terminal?

---

### Post by rebootme on 2011-02-28
Thanks for the tip.  It didn't work so I ran the following so I could actually see the invisible output.

> unity --reset &> unityreset

There were enough errors in there that some googling around led me to the following which worked.

> sudo nvidia-xconfig

---

