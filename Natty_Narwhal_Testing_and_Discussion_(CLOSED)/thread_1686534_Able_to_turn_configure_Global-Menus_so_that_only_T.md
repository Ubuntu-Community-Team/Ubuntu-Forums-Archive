---
title: "Able to turn configure Global-Menus so that only Titlebar appears in Panel?"
date: 2011-02-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nrundy on 2011-02-12
Global Menus (i.e., File Edit View etc.) is a bad idea IMHO for a Desktop Panel. Too much mouse travel is required when windows are in the "restore size" (i.e., not minimized nor maximized). 

What would be awesome though would be if all windows had the traditional titlebar & menubar but when a window is maximized that the Titlebar of the maximized window merges into the Top-Panel. This would save loads of space but also prevent needless mouse travel for menu access when a window is in restore-size.

Any chance Unity Desktop will allow this configuration?

---

### Post by mc4man on 2011-02-12
Atm don't think so - had a wishlist bug on similar (unmaxed retain menus, maxed use global),  just noticed it was duped to this even though I don't think screen size matters at all, find it just as unwieldy on a 13" laptop as a 24" desktop

[https://bugs.launchpad.net/unity/+bug/682788](https://bugs.launchpad.net/unity/+bug/682788)

---

### Post by nilarimogard on 2011-02-12
If you're not using Unity (use classic Gnome Panels), you can use [Window Applets]("http://www.webupd8.org/2010/12/window-applets-0210-released.html") for exactly that. Further more, you can place the window buttons separately from the window title (like the window buttons on the top right, some applets next to it and the window title in the middle).

---

### Post by mc4man on 2011-02-12
On a unity note - While atm it is an either or scenario, there may be some apps where you'll usually never run maxed and or wish to retain the menu in that app.
_ATM_ it can be done easily thru either a binary diversion or in most cases a simple edit in the app's .desktop to the exec= line will suffice.
Simple example w/ audacious
(gksudo gedit /usr/share/applications/audacious2.desktop

Editing the Exec= to this will retain menus
```
Exec=env UBUNTU_MENUPROXY=0 audacious2 %U
```
Obviously such things are subject to change as natty progresses

---

### Post by nrundy on 2011-02-12
If Unity goes Global Menus (File Edit) on the panel it's gonna make me want to use GNOME-shell. But then I'm gonna wish GNOME-shell could merge the Titlebar into the Panel when I maximize a window.

I think Unity looks and sounds awesome otherwise though.

---

### Post by Mr. Picklesworth on 2011-02-12
You can uninstall the indicator-appmenu package. It isn't ideal (since that's a system wide change and this should be a per-user choice), but should do the trick for now :)

---

### Post by nrundy on 2011-02-12
I like the indicators though. I like to get feedback on what's happening.

---

