---
title: "Remove Nautilus menu bar on Desktop"
date: 2011-02-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by taotree on 2011-02-10
I just upgraded to natty alpha 1 and now there is a menu bar on top that I cannot remove. It has File/Edit/View/Places/Help. The Help->About suggests it is Nautilus. It's not a panel, if I go into panel config it only shows my bottom panel and not this top one.

Nothing happens if I right click it.

---

### Post by corncob on 2011-02-10
Are you running emerald by any chance?  Just a thought.

---

### Post by wojox on 2011-02-10
Click the desktop, then click the panel. I don't think it can be removed. It's part of Unity.

---

### Post by taotree on 2011-02-10
Not sure what emerald is. Looks like it's part of Unity as you say. Very frustrating if it can't be removed since it's a total waste of screen space. I tried killing nautilus but it just gets respawned.

---

### Post by cariboo on 2011-02-10
It's an integral part of the Unity tool bar. When you open other applications, it gets out of the way.

Moved to Natty Testing & Discussion.

---

### Post by ScislaC on 2011-02-11
The nautilus bar is there on the Classic Desktop, so whether or not it's integral to Unity, it shouldn't show on Classic.

---

### Post by Anduu on 2011-02-11
Yes it definitely is showing on my classic desktop...needs to go.

I am also a bit miffed that the global menu applet is loaded by default in classic as well.At least it can be removed.

---

### Post by forcecore on 2011-02-11
I think it should be removeable in final, who needs menubar every time - even FireFox 4 has simple option to eliminate menubar. Menubar is history... year is 2011.

---

### Post by JOHNNYG713 on 2011-02-11
More than likely a bug in alpha 2 and should be resolved with an update soon, Remember Natty is still under development and is not stable as yet ! so you might (Will) have some bugs pop up ! At this point Natty is just for testing purposes only !

---

### Post by terry_gardener on 2011-02-11
i also get the nautilus menu items when i have nothing open in the panel. 

i think it is because by default the desktop is drawn by nautilus.

---

### Post by durand on 2011-02-11
You need to remove unity-window-decorator and appmenu-gtk. Thats what was causing it for me. This will however not let you use unity.

---

### Post by mc4man on 2011-02-16
Don't use gnome-panel but just noticed an update to gtk that should allow you to remove the top panel and have no panel at all.
(atm is just reverting to a previous 

bug on
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/717358](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/717358)

(in other words you don't need to remove anything if wanting to keep option to login to Unity

---

