---
title: "Problem with Xorg, X, Xephyr, Fonts"
date: 2008-09-04
forum: Multimedia Software
---

### Post by cronos4d on 2008-09-04
Hello, 
I am trying to use freedesktop.org's Xephyr software and I am getting the following issue:

```
root@moblindev:/# xinit /etc/X11/xinit/xinitrc -- /usr/bin/Xephyr :4
-host-cursor -screen 800x600 -dpi 96 -ac
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Could not init font path element /usr/share/fonts/X11/cyrillic, removing
from list!
Could not init font path element
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
[config/hal] couldn't initialise context: (null) ((null))
waiting for X server to shut down FreeFontPath: FPE
"/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


I browsed the forums on this problem, but the solutions and speculations are
all too different to deduce any sort of conclusion.
Thanks for any suggestions.

```


Any help is appreciated.
I have already consulted the freedesktop and X.org mailing lists, but with no responses.

---

### Post by digambar.patankar on 2008-12-04
Hi,
I am getting the same problem.
If you find any solution please help me to get it solve.

help will be appreciated.

digambar.

---

### Post by cronos4d on 2008-12-12
Are you getting this problem specifically with Moblin? If so I do have a solution for you.

---

