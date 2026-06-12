---
title: "Does firestarter protect me at startup?"
date: 2006-01-24
forum: Networking &amp; Wireless
---

### Post by Aybara on 2006-01-24
I have installed firestarter. I tried making it start at boot, but I need to be root to do it. I googled to a forum that showed me how I use visudo to allow everyone to start firestarter.

Another post said that firestarter is already running, even if I don't see the GUI. Is this correct, and is there any way to check it?

If so, I guess that means that I only need to open firestarter when I want to add new rules..

---

### Post by 23meg on 2006-01-24
> Another post said that firestarter is already running, even if I don't see the GUI. Is this correct, and is there any way to check it?It's correct. You can check with ```
ps aux |grep firestarter
```
> If so, I guess that means that I only need to open firestarter when I want to add new rules..Right, that's the best practice.

---

