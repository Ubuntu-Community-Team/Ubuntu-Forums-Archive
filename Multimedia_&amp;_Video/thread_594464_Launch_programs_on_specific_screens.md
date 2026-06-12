---
title: "Launch programs on specific screens"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by boast on 2007-10-28
I would like to add pidgin in "startup programs," but the problem is, I do not have xinerama enabled because I game. So the screens being seperated, I need pidgin to open up on the second monitor. Is there a command in order to achieve this? 

something like, I dunno..

-workspace_index="display:0.1"

:confused:

---

### Post by sloggerkhan on 2007-10-31
so are you saying you have a dual head setup or what?

---

### Post by akShane on 2007-11-04
Try putting this in as the command:

env DISPLAY=:0.1 pidgin

Haven't tried it as a startup program, but it works as a launcher.

---

