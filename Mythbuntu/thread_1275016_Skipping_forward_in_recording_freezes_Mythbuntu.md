---
title: "Skipping forward in recording freezes Mythbuntu"
date: 2009-09-25
forum: Mythbuntu
---

### Post by Crusty Juggler on 2009-09-25
I've had my Myth system working perfectly well for quite awhile now, but all of the sudden today a problem sprang up from nowhere.

If I try to skip ahead or rewind in a recording, the picture freezes while the audio continues, though the audio is a bit stuttery.  Occasionally the audio speeds up as well, as though it is playing back at about 1.5 times the normal rate.

At first I thought this was due to too much CPU demand on the system due to commercial flagging at the same time, but stopping all other jobs and rebooting did not solve the issue.  Also, this occurs with both newly recorded programs and old ones, so it is not the recording itself.

Sorry I can't provide any logs, as I am not sure where to look.  If anyone can direct me to which logs might be helpful, please do.  Thanks in advance.

---

### Post by Crusty Juggler on 2009-09-26
Sorry to bump, but this is pretty much making Mythbuntu nearly useless for me.

---

### Post by SiHa on 2009-09-27
Maybe your database has got corrupted somehow, I think it's quite common.

Myth uses seektables in the database to help it FF/RW through it's recordings. I would imagine that if these are messed up it might cause the problem you have.

You could try the repair / optimize functions available from Mythweb.

**backend.server.IP.address/mythweb/settings/database**

PS, the logs should be in **/var/log/mythtv** if this doesn't help.

---

### Post by Crusty Juggler on 2009-09-27
> **SiHa said:**
> Maybe your database has got corrupted somehow, I think it's quite common.

Myth uses seektables in the database to help it FF/RW through it's recordings. I would imagine that if these are messed up it might cause the problem you have.

You could try the repair / optimize functions available from Mythweb.

**backend.server.IP.address/mythweb/settings/database**

PS, the logs should be in **/var/log/mythtv** if this doesn't help.

That did it.  Which I don't understand because one of the first things I tried was "Optimise Tables" in the Mythbuntu Control Centre.

Whatever... it works now.  Thank you!

---

