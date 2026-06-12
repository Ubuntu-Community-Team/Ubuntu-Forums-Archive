---
title: "opening dir.'s with something other than nautilus changes default"
date: 2010-08-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mc4man on 2010-08-28
Maybe this bug has been fixed though hasn't here thru updates on 2 installs 

Easily tested by r. clicking on a folder - open with - other application and picking something
If bug is still alive then when opening Places - Home folder the app just used will be the new default folder handler
(doesn't affect dir.'s on the Desktop

If so, once fixed then that app will never become the default again, new apps will till used once and fixed.
(anything listed directly from r. click - open with will not be set as new default

firefox is a good app to test with as it won't get hung up parsing the home dir. like many music players

While initially this line doesn't exist, after using anything but nautilus it will be created and the improper behavior can be observed there (if the bug is still happening
~/.local/share/applications/mimeapps.list
inode/directory=

---

### Post by mc4man on 2010-09-04
I guess I'll push this once, maybe it's just here, though have seen this for close to 2 months.
(or maybe very few actually ever open a dir. with anything other than nautilus, though that would change come release.
[orig.bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833") - though if present probably an upstream issue

---

### Post by dagrump on 2010-09-04
I gave it a me too, I guess I hadn't ran into it till today.

---

### Post by mc4man on 2010-09-04
dagrump - 
Thanks for taking a look - so I guess it's not just here.

If you have the time or inclination to go back to lp and change the status from 'new' to 'confirmed' that would be great.

(just click on New in the Status column   and you'll get a pop up.

---

### Post by dagrump on 2010-09-04
Confirmed.

---

### Post by mc4man on 2010-10-04
The cause of this is the 'Remember this application...' option seen whenever using the 'open with other application' from the context menu.

It is enabled by default and will change the default folder handler to whatever app is chosen.
If unchecked then the app chosen will still be added to the 'open with' menu but the default folder handler will stay with nautilus.

Personally have grown tired of this (having to uncheck), so have patched nautilus to not enable the option (plus have added back the "umount option"

Have suggested that the repo version do the same - make the box inactive by default or even remove the option altogether. (has no real value

I believe it will remain as is even though it would only take about 5 sec's to fix (considered an upstream issue - don't quite get that.

---

