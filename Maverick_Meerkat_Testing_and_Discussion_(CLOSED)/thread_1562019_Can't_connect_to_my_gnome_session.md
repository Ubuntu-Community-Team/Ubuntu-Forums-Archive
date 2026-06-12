---
title: "Can't connect to my gnome session"
date: 2010-08-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Souris on 2010-08-27
Since recent updates (notably since yesterday's xorg-ati, xorg-radeon) I can't anymore connect myself to my gnome session.

It always come back to login screen.

precision : all was fine since I checked 'sync with vblank' under ccsm

and I don't know how to change this option with command line.

Cheers, Souris.

---

### Post by pulpo69 on 2010-08-27
since latest updates, gnome has no panels and i can't get them back.

---

### Post by Gregorybekkers on 2010-08-27
try this 

rm -r ~/.gconf/apps/panel


> **pulpo69 said:**
> since latest updates, gnome has no panels and i can't get them back.

---

### Post by pulpo69 on 2010-08-27
hi gregory,
i tried it, but it didn't change anything.

---

### Post by Gregorybekkers on 2010-08-27
> **pulpo69 said:**
> hi gregory,
i tried it, but it didn't change anything.


Did you restart gnome afterwards?

---

### Post by donniezazen on 2010-08-27
I too am not able to login to Gnome session.

---

### Post by pulpo69 on 2010-08-27
yes i restarted gnome, but nothing changed.

---

### Post by Souris on 2010-08-28
PLEASE! Can we come back to my original problem???

pulpo69 : sorry but this ISN'T a thread about gnome panel problems => open your own thread please.

soham_1207 : do you have sync to vblank checked under ccsm?

I have ATI Radeon HD 4200, with opensource driver, 64 bits

#-o

---

### Post by mc4man on 2010-08-28
> change this option with command line.
Don't gave any ati so not sure this is your issue - though somewhat doubt it is.
Anyway  - 

```
gconftool-2   --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank "True"

```

---

### Post by Souris on 2010-08-28
Hourrraaa!!!!!

many thanks mc4man !!! it works!!!

I've disabled sync to vblank with :

gconftool-2   --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank "False"

SO :

sync to vblank ON  => BUG
sync to vblank OFF => OK


(not sure if my original post was clear, english is not my natural language)

---

### Post by mc4man on 2010-08-28
Glad you got it sorted out - seems strange, (as a nvidia user), that you can't boot with vsync enabled - hope they get that fixed at some point.
(if vsync is needed

---

