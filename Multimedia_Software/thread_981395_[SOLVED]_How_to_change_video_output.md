---
title: "[SOLVED] How to change video output?"
date: 2008-11-13
forum: Multimedia Software
---

### Post by Izek on 2008-11-13
I know there's a setting somewhere that allows me to configure what handles video output (IE: x11 (no xv)) But I can't remember where that is in Hardy Heron.

---

### Post by sisco311 on 2008-11-13
press Alt+F2 and type:
```

gstreamer-properties
```
go to the video tab -> Default output -> Plugin

---

