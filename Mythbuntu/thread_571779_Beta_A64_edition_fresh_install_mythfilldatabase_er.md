---
title: "Beta A64 edition fresh install: mythfilldatabase error"
date: 2007-10-09
forum: Mythbuntu
---

### Post by obscure411 on 2007-10-09
Error occurs every time mythfilldatabase runs:

"ICE default IO error handler doing an exit(), pid = 6546, errno = 32"

It doesn't seem to prevent mythfilldatabase from running, because I was able to populate the database and add the channel icons, but get this error everytime.

I'll post the debug output if anyone thinks it will be useful, but didn't want to flood the forum with irrelevant information -- the verbose options on mythfilldatabase are quite extensive :)

Thanks!

---

### Post by superm1 on 2007-10-09
> **obscure411 said:**
> Error occurs every time mythfilldatabase runs:

"ICE default IO error handler doing an exit(), pid = 6546, errno = 32"

It doesn't seem to prevent mythfilldatabase from running, because I was able to populate the database and add the channel icons, but get this error everytime.

I'll post the debug output if anyone thinks it will be useful, but didn't want to flood the forum with irrelevant information -- the verbose options on mythfilldatabase are quite extensive :)

Thanks!

Please do file a bug on launchpad.  Verbose output would be good.  When this happens, does it trigger apport?  Apport will make you a crash report that you can use. 

If it did, close mythtv frontend, and then look in your bar by the network manager icon.  If a crash report was made, a little orange icon will be up there.  Click it to submit.

---

### Post by obscure411 on 2007-10-09
Nope -- it's not triggering apport.

I'll do a --v all output and post on launchpad now.

---

