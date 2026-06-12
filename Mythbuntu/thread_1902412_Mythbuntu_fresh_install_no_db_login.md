---
title: "Mythbuntu fresh install no db login"
date: 2011-12-30
forum: Mythbuntu
---

### Post by wyliecoyoteuk on 2011-12-30
After a fresh install of Mythbuntu 11.10 on an empty hard drive, I get "failure to login to database"!
Any ideas where to start?
surely the most basic install should configure and start the services?

---

### Post by nickrout on 2011-12-30
> **wyliecoyoteuk said:**
> After a fresh install of Mythbuntu 11.10 on an empty hard drive, I get "failure to login to database"!
Any ideas where to start?
surely the most basic install should configure and start the services?

where and when does this error message manifest itself?

sounds like you missed a config step during installation.

---

### Post by wyliecoyoteuk on 2011-12-31
Install runs through fine, then on first login, when starting to configure the frontend or backend,I get the error.
I have checked the SQL user and password, it is correct, user is in mythtv group, etc.
Every time I have done a fresh install before, (since 8.10) it has just worked.

---

### Post by wyliecoyoteuk on 2011-12-31
Looking a little closer, it would seem that mythconverg had not been created during install for some reason, although everything seemed to go fine.
Reran the install, and it all worked!

---

