---
title: "Where frontend called on launch?"
date: 2009-07-11
forum: Mythbuntu
---

### Post by chrispoole on 2009-07-11
Hi guys,
I am having some issues with the frontend upon launch.

I want to add some extra flags to the frontend call, to get some more logs.

Where is mythfrontend called from, on startup?

I'm running Mythbuntu 9.04, as frontend and backend.

Thanks.

---

### Post by Verzweifler on 2009-07-11
Try the Desktop's Mainmenu - Applications - Settings - Session and Startup... Go to the Autostart Programs Tab and you'll find the activated MythTV Frontend entry.

I only disabled it on my Backend, but I am pretty sure that you can just "add" a new entry for the frontend with all the flags you need. But watch out, do only check one of the entries otherwise you'll have two frontends running...

---

### Post by joho500 on 2009-07-12
That's handled by the file mythtv.desktop in you home folder ~/.config/autostart. You can also add options there.

Joost.

---

