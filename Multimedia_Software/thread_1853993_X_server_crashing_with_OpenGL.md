---
title: "X server crashing with OpenGL"
date: 2011-10-03
forum: Multimedia Software
---

### Post by GordonGR2011 on 2011-10-03
Hallo everyone.

I have the following issue: Sometimes, when using OpenGL applications (SecondLife viewers, actually), my whole X freezes. If I kill it with Control+Alt+Backspace it reopens at the next virtual console (Control+Alt+F8), but only as audio. That is, I can hear the sound GDM makes, I can hear the sound Gnome makes (I give my user name and password blindly), but I have no video. Other times my whole system crashes (consoles as well), and other times it all works fluently.

My graphics adaptor is an on board Intel GMA X4500 (which I know isn't made for gaming).

nikos@Russell:~$  lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e32] (rev 03)


Any ideas how to fix this?

---

