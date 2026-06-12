---
title: "What plugin is this in unity/compiz?"
date: 2011-01-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-01-17
If anyone happens to know - 

When there are multiple windows of the same app open a click on the launcher icon 'pulls' them into a display screen where one can pick a window to bring to the front (focus
Usually it's just a single click on the icon, sometimes a double followed by a single.

It's a fairly useful function that seems semi broken atm - previously it would pull all open same app windows even if on multiple workspaces. Now it only works if the multiple windows are on 1 workspace
screen is an ex. of the display screen w/ 4 terminals open

---

### Post by anders_c_ on 2011-01-17
I believe that's the "Scale" plugin under window management.

---

### Post by anders_c_ on 2011-01-17
I believe that's the "Scale" plugin under window management.

---

### Post by mc4man on 2011-01-17
> I believe that's the "Scale" plugin under window management.
Thanks, it does seem to be that, will have to take a look..
(the basic super+a does work fine, though that pulls all open windows, some of the other's do, window groups doesn't here
Also not sure how the compiz settings relate to unity launcher in this case

---

### Post by Gourgi on 2011-01-17
> **mc4man said:**
> Thanks, it does seem to be that, will have to take a look..
(the basic super+a does work fine, though that pulls all open windows, some of the other's do, window groups doesn't here
Also not sure how the compiz settings relate to unity launcher in this case

in my maverick machine the combination to scale through window group (windows of the same owning program (e.g. GIMP windows) is "Super+q", you can try that.

But the main question is a mystery for me too... : 
> **What is the proper configuration i should have in order to scale window group when clicking any dock/launcher's icon (gnome-panel, awn, docky...) exactly as in unity-launcher ??**

Is this a unity-only hack ?
Is there some regexp/window matching magic behind this or am i just missing something?

---

### Post by shafin on 2011-01-18
> **Gourgi said:**
> in my maverick machine the combination to scale through window group (windows of the same owning program (e.g. GIMP windows) is "Super+q", you can try that.

But the main question is a mystery for me too... : 

Is this a unity-only hack ?
Is there some regexp/window matching magic behind this or am i just missing something?
You can do this by setting a shortcut for [I]"Initiate Window Picker for Window Group" on scale plugin in CCSM.
To set it to a button, install xdotool, and set the command 'xdotool key [COLOR=Blue]Ctrl+e[/COLOR]' as the target of your button where you replace the [/I]*[COLOR=Blue]Ctrl+e [/COLOR]*[I]part with your particular shortcut.
[/I]**

---

### Post by mc4man on 2011-01-18
> **Gourgi said:**
> in my maverick machine the combination to scale through window group (windows of the same owning program (e.g. GIMP windows) is "Super+q", you can try that.

Atm (at least here) none of the keyboard bindings work for window group or at least properly. (that's on compiz

It does however work thru the launcher icon, just not as good as it should.
(a couple of functions went semi south with the latest compiz/unity updates.
I guess I'll file a bug against unity if I can figure a half decent way to title it.

---

