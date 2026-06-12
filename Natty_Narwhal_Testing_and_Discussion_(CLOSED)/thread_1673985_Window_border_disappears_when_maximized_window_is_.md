---
title: "Window border disappears when maximized window is not focused"
date: 2011-01-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ikkefc3 on 2011-01-23
Window border disappears when maximized window is not focused while using Compiz without unity.

For example:
I have Firefox maximized and click on another window (IM for instance), the title bar disappears/goes completely transparent.

How can I make it not transparent/disappear when it loses focus?

---

### Post by pressureman on 2011-01-23
I was just about to post the same thing... this has been bugging me for about a week now, and I was hoping it was just something transient.

At a guess, I'd say it's a side effect of the global menu stuff that's been going for.... you guessed it.... Unity.

---

### Post by pressureman on 2011-01-31
Is this still happening for anyone? I guess I'm probably in the minority here, using gnome classic desktop. I just wondered whether a fresh install would help...

---

### Post by rburkartjo on 2011-01-31
i did notice that when i could boot into the classic desktop but since i changed my screen resolution to 1400 x 900 i cant get classic to load into anything that will work. 3 and 2d at least loads decently.

---

### Post by tjeremiah on 2011-01-31
yes and its very annoying. Its been happening since the beginning.

---

### Post by Starks on 2011-01-31
Confirming and it is very disruptive to my workflow.

---

### Post by Harry33 on 2011-01-31
This Compiz (0.9.2.1+glibmainloop4-0ubuntu8) update here might be of help:

```
compiz (1:0.9.2.1+glibmainloop4-0ubuntu8) natty; urgency=low

  * debian/patches/14_fix_empathy_list_vanish.patch:
    - fix the buddy list disappearing (LP: #682781)
  * debian/patchs/15_hidden_maximized_decoration.patch:
    - fix sometimes invisible decoration on maximized window still decorated
  * 16_display_unfocused_state.patch:
    - fix unfocused state not being displayed properly in the decoration
      (LP: #704413)

```

Here (should be in Natty repos already):
[https://launchpad.net/ubuntu/natty/+source/compiz/1:0.9.2.1+glibmainloop4-0ubuntu8](https://launchpad.net/ubuntu/natty/+source/compiz/1:0.9.2.1+glibmainloop4-0ubuntu8)

---

### Post by mc4man on 2011-01-31
> This Compiz (0.9.2.1+glibmainloop4-0ubuntu update here might be of help
that should take care of this particluar compiz mis-behavior

---

### Post by pressureman on 2011-01-31
> **Harry33 said:**
> This Compiz (0.9.2.1+glibmainloop4-0ubuntu8) update here might be of help:

Yep, that fixes it for me.

---

### Post by tjeremiah on 2011-01-31
speaking of compiz, instead of me creating another thread, is the "PLACE WINDOWS" option in Compiz manager opening up for anybody else? Every time I click to open it to create settings, it doesnt open .

---

### Post by mc4man on 2011-01-31
> is the "PLACE WINDOWS" option in Compiz manager opening up for anybody else

Works fine here, actually was just in switching placement for the moment to 'centered'. While not assured it may help prevent the creation of an invisible window till that compiz issue is fixed.

Try a restart (restart, not logout/in

---

