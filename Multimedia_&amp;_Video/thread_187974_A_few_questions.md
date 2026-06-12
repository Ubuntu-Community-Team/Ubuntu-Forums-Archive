---
title: "A few questions"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by shoeshinecs on 2006-06-03
How do I add Rosegarden 1.2.3 and ZynAddSubFX to the Ubuntu Studio menu? How do I remove apps that I don't want? Specifically, Pitivi and mPlayer.
There's no help documentation for Rosegarden 1.2.3. Does anyone know how to install it?

---

### Post by dolson on 2006-06-03
I'm pretty sure Rosegarden 1.2.3 is not in Ubuntu, it's some weird version, 1.0-1.2ubuntu2.

ZynAddSubFX has in incorrect menu entry location. The Studio Launcher script currently only searches in one location for .desktop files, and this is /usr/share/applications. Two solutions exist. Copy the ZynAddSubFX .desktop file into here, or fix the .desktop file location in the package and submit it to REVU.

To add an application to the blacklist, edit ~/.ubuntustudio2config and add any applications you wish to add to the line that says BlackList.

---

