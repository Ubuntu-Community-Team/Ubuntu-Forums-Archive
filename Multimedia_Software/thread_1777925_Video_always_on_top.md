---
title: "Video always on top"
date: 2011-06-08
forum: Multimedia Software
---

### Post by --Ja-- on 2011-06-08
Hi all!

I'm having problems with video applications, such as VLC, Totem and even Google Earth.

What happens is that video being played is always on top, even if some other windows is positioned over it.

This is happening on HP ProBook 4710s, with gnome, metacity and proprietary ATI driver.

Screenshot of a problem:
[[IMG]http://img121.imageshack.us/img121/2377/screenshotyo.th.png[/IMG]](http://img121.imageshack.us/img121/2377/screenshotyo.png)

System is Ubuntu 11.04, fully updated.

Thank you!

---

### Post by --Ja-- on 2011-06-09
Anyone?

---

### Post by Green_Star on 2011-06-13
I too having this problem with my 1104 Ubuntu, this is very annoying. Any fix will be appreciated.

---

### Post by Green_Star on 2011-06-13
I found the solution.

Unchecking /apps/metacity/general/capture_before_unmap in gconf-editor, logout and log back in solved this issue in my computer.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/758609](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/758609)

---

