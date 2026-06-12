---
title: "Upgraded from .25 to .26 and the secondary backend won't connect to the database"
date: 2013-08-31
forum: Mythbuntu
---

### Post by tdcarlo on 2013-08-31
Hi,

As I said in the title, I upgraded from .25 to .26.  On my master backend, I had some problems connecting to the database.  It turns out that mysql wasn't enabled.  I fixed that in the control center.  Next, I set up a frontend on my computer that went smooth as could be.  Finally, I upgraded my secondary backend.  I followed the exact same steps as when I did the master backend.  I reboot the machine and it says "could not connect to the database".  I thought "Oh, I've seen this before.  I'll go to the control center and enable mysql."  It turns out that it is not an option in the control center if the computer is a secondary backend.  The only option is to run setup which gets me a second screen screaming "could not connect to the database."  

I've compared the settings (IP address, ports, passwords, etc)  on the working frontend to the not working secondary backend/front end and they are identical.   My thoughts are that mysql is not enabled but I cannot figure out how to enable it.  I'll happily take all advice and suggestions.
Thanks in advance for any help,
Troy

---

### Post by tdcarlo on 2013-09-01
I have no idea what changed but I woke this morning and its working fine.  It solved itself!

---

