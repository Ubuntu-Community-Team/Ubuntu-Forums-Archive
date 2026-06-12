---
title: "Why can other users control my volume?"
date: 2012-03-03
forum: Multimedia Software
---

### Post by x-shaney-x on 2012-03-03
If another user has logged in to my ubuntu system and altered the volume, such as turned it full blast or muted, my volume is set to however they left it when I log in.

This seems not only odd behaviour but unacceptable.

---

### Post by Aurauxis on 2012-03-03
The volume users can control is not "yours" to begin with.
Audio is managed at a root level, and is system-wide.

---

### Post by x-shaney-x on 2012-03-04
Yes but surely that shouldn't be the case.
Suppose one evening the missus is logged in and blasting out some death metal or something then logs out.
Next morning I go off to the library with the laptop and get disgusted looks off everyone?

---

### Post by Aurauxis on 2012-03-04
Try this solution:
Find "Startup Applications", and add a new entry.
Use this command:
```
amixer sset Master toggle
```Now any time you log on, the sound will be muted.

---

