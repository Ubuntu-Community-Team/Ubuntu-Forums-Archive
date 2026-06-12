---
title: "[Remote control] xev don't recognize all keys"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by davidegn82 on 2008-02-17
In this days, I'm trouble with Hauppauge HVR-3000 Remote control.

The new Remote control is fully supported in my linux kernel (My release of ubuntu is Gusty Gibbon) and it works as a keyboard.

I use "xev" to test the keys of remote control but only few keys are recognized by the system. If i use the input layer "input-events" on my remote control event (in my case, "/dev/input/event2"), all keys are recognized and the keymap is correct.

In mythtv, it is possible to use only the keys recognized with xev and I don't understand what is the difference from "xev" and "input-events".

Why are only few keys recognized as events by the kernel? What can I do to solve this problem?

---

