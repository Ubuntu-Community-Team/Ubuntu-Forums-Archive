---
title: "compiz options"
date: 2011-03-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ngsupb on 2011-03-20
Hi guys!


Can someone help to figure out how to check and change the compiz's startup options in 11.04? 

I would like to make sure that "loose binding" and "indirect rendering" are enabled.

---

### Post by cariboo on 2011-03-20
Are the options in ccsm?

---

### Post by Amaranth on 2011-03-20
Loose binding no longer exists, we use a hybrid of the loose and strict methods from 0.8 that gets you the best of both.

Indirect rendering is still an option and I think you can set the /desktop/gnome/session/required_components/windowmanager gconf key to 'compiz --indirect-rendering' to get what you want there but it'll probably break the legacy session options. Otherwise you could edit /usr/bin/gnome-wm to do it but that'll go away when the package that provides it is upgraded.

---

### Post by ngsupb on 2011-03-21
> **Amaranth said:**
> Loose binding no longer exists, we use a hybrid of the loose and strict methods from 0.8 that gets you the best of both.

Indirect rendering is still an option and I think you can set the /desktop/gnome/session/required_components/windowmanager gconf key to 'compiz --indirect-rendering' to get what you want there but it'll probably break the legacy session options. Otherwise you could edit /usr/bin/gnome-wm to do it but that'll go away when the package that provides it is upgraded.


Got it, thank you. Just trying to get some better performance on nvidia+compiz. Having a problem with it.

---

