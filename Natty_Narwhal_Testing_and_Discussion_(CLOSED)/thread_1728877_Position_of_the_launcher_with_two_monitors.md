---
title: "Position of the launcher with two monitors"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jorijn on 2011-04-14
Hi,

Just tried the beta2, great job. It really has come far. I have a dualscreen set up with my laptop. Attached is a monitor with DVI.

It doesn't matter in what order I configure the monitors, the Unity Launcher stays on the laptop. This is rather anoying since my laptop is placed right.

I'm not sure what to do with this question, I don't know if its a bug or if its just my lack of searching through all the available settings.

Hope any of you can help out.

Regards,
Jorijn.

---

### Post by jorijn on 2011-04-15
bump

---

### Post by Tich666 on 2011-04-15
assuming you can configure your monitor with xrandr, this will fix it!

```
xrandr --output <your primary monitor here> --primary
```

---

