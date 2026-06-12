---
title: "Mythbuntu 9.10 Upgrade hiccups"
date: 2009-10-30
forum: Mythbuntu
---

### Post by dotnick on 2009-10-30
I haven't seen anyone else report this, but I was using the avenard repository for 0.21+fixes.  I backed up my database using the scripts and then started the upgrade process.  Two things that I found.

My first run through didn't upgrade MySQL or the mythtv packages noting that the upgrade process thought that the 0.21+fixes were newer.  For some reason this created MySQL problems as it wouldn't start the daemon.  So I updated all those packages using aptitude and MySQL started working.

Now MythBackend Setup works fine, but both MythWelcome and MythFrontend hang.  When looking at the console, it seems to be in a Wake-On-Lan loop for both cases, but the frontend and backend are on the same machine.  Does anyone know where I should look for the hangup?  I've already checked the /usr/bin/mythfrontend file, but don't see any references to wakeonlan in there.

I'm half ready to wipe the database out, create new, get the frontend up and running and then try to restore using the scripts.

---

