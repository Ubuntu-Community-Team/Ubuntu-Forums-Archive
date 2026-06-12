---
title: "zero byte mythfrontend.log"
date: 2008-06-13
forum: Mythbuntu
---

### Post by frego on 2008-06-13
Sometimes my mythfrontend.log has zero bytes with nothing in it, othertimes it fills up as expected.  Does anyone have any thoughts on what the problem might be?  Permissions and ownership look fine to me and the backend has no problems logging.  I do notice that the mythbackend.log is owned by the user, mythtv and the group mythtv while the mythfrontend.log is owned by my local user, group mythtv.  (my local user is in the group mythtv.

---

### Post by laga on 2008-06-13
How do you start the frontend? /var/log/mythtv/mythfrontend.log is only touched when you start mythfrontend using the menu entry or when using the autostart feature in Mythbuntu (because these run */usr/bin/mythfrontend --service* which enables logging).

---

### Post by frego on 2008-06-14
Right you are!  I created a shortcut to mythfrontend and put it on my desktop.  I'll start it from the menu now.  Does anyone know in XFCE how to put a shortcut on the desktop that passes the --service parameter?

---

### Post by laga on 2008-06-15
I wonder if you can just link the .desktop file to your Desktop/ folder?

---

