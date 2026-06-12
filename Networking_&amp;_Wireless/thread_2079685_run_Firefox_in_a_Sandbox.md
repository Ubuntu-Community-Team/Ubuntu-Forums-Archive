---
title: "run Firefox in a Sandbox"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by hobertsl on 2012-11-02
Hello! With the following command you can run Firefox in a Sandbox

sandbox -X -s -W metacity firefox

I was wondering if there's any way to put this command in the Firefox-Icon so that my mom can do this easily too. Wish you all the best!

---

### Post by DoubleClicker on 2012-11-27
[LIST]
[*] Gnome-panel and desktop: simply right-click the launcher, select "Properties" and type **sandbox -X -s -W metacity firefox** in the "Command" field
[*] Menu: right-click the menu and select "Edit Menus". In the new  window, find the launcher you want to edit and click the "Properties"  button on the right. Again,  type **sandbox -X -s -W metacity firefox **in the "Command" field
[/LIST]

---

### Post by vasa1 on 2012-11-27
Very interesting! Can someone please post some links related to this topic? The last time I looked, "sandboxing" required quite a complicated procedure.

---

