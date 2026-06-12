---
title: "Unity: unwanted dark shadow under the upper panel"
date: 2011-04-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by meanpt on 2011-04-19
A new dark shadow strip under the upper panel and overlapping the upper apps window's panel is now shown. I don't want it. How to disable it?

---

### Post by cubeist on 2011-04-19
I too hate the panel shadow. There is no way to turn it off, but there is a workaround.

The graphic for the shadow is at
```
/usr/share/unity/3/panel-shadow.png
```

Open in gimp, use the eraser and remove the gradient. (make it transparent).

A couple notes,
- need to be superuser to save the changes in gimp
- every time you update unity the panel will revert to original with gradient
- backup the panel-shadow.png before making changes.

---

### Post by mc4man on 2011-04-19
If you are not using the Unity MT Grab Handles plugin (pretty worthless unless you have a supported touch device), then disabling the Png plugin in ccsm will also remove the 'shadow'

---

### Post by cubeist on 2011-04-19
> **mc4man said:**
> If you are not using the Unity MT Grab Handles plugin (pretty worthless unless you have a supported touch device), then disabling the Png plugin in ccsm will also remove the 'shadow'

Perfect, thanks!

---

### Post by DBO on 2011-04-19
I don't know if it will help or not but the shadow has been made lighter in the next release.

---

### Post by meanpt on 2011-04-21
:) ....for the time being, it seems everything went normal again .... no more shadowing ...

ED: arrrhggghhggg --- oh no, they put it back again ... but why are they using it? Any time I use firefox the thing hides the tabs .... bah ...

---

### Post by coffeecat on 2011-04-21
> **mc4man said:**
> If you are not using the Unity MT Grab Handles plugin (pretty worthless unless you have a supported touch device)

Far from being worthless, I find the grab handles useful on a conventional desktop with 24" monitor and mouse. :|

---

### Post by kaldor on 2011-04-21
> **cubeist said:**
> I too hate the panel shadow. There is no way to turn it off, but there is a workaround.

The graphic for the shadow is at
```
/usr/share/unity/3/panel-shadow.png
```

Open in gimp, use the eraser and remove the gradient. (make it transparent).

A couple notes,
- need to be superuser to save the changes in gimp
- every time you update unity the panel will revert to original with gradient
- backup the panel-shadow.png before making changes.

lol, reminds me of the good ol' ducktape method.

---

