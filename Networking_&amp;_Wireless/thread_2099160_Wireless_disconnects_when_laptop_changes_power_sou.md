---
title: "Wireless disconnects when laptop changes power source."
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by JokerJeromeX on 2012-12-28
[FONT="Lucida Console"]My laptop disconnects and reconnects to my wifi whenever I unplug it from the wall or plug it back in. I think this is from the ubuntu power manager but I cannot for the life of me find out how to disable it. Can someone tell me either how to make sure it stays connected when I unplug it or plug it back in, or just disable all power management, or whatever is causing it? [/FONT]

---

### Post by Pjotr123 on 2012-12-28
Disable power management only for the wireless card:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card)
(item 2.1, right column)

---

### Post by JokerJeromeX on 2012-12-28
And what if power management is already off, but it still disconnects?

---

### Post by Pjotr123 on 2012-12-28
> **JokerJeromeX said:**
> And what if power management is already off, but it still disconnects?

Well, is it off? For the *wireless card*, that is.

---

### Post by JokerJeromeX on 2012-12-28
It says that power management is off as far as I can tell.

---

### Post by Pjotr123 on 2012-12-29
What's the complete output of:
```
iwconfig
```

Use copy/paste to transfer it to your answer.

---

