---
title: "Cannot Install DVD Styler"
date: 2010-02-17
forum: Multimedia Software
---

### Post by superfrogman94 on 2010-02-17
i find that i can no longer install dvd styler from the ubuntu software center.
it tells me the Package dependencies cannot be resolved. so i go to synapic to see if i could install it there and it tells me   Could Not mark all packages for installation or upgrade

and it says in the box below  dvdstyler:
 Depends: libavcodec-unstripped-52 but it is not going to be installed

anyone can help me? i do like this program and found it very helpful to author dvd's

EDIT: also when i try to go to the depend and install it gives me the same error : libavcodec-unstripped-52:
 Depends: libavcodec-extra-52 but it is not going to be installed., now i even installed the depends but i still recive the error..help

---

### Post by superfrogman94 on 2010-02-17
sorry for double post but i found a fix

to fix dependicies for dvd styler use the command

```
sudo aptitude install dvdstyler
```for some reason this actually worked well i guess this thread could be closed now :)

EDIT: hmm the update manager removes it but using aptitude gets it back....

---

