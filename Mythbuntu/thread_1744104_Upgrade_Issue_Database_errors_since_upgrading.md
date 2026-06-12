---
title: "Upgrade Issue: Database errors since upgrading?"
date: 2011-04-30
forum: Mythbuntu
---

### Post by mr_luksom on 2011-04-30
I upgraded my FE and BE today, and I am noticing very sluggish starts to playback and browsing of recordings. Once recordings have started they are as per 10.10, as is non-database related menus (setup etc).

I am getting the following errors with '-v database' flag'.

Do I need to rebuild the database, or something like that?

```

2011-04-30 17:13:05.736 MythCoreContext: Connecting to backend server: 10.1.1.4:6543 (try 1 of 1)
2011-04-30 17:13:12.737 MythSocket(32e6e70:55): readStringList: Error, timed out after 7000 ms.
2011-04-30 17:13:12.737 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.

```

---

