---
title: "[SOLVED] Live TV Dead..."
date: 2008-03-20
forum: Mythbuntu
---

### Post by nasha on 2008-03-20
Some time in the last 24hrs, live tv no longer works. I noticed i didnt have any recordings :( If i try to watch live tv, it returns to the main menu, with the following output in terminal:
```

2008-03-21 00:56:01.279 Connecting to backend server: 192.168.1.100:6543 
(try 1 of 5)
2008-03-21 00:56:01.280 Using protocol version 40
2008-03-21 00:56:01.298 TV: Attempting to change from None to 
WatchingLiveTV
2008-03-21 00:56:01.299 Using protocol version 40
2008-03-21 00:56:02.348 GetEntryAt(-1) failed.
2008-03-21 00:56:02.349 EntryToProgram(0@Thu Jan 1 10:00:00 1970) failed 
to get pginfo
2008-03-21 00:56:02.349 TV Error: LiveTV not successfully started
2008-03-21 00:56:02.350 TV Error: LiveTV not successfully started
2008-03-21 00:56:02.401 TV: Deleting TV Chain in destructor
2008-03-21 00:56:02.422 DPMS Deactivated 
2008-03-21 00:56:02.423 DPMS Reactivated.

```

Any ideas?

---

### Post by nasha on 2008-03-20
Permissions on the new HDD i added weren't allowing write access to mythtv.
The error message didnt really reflect the problem though...

---

### Post by Jummel on 2009-03-25
> **nasha said:**
> Permissions on the new HDD i added weren't allowing write access to mythtv.
The error message didnt really reflect the problem though...

What do you mean by permissions on the new HDD? I'm having this issue trying to set Myth to work over my network. What permissions did you change?

Thanks

---

### Post by novellahub on 2009-03-25
He must mean he changed the permissions or ownership so that the user Mythtv can use it.

When adding a new drive to a mythtv box, you need to first give write permissions:

```
chmod 775 [name of folder location]
```

Then make it so the mythtv user and group has rights:

```
chown mythtv:mythtv [name of folder]
```

---

