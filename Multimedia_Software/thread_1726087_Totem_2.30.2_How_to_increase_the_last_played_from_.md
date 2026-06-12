---
title: "Totem 2.30.2 How to increase the last played from 5 to 20"
date: 2011-04-10
forum: Multimedia Software
---

### Post by Sidewinder1 on 2011-04-10
Is there a configuration file that I need to amend in order to increase the number of "last played" files (currently limited to 5) in the Movie drop down. I would like it to list the last 15 or 20 that I have opened.

Tia,
Side

---

### Post by mc4man on 2011-04-10
> Is there a configuration file that I need to amend in order to increase the number of "last played" files
I don't believe so, the # is set in the source as shown below (I'm on natty so may be slightly different line # than natty's, probably around line 519 give or take  ), so you'd need to build from source

/src/totem-menu.c
 ```
               g_free (label);

                if (++n_items == 5)
                        break;
```
If you changed the 5 to fifteen then that's what you'd get

---

### Post by Yellow Pasque on 2011-04-10
I made a simple patch and uploaded it to Launchpad: [https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages)
Just download the totem packages you want and install them (don't subscribe to the PPA, because it has other stuff in it).

---

### Post by Sidewinder1 on 2011-04-11
Many thanks guys.
Side

---

