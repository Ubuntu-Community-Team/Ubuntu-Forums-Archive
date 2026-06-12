---
title: "User 'ntp' appears in gdm login list"
date: 2011-01-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ubername on 2011-01-16
I recently installed ntp packages to allow syncing of my clock to network servers. Since then a user 'ntp' appears in the list of users at login, but does not appear in the 'users and groups' admin tool. I reckon this may be a bug in whatever installs the ntp stuff. However, I believe the GDM list is supposed to only contain users where UID>1000 and I believe my ntp user has UID 114 so possibly a bug with GDM?


Any clues, and also tips how I might remove the 'ntp' user from the login list, e.g. via command line?

---

### Post by ubername on 2011-03-03
Recent updates fixed this. Marking 'Solved'

---

