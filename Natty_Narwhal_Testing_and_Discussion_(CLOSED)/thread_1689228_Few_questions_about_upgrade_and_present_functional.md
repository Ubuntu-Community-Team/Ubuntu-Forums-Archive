---
title: "Few questions about upgrade and present functionality of Unity"
date: 2011-02-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Enternald on 2011-02-16
In Unity (2D) search window doesn't work. I write something and nothing show up. Also I click Music, Game, Photos & Videos , office and other thumbnails , they dissapear, but nothing show ups (icons op apps). 
1)What I could do to debug this? Or solve it? Or it is not implemented yet?
2) What search engine it uses, my update to natty didn't installed tracker. If that could be the problem I could install tracker and try to see if it helps.

Other problems in Natty:
Nvideo video card drivers (popular problem). 
Original gnome-panel do not start in classic mode. (I would test this after solving Unity).

---

### Post by zika on 2011-02-16
> **Enternald said:**
> Original gnome-panel do not start in classic mode. (I would test this after solving Unity).??
I use it every day...

---

### Post by Harry33 on 2011-02-16
> **Enternald said:**
> 
....
Other problems in Natty:
Nvideo video card drivers (popular problem). 
Original gnome-panel do not start in classic mode. (I would test this after solving Unity).

NVidia graphics drivers are among the best drivers in Linux systems.
Of course high end graphics cards has also something to do with this.
The fact that the current drivers do not support development versions of xserver 1.10 is only temporary. Soon we will have fine drivers for new xserver too.
Then again, xserver 1.10 is not ready yet, next we will see rc2.

Gnome-panel problem seems a bit odd to me. It works very well now and it has been working well before too.
More info is needed to explain the panel issues you have.

---

### Post by mc4man on 2011-02-16
> Original gnome-panel do not start in classic mode.
Until putting a new mesa in place yesterday to re-enable unity w/ nouveau had been using gnome-panel on an install w/ a nvidia pci-e card.

What I did notice with a couple of the more  recent .iso's was the panels would not always load, (on one .iso they never would, no matter what.

If you're not already then you may want to try installing from the Alpha2 iso and then updating
You could also try at login > Classic - no effects,

---

### Post by ecr959 on 2011-02-16
> **mc4man said:**
> 
You could also try at login > Classic - no effects,

This is the way I'm using Natty.     Its very stable, - I would say problem free.  I'm going to stay with the "classic - no effects"  option until Beta.

---

### Post by PaulW2U on 2011-02-17
> **ecr959 said:**
> This is the way I'm using Natty.     Its very stable, - I would say problem free.  I'm going to stay with the "classic - no effects"  option until Beta.
I'm trying it too as I'm seeing too many strange things happening and I'm having difficulty reporting them right now. I'll switch back to "Classic Desktop" or Unity when the updates and fixes start rolling in.

---

### Post by Enternald on 2011-02-17
For whatever reasons, gnome-panel in classic mode doesn't show up unless you choose to run no effects mode. Thats strange because I have thought that in normal if effects shouldn't be supported, panel should be reloaded. Even more: ```
gnome-panel
``` from terminal doesn't work output is that WM already have panel or whatever. Still when I run panel from root terminal everything works.
In no-effects mode I have no problems whatsoever. 
My question is still valid does someone else experience Unity's menu search field not working (or the menu as whole.)?

---

### Post by mc4man on 2011-02-17
> My question is still valid does someone else experience Unity's menu search field not working
The search from the global menu > places does not work, hasn't in a long time, if ever. Same for nautilus > go to some extent
> or the menu as whole.
That works fine, though from fresh start always need to open something first before it becomes active

The other searches - (dash, the 2 places), they work so -so, better several days ago.
Also am now  seeing a small memory leak in compiz when using them

The "Search for Files' in applications (gnome-search-tool) works fine, can be added to the launcher

---

### Post by Enternald on 2011-02-17
> That works fine, though from fresh start always need to open something first before it becomes active

Well I will give a try, but as I remember that didn't worked (I have in mind unity's menu with apps not gnome menu). And what you open from fresh start: I tried g-terminal, Firefox, nautilus. But when I click i.e.  Games icon, the window is empty.

EDIT: Still doesn't work

---

### Post by cariboo on 2011-02-17
When clicking on the Ubuntu icon in the top left corner, I get the menu items, but it just takes me to /usr/share/application, when clicking any of the icons. The only thing that has been implemented so far are the menu items. I'd suggest clicking on the icon with the triangle and scissors (applications menu) if you want to start a program that isn't in the panel.

---

### Post by Enternald on 2011-02-17
I see : I wanted to know if it is implemented or not. Now everything is clear. Waiting future updates :D.

---

### Post by cariboo on 2011-02-17
There is a Unity update coming later today, but I don't see anything about the menu's

---

