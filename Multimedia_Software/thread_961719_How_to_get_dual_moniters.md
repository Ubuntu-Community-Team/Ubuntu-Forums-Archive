---
title: "How to get dual moniters?"
date: 2008-10-28
forum: Multimedia Software
---

### Post by EgoManiak on 2008-10-28
I have a Compaq presario v2000 laptop and a dell crt monitor that i want to use with an extended desktop configuration. i am BRAND NEW to linux, so this might be an easy fix.

---

### Post by overdrank on 2008-10-28
> **EgoManiak said:**
> I have a Compaq presario v2000 laptop and a dell crt monitor that i want to use with an extended desktop configuration. i am BRAND NEW to linux, so this might be an easy fix.

Hi and welcome, you can try and use the atl, F2 keys and enter the command ```
gksu displayconfig-gtk
``` 
Also what is the model of the graphics card? You can use the command in the terminal ```
lspci
``` look for VGA and this is the graphics card.
If you are using nvidia then you may try and use the command ```
gksu nvidia-settings
``` to setup your extra monitor there.

---

