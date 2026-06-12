---
title: "missing close minimize maximize buttons"
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jakejh on 2010-09-20
I just upgraded to ubuntu beta 10.10 and now the close minimise and maximise buttons are missing i tried everything I could find but nothing worked

---

### Post by cariboo on 2010-09-20
Press Alt-F2 and type:

```
metacity --replace
```

to see if that brings your buttons back.

---

### Post by jakejh on 2010-09-22
I tried that already it doesn't work

---

### Post by slooksterpsv on 2010-09-22
ALT+F2 -> type in : gconf-editor - click on OK
Then navigate to: 
Apps -> Metacity -> General
Do you have a button layout there? If so what's listed there? May need to replace whats there with 

close,minimize,maximize:

---

### Post by jakejh on 2010-09-23
I tried that already that didn't work

---

### Post by cariboo on 2010-09-23
Does this happen with all themes, or just one in particular?

---

### Post by slooksterpsv on 2010-09-24
I wonder what:
dpkg-reconfigure metacity
would do?

---

### Post by jakejh on 2010-09-24
> **cariboo907 said:**
> Does this happen with all themes, or just one in particular?


it happens with all themes but only when the window is maximised

---

### Post by slooksterpsv on 2010-09-25
> **jakejh said:**
> it happens with all themes but only when the window is maximised

Try: dpkg-reconfigure metacity

---

### Post by jakejh on 2010-09-25
> **slooksterpsv said:**
> Try: dpkg-reconfigure metacity

that didn't work either

---

### Post by cariboo on 2010-09-25
Can you show us a screenshot?

---

### Post by jakejh on 2010-09-25
[ATTACH]170494[/ATTACH]




screen shot    attached   [IMG]file:///home/jake/Desktop/Screenshot.png[/IMG]

---

### Post by seeker5528 on 2010-09-25
> **jakejh said:**
> [ATTACH]170494[/ATTACH]




screen shot    attached   [IMG]file:///home/jake/Desktop/Screenshot.png[/IMG]

If you hold down the 'Alt' key and drag the window around, what do you see then?

Later, Seeker

---

### Post by jakejh on 2010-09-25
> **seeker5528 said:**
> If you hold down the 'Alt' key and drag the window around, what do you see then? 


i'm using compiz so it just stretches and unmaximized thought i can't see any close maximise minimise buttons until it unmaximises

---

### Post by seeker5528 on 2010-09-25
> **jakejh said:**
> i'm using compiz so it just stretches and unmaximized thought i can't see any close maximise minimise buttons until it unmaximises

Sound like they are not missing then, just covered by the panel.

Is this after you maximized the window or is that how it shows up when the app is newly opened?

My best guess is either something is off when it opens maximized, or it's not opening maximized and since the window is larger than the space between the panels that whatever window placing logic is being used is causing the window to be placed higher than Docky instead of lower than the top panel.

In either case I generally expect that if you resize the window to a little less than the maximized size, it should open that size the next time, but it doesn't seem to work that way with every application. 

Later, Seeker

---

### Post by jakejh on 2010-09-25
> **seeker5528 said:**
> Sound like they are not missing then, just covered by the panel.

Is this after you maximized the window or is that how it shows up when the app is newly opened?

My best guess is either something is off when it opens maximized, or it's not opening maximized and since the window is larger than the space between the panels that whatever window placing logic is being used is causing the window to be placed higher than Docky instead of lower than the top panel.

In either case I generally expect that if you resize the window to a little less than the maximized size, it should open that size the next time, but it doesn't seem to work that way with every application. 



its not that they are missing i have the panel set to transparent and i can't see anything threw it also even if if turn docky off the window just extends downwards but the buttons are still missing

---

### Post by Framli on 2010-09-25
Do you have the Maximus package installed? It might be the cause.

---

### Post by jakejh on 2010-09-26
> **Framli said:**
> Do you have the Maximus package installed? It might be the cause.

ya that was the cause I uninstalled Maximus restarted and now everything is fine thanks

---

### Post by ktp on 2010-09-26
> **jakejh said:**
> ya that was the cause I uninstalled Maximus restarted and now everything is fine thanks

Nice!!  Can you please mark the thread solved then (see Thread Tools link at the top)?

---

