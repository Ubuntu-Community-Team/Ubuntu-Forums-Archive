---
title: "Damn that Metadata"
date: 2011-02-19
forum: Mythbuntu
---

### Post by mattneub on 2011-02-19
Been running Mythbuntu for a about six-months.  Installed with MythTV 0.23 originally.

Within the frontend the "Watch Videos" links to a windows shared drive on the LAN mounted on machine.

I kept losing my metadata on the external videos, they'd download fine, then when I leave the "Watch Videos" screen and come back the metadata was gone.  Thought an upgrade to MythTV 0.24 would fix it.

Installed the automatic updates repositories and updated everything.  Now when I startup the frontend I get the message "MythTV wants to upgrade your database for the video schema, from 1034 to 1038,.." it gives this a go, but can't update the database apparently as when I log back in it give me the same message, and the "Watch Videos" link doesn't work any longer.

Any thoughts out there, do I need to do something to manually update the database?  

I've dug through the backend options and don't see the option to do this, nor do I see anything in the Control Center.

---

### Post by tgm4883 on 2011-02-19
Backend and frontend logs are necessary to help you here. You can grab these with mythbuntu-log-grabber


It sounds like there is a permission issue on your machine, the metadata images aren't getting saved.

---

### Post by nickrout on 2011-02-19
> **mattneub said:**
> Been running Mythbuntu for a about six-months.  Installed with MythTV 0.23 originally.

Within the frontend the "Watch Videos" links to a windows shared drive on the LAN mounted on machine.

I kept losing my metadata on the external videos, they'd download fine, then when I leave the "Watch Videos" screen and come back the metadata was gone.  Thought an upgrade to MythTV 0.24 would fix it.

Installed the automatic updates repositories and updated everything.  Now when I startup the frontend I get the message "MythTV wants to upgrade your database for the video schema, from 1034 to 1038,.." it gives this a go, but can't update the database apparently as when I log back in it give me the same message, and the "Watch Videos" link doesn't work any longer.

Any thoughts out there, do I need to do something to manually update the database?  

I've dug through the backend options and don't see the option to do this, nor do I see anything in the Control Center.

read this thread

[http://ubuntuforums.org/showthread.php?p=10473229#post10473229](http://ubuntuforums.org/showthread.php?p=10473229#post10473229)

---

