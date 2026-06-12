---
title: "mythtv-database upgrade error"
date: 2009-08-26
forum: Mythbuntu
---

### Post by bcg30506 on 2009-08-26
Setting up mythtv-database (2:0.21.0+fixes-21366-openglvdpau2-nv190-0ubuntu0) ...
Failed to connect to database (incorrect admin password)
Failed to create or modify database (incorrect admin username/password?)
Try:
sudo dpkg-reconfigure mythtv-database

What if anything should I do about this?  I already have a working and very populated database.  If I ran this manually, do I risk losing it?  Does this package update the database structure?

---

### Post by mpp on 2009-10-31
Hi,  I've experience this problem too during upgrade from jaunty to karmic.  Solution is to let mythtv-frontend do the upgrade for you, see my post in this thread: [http://ubuntuforums.org/showthread.php?p=8208881](http://ubuntuforums.org/showthread.php?p=8208881)

have fun()
mike

---

