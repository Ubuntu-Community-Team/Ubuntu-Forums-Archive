---
title: "Mythbuntu 9.04 frontend startup unresponsive until lots of keys pressed"
date: 2009-08-14
forum: Multimedia Software
---

### Post by bd1 on 2009-08-14
Using Mythbuntu 9.04 on power up when the frontend has started it doesn't respond until a key has been pressed many times. It doesn't matter how long the PC has been left since power up - tried half an hour or so. If I quit the frontend and restart it, it is fine.

Any suggestions? The same hardware worked fine under 8.04. I have just re-installed after installing a new hard disk.

NOTE: Already posted on [Mythbuntu]("http://ubuntuforums.org/forumdisplay.php?f=301") forum.

---

### Post by bd1 on 2009-08-17
I've finally worked out what is happening. The Update Manager is running in the background and although it is not visible it is taking the keypresses. I think I was just getting lucky eventually and managing to quit it. As I do most of my testing via VNC I wasn't able to do Alt-TAB to bring it into the foreground. I don't know exactly how it was getting started, but I suspect I managed to stupidly put in it in a save session. Now it isn't running everything is fine.

---

