---
title: "How do I reset the Unity launcher?"
date: 2011-03-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Starks on 2011-03-07
I'm trying to wipe all current Unity settings, including icons I added to the launcher.

---

### Post by go7Ul1ai on 2011-03-07
> **Starks said:**
> I'm trying to wipe all current Unity settings, including icons I added to the launcher.

Open a fresh terminal then type:

```
unity --reset
```

---

### Post by Starks on 2011-03-07
Um, that doesn't bring back necessary icons that I removed or remove user-added icons.

---

### Post by mc4man on 2011-03-07
I think, (not sure) you may need to use 2 things
gconf-editor (/apps/compiz-1/plugins/unityshell/screen0/options/ )  to set any unity plugin changes back to defaults and the maybe this to reset the launcher (icon wise
```
gsettings reset com.canonical.Unity.Launcher favorite-migration
```
ck. out man gsettings

Edit: while the above did work 4 wks. ago to restore default favorites it was just a blip, now does something totally different...

Maybe at some point all this will end up in dconf-editor as displayed and editable settings?

---

