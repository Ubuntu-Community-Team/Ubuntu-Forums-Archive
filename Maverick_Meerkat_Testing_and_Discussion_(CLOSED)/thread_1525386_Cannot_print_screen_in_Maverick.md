---
title: "Cannot print screen in Maverick"
date: 2010-07-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2010-07-06
I have opened a bug on gnome-games and I tried to provide a screen print to give a better description of my problem. In Lucid, I type "Alt + Print Scrn" and it works. But in Maverick, nothing happens.

Now, support has asked me for a print screen showing the problem. I cannot figure out how to do one in Maverick. Please help.

Thanks,
Tim

PS - My bug is 602007.

---

### Post by Vanishing on 2010-07-06
Samething here..
right now i use scrot.

---

### Post by mc4man on 2010-07-06
Will be fixed at some point(kernel update), use the 'take screenshot' util, or something else in meantime

[bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596257")

---

### Post by ratcheer on 2010-07-06
> **Vanishing said:**
> Samething here..
right now i use scrot.

Thanks. I have installed scrot, how do I use it?

Tim

---

### Post by ratcheer on 2010-07-06
Never mind. Now, I can run scrot and get a screen shot, but when I go to the terminal window to execute scrot, it takes focus away from the game screen, so the game screen goes to pause mode before the screen shot is made.

Tim

---

### Post by ratcheer on 2010-07-06
> **mc4man said:**
> Will be fixed at some point(kernel update), use the 'take screenshot' util, or something else in meantime

[bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/596257")

Take Screenshot also fails. It matches an existing bug, so I added an "also affects me" to the Take Screenshot bug. It is crashing with a signal 5 in _Xerror() error.

Thanks, though.

Tim

---

### Post by ratcheer on 2010-07-06
Ah, I figured out how to delay scrot, then press Resume on gnomines to get a good screenshot of my problem.

Thanks, everyone.

Tim

---

### Post by kyleabaker on 2010-07-07
My print screen key hasn't been working, but I usually just pop open a terminal or Alt-F2 and run:
```
gnome-screenshot
```

or with a delay of 5 seconds:
```
gnome-screenshot -d 5
```

I didn't realize how much I use print screen until this bug, haha.

---

