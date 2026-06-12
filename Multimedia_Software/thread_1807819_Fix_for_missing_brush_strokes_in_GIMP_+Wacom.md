---
title: "Fix for missing brush strokes in GIMP +Wacom"
date: 2011-07-19
forum: Multimedia Software
---

### Post by chitarrino on 2011-07-19
Fix for the annoying bug that lets GIMP 2.6 miss some brush strokes when drawing.

Type this in a terminal window.
```
xsetwacom set "Serial Wacom Tablet stylus" TabletPCButton on
```

Replace "Serial Wacom Tablet stylus" with the name of your device, you can find it by typing
```
xsetwacom --list
```

This setting won't be remembered if you log out. To make it permanent, add it to your startup scripts.

---

