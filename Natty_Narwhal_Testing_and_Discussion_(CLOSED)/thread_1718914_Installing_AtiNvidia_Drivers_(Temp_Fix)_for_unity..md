---
title: "Installing Ati/Nvidia Drivers (Temp Fix) for unity."
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Jerry421 on 2011-04-01
[SIZE=2]@ Anyone who is rebooting after installed Nvidia/Ati drivers and seeing  the classic Gnome Menu when you clearly want your unity menu. This is a  temporary fix that came to mind. It hides the gnome panel so you cant  see it. Hope this Helps![/SIZE]
**First:** ```
**sudo add-apt-repository** **ppa:unity/daily**
``` 
**Second: **```
**sudo apt-get update**
```[B]
Third: [/B]Open Update Manager and update.
**Forth:** Restart Delete **_BOTTOM_** bar
**Fifth: **right click top bar properties and change size to 21.
**Sixth:** Uncheck Expand Check Autohide Drag to right corner.
**Seventh:** System Settings>Startup Applications>Add> Name: Unity        Command: Unity
**Eighth:** Reboot
**Ninth:  **Enjoy :popcorn:

---

