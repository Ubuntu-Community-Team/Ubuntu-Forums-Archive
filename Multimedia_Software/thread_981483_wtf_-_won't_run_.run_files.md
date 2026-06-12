---
title: "wtf - won't run .run files"
date: 2008-11-13
forum: Multimedia Software
---

### Post by stealthc on 2008-11-13
They worked with the same os before, so wtf is going on here?  I can't install enemy territory (either quake wars or wolfenstien) because it won't run a .run file.....
:( installed fine the last time I tried to on my old hardy install
same damned install, it's still hardy, so wtf??

---

### Post by minky311 on 2008-11-13
Try right clicking the file and choosing properties. Once the window has opened click on **Permissions** and check the box next to **Allow executing file as program**

---

### Post by cariboo on 2008-11-13
Are your .run files executable? To make them executable in a terminal type:

```
chmod +x ~/Desktop/*run
```

This assumes your .run file is on the desktop. This will also make any other .run files on your desktop executable.

Jim

---

