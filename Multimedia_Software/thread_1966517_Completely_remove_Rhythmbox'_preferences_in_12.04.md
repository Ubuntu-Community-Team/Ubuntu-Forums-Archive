---
title: "Completely remove Rhythmbox' preferences in 12.04"
date: 2012-04-27
forum: Multimedia Software
---

### Post by dumdidum on 2012-04-27
I'm trying to get rid of all Rhythmbox settings. Googling suggested that
```
rm -rf ~/.gnome2/rhythmbox ~/.local/share/rhythmbox .gconf/apps/rhythmbox
```
should do the trick but it doesn't. Upon starting Rhythmbox for the first time after executing above command it still remembers a bunch of custom settings (e.g., it still remembers my unusual library location which is on another partition and not the standard ~/Music, it still remembers the columns I set for the browser, etc.)

What else do I need to delete in order to completely reset the application?

---

### Post by ajgreeny on 2012-04-27
To make sure you have every reference to RB in your home, use the command ```
locate rhythmbox | grep $USER
``` in terminal to see if you have missed anything in your user's home folder/partition.

All I can see on my 10.04 that may exist, but I'm not sure about in 12.04, is ~/.gconf/apps/rhythmbox... but I have no idea if that exists any more.

---

### Post by dumdidum on 2012-04-27
> **ajgreeny said:**
> 
All I can see on my 10.04 that may exist, but I'm not sure about in 12.04, is .gconf/apps/rhythmbox... but I have no idea if that exists any more.
Thanks!

I did remove .gconf/apps/rhythmbox as well. There was a typo in the above post. My bad.

```
locate rhythmbox | grep $USER
```
gives me four locations:

~/.cache/rhythmbox
~/.gconf/apps/rhythmbox
~/.gnome2/accels/rhythmbox
~/.local/share/rhythmbox

Despite removing those four directories, Rhythmbox still remembers my custom settings :confused: It's quite odd.

---

### Post by mc4man on 2012-04-27
Try installing dconf-tools & then opening dconf-editor

Browse to org > gnome > rhythmbox, expand & see what you can adjust or set back to default there, screen of the db key

---

### Post by dumdidum on 2012-04-27
mc4man,

this did the trick! thanks a lot :)

---

### Post by daddyfix on 2012-11-18
Thanks!

---

