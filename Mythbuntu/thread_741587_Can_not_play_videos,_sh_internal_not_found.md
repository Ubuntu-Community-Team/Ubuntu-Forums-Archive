---
title: "Can not play videos, sh: internal not found"
date: 2008-03-31
forum: Mythbuntu
---

### Post by ir8trader on 2008-03-31
All:
     I had modified my DVD Player in Utilities / Setup -> Settngs -> Media Settings -> Video Settings -> Player Settings to use VLC, that woked fine but I had problems wih the windows manager and did not want to dig into figuring that one out (I've since found the answer, no need to go into it here). So I typed "Internal" (no quotes of course) into the "DVD Player Command" field. After that I now get the following error message in the mythfrontend.log:

sh: internal not found

Which I think is odd since I entered it with an uppercase I, and even saw in the log where it said 

"Registering Internal as a media playback plugin."

Any advice, I'm getting ready t just remove the mythtv package and reinstall it.

I am both a front end and a primary  backend

0.20.2-0ubuntu10 (Gutsy)

---

### Post by warp99 on 2008-03-31
Internal only works with version 0.21 of MythTV, which is in the backport repositories. 

I would suggest using Xine since it has support for DVD menus or install version 0.21.

Edit:

The reason is that the MythDVD plug-in was dropped and integrated with version 0.21.

---

