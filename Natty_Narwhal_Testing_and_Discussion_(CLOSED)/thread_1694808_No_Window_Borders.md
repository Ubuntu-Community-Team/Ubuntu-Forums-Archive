---
title: "No Window Borders"
date: 2011-02-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jim11 on 2011-02-24
I updated today, and window borders disappeared from all my programs. If anyone knows how to fix it (if I need to downgrade packages which packages do I need [I update everyday]). I assume it has something to due with the xorg packages, but don't know for sure.

I am running updated Natty Alpha, on an Acer 7740. With this integrated intel video card:
 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)

---

### Post by mc4man on 2011-02-24
Check and see if your compiz is at 1:0.9.4-0ubuntu1 AND your libdecoration0 is the same version - libdecoration0 (1:0.9.4-0ubuntu1)

---

### Post by tjeremiah on 2011-02-25
Same happened to me. I rebooted and ran recovery mode, fixed broken packages, rebooted again and my borders are back.

---

### Post by PaulW2U on 2011-02-25
> **mc4man said:**
> Check and see if your compiz is at 1:0.9.4-0ubuntu1 AND your libdecoration0 is the same version - libdecoration0 (1:0.9.4-0ubuntu1)
I have this problem from time to time and those version numbers are what I have. The temporary fix seems to be **compiz --replace**. This brings back the window borders and the max, min and close buttons.

---

### Post by pressureman on 2011-02-25
My session runs fine, but as soon as I send an email in Thunderbird, I lose window decorations:

```

Feb 25 15:56:46 localhost kernel: [13921.488962] unity-window-de[5445]: segfault at 310 ip 0000000000415bab sp 00007fffc89530f0 error 4 in unity-window-decorator[400000+1b000]

```

I'm not even sure why unity-window-decorator is crashing, since I'm using Gnome classic desktop (as I thought it was the less turbulent/buggy at this stage of development).

---

