---
title: "Remove mysql, but leaving Amarok"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by Aleksandersen on 2007-07-31
Hi,

How can I uninstall mysql without removing Amarok? I have setup and PostgreSQL database that I use with Amarok instead.

However Adept insist on removing Amarok when I select to remove mysql-common. How can I override this dependency?

*Thanks.*

---

### Post by Andrew-buntu on 2007-08-01
You could make your own package that removes the dependency but then you're off the beaten path and won't be getting updates through Ubuntu.
I would just keep the mysql service from starting.  That will keep it from using resources or being available to your network.  I *think* (sorry, away from my Ubuntu compy): ```
update-rc.d mysql remove
``` will do the trick.

---

