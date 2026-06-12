---
title: "No menu bar minimize buttons"
date: 2010-06-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by clyderino on 2010-06-05
I have Meerkat alpha 1 Netbook version: there are no "maximize/minimize/close" buttons on the menu bars. How do I restore them?

---

### Post by arjunak01 on 2010-06-05
press ALT F2 and type ```
gconf-editor
```goto apps > metacity > general
double click on button layout it must be something like menu:minimize,maximize,close

---

### Post by arjunak01 on 2010-06-05
if the entire title bar is missing then open Appearance window  goto visual effects tab and choose none

---

### Post by xeddog on 2010-06-05
I'm not familiar with the netbook edition, but could the buttons be in the upper LEFT corner?

xeddog

---

### Post by clyderino on 2010-06-06
Thanks for the replys. Meerkat 10.10 for Netbook will have a Macintosh like "global menu" setup by default wherein the menu for the application in use is shown in the title bar. Even though you could download an applet to make it work in previous versions,it is not quite working yet in the alpha released so far: some of the apps have the menu bar in the application window, as in the past. Many of these, on my setup, do not close/minimize/maximize buttons in the menu bar. 
So...a work in progress!

---

### Post by slimtonio on 2010-06-10
Hi,

I am using a Dell 13z o nubuntu 10.04 and I don't know why, but the close minimize and maximize buttons disappeared too.

They are there in gconf-editor, -> metacity etc, but they don't aapear on my windows!

Two days ago i had the same problem because i installed compiz fusion icon. But i removed it and the problem was solved.

But I don't know why, they disappeared again this afternoon....

any idea please?

---

### Post by cariboo on 2010-06-10
Appmenu should be in the Maverick repositories sometime today, things are in a state of flux at the moment, after all we are only at alpha 1. Yesterday, I had a combination of the UNE and Unity, today after updates I on;ly get the Unity panel.

---

### Post by slimtonio on 2010-06-10
Thank you for your answer!

---

