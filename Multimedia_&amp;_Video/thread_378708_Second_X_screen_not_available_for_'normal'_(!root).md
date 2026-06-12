---
title: "Second X screen not available for 'normal' (!root) user"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by pirannia on 2007-03-07
Configuration: NVidia 6800 GS, dual screen (LCD + TV), TV in mode "HD720" (1920x720), screens configured on separate devices (no TwinView,  no Xinerama).

Problem: when logging as root, the TV screen shows up, I can use it as a normal X screen BUT when logging as a normal user (groups: users, adm), I can only use the LCD screen (on my monitor), the TV screen displays the X server dotted background and I only see the mouse pointer moving in it (no desktop, no menus, nada).

I've excluded any drivers and xorg.conf problems since logged as 'root' works just as I wanted.

Any ideeas I can try before deleting the 'normal' user and creating a new one (potentially having the same issue) ?

---

