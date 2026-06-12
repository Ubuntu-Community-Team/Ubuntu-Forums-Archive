---
title: "My app misteriously crashes under Maverick"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-08-21
Hi,
I'm playing/creating a file browser (in Gtkmm) and it crashes for no reason in Ubuntu 10.10 64 bit but works fine on Ubuntu 10.04 64 bit. I don't think anyone will bother checking what's the matter (I know the line in the source code where it crashes, but I can't figure out _why_), I'm just asking a few folks using Ubuntu 10.10 to confirm the crash for me to know the crash doesn't only happen on _my_ Ubuntu 10.10 setup.

Here's how to replicate the bug:
Launch the app (a simple browser window will appear), type in the location bar /usr/bin or /usr/lib, hit enter and then click somewhere near a file name - at this point the app should crash (the window should close).


PS: if you don't trust my (64 bit) binary you can check the attached source code (a NetBeans 6.9.1 C++ project) and compile and run it yourself.
Thanks a lot for your (crash) confirmation or lack there of in advance.

---

