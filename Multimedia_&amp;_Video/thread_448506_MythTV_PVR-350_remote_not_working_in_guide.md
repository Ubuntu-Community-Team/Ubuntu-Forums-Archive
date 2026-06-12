---
title: "MythTV PVR-350 remote not working in guide?"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by electronikjunkie on 2007-05-19
I got my Myth box completely setup, but I'm having a problem with my PVR-350 remote. The remote works fine on the 1st level of menu screens (ie, the first window you see when starting myth). It's when I go into a sublevel menu (manage recordings -> schedule recordings) it stops working except for the escape button. Also the remote works fine when watching live tv. I can change the channel, pause, record, change the vol, etc..., but when I go into the guide it only lets me move up once, down once, or right once, and then stops working. Has anyone see this problem before?

TK

---

### Post by electronikjunkie on 2007-05-21
Ah ha! I run mythfrontend with this command:
```
mythfrontend -display :0.1 &
```
My MythTV display is in another room. I had to move the mouse into the second screen and click on the MythTV window and then move my mouse back to screen one. Tricky tricky ;0>

---

