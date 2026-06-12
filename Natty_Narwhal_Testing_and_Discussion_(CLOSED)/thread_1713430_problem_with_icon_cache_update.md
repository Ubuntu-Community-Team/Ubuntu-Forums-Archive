---
title: "problem with icon cache update"
date: 2011-03-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by zika on 2011-03-24
```
gtk-update-icon-cache: The generated cache was invalid.
WARNING: icon cache generation failed for /usr/share/icons/ubuntu-mono-dark
gtk-update-icon-cache: The generated cache was invalid.
WARNING: icon cache generation failed for /usr/share/icons/ubuntu-mono-light
```

---

### Post by alex_mayorga on 2011-03-24
Do you see weird icons in the notification are like these?

[IMG]http://i.imm.io/4y6g.png[/IMG]

---

### Post by zika on 2011-03-25
> **alex_mayorga said:**
> Do you see weird icons in the notification are like these?

[IMG]http://i.imm.io/4y6g.png[/IMG]I'm in FluxBox, now, I'll check when I switch. Yesterday, while cache was corrupt, I did not see such artefacts...

Update: No, I do not have problem with visible icons...

---

### Post by Harry33 on 2011-03-25
> **alex_mayorga said:**
> Do you see weird icons in the notification are like these?

[IMG]http://i.imm.io/4y6g.png[/IMG]

This is due to the bug in the package libappindicator1_0.3.0-0ubuntu1.
See more info in this thread:
[http://ubuntuforums.org/showthread.php?t=1713317](http://ubuntuforums.org/showthread.php?t=1713317)

---

