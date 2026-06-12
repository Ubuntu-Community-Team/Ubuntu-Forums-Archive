---
title: "K3b is Unresponsive"
date: 2021-12-16
forum: Multimedia Software
---

### Post by geeky-1 on 2021-12-16
My K3b has been very slow to open and very unresponsive lately. It is the most current version and I think I even tried uninstalling and reinstalling.

---

### Post by csae2608 on 2022-01-04
when th app is "hanging" you can kill the window by using ALT + F2 and then type into window "xkill" and click into the hanging windows, atleast that was the way with Xorg Windows Manager, maybe with newer Wayland this no longer applies (please correct where wrong)

---

### Post by schragge on 2022-01-04
According to [this question]("https://askubuntu.com/questions/1111346") @Ask Ubuntu, xkill doesn't work in Wayland. But my experience with it in Wayland is inconsistent: it does work as expected with some windows, half-works with others, and doesn't work at all with yet others. Half-works means I don't get any visual feedback, i.e. mouse cursor doesn't change to **X**, but the window gets killed.

I guess it doesn't work with applications that run natively under Wayland rather than under XWayland.

At least in Weston, [you can use **Super** + **K** to kill the active window]("https://www.mankier.com/7/weston-bindings#Description").

---

