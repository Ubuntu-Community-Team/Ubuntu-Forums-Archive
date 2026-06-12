---
title: "Global menus in Classic mode"
date: 2011-02-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by teachop on 2011-02-06
Since Unity isn't working for me, I have been logging into Classic mode.  I was surprised that classic mode uses global menu bars.  The result for me is that many programs that I use don't have menus at all, much of the time.  These include eclipse, nautilus, terminal.  My other staple, firefox, seems to be OK.

Is there a way in classic mode to get classic menus, at least for now?

---

### Post by teachop on 2011-02-06
Never mind, just figured out you can remove the global menu from the panel and things come back to normal.

---

### Post by chrisccoulson on 2011-02-06
Did you report the bugs you were experiencing with the menu?

---

### Post by teachop on 2011-02-06
> **chrisccoulson said:**
> Did you report the bugs you were experiencing with the menu?
No I didn't.  I scanned the launchpad bugs for appmenu, and didn't see anything either.

For eclipse, after a cold boot there is no menu anyplace.  I have found that what I need to do is add the appmenu back to the panel, then remove it, and the menu shows in the application itself.  Perhaps it means eclipse needs an update.

Sometimes there were no menus in terminal or nautilus, and these are part of the alpha, so that must be a bug.  I suppose I should get my thoughts pulled together on launchpad as a bug report.  Yes.

---

### Post by Funnnny on 2011-02-06
eclipse was never compatible with global menu in Unity :D

---

### Post by teachop on 2011-02-06
> **Funnnny said:**
> eclipse was never compatible with global menu in Unity :D
I don't mind that, as long as the menu is someplace!  No menu is rough.  Adding and removing indicator appmenu is a fix for now.

---

### Post by Funnnny on 2011-02-07
You can just export a env var, (UBUNTU_MENUPROXY or something like this, I cannot test this for you now :) )

---

### Post by stevovukovic on 2011-02-10
> **teachop said:**
> Never mind, just figured out you can remove the global menu from the panel and things come back to normal.

Do you have Nautilus global menu under Top GNOME panel?

---

### Post by teachop on 2011-02-10
> **stevovukovic said:**
> Do you have Nautilus global menu under Top GNOME panel?
I removed indicator applet appmenu.  So there are no menus in the panel.  However, I have found over time that the menus are still messed over, even with that removed.  Sometimes the menus in applications are missing (eclipse) sometimes they just quit responding.  There is a long ways to go.

---

### Post by stevovukovic on 2011-02-10
Move Top panel to the side, left or right. I have Nautilus global menu hidden UNDER top panel. Do you have it to?

---

### Post by teachop on 2011-02-10
> **stevovukovic said:**
> Move Top panel to the side, left or right. I have Nautilus global menu hidden UNDER top panel. Do you have it to?

No.

---

### Post by stevovukovic on 2011-02-12
[http://www1.ubuntuforums.org/showthread.php?p=10448152](http://www1.ubuntuforums.org/showthread.php?p=10448152)

---

### Post by teachop on 2011-02-12
> **stevovukovic said:**
> Move Top panel to the side, left or right. I have Nautilus global menu hidden UNDER top panel. Do you have it to?

Woops.  Did updates yesterday, now yes I do have it too...  Hope they snuff the Unity remnants like this in Classic mode in the next 2 months.

---

### Post by teachop on 2011-02-12
.

---

