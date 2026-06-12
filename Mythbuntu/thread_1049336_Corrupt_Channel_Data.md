---
title: "Corrupt Channel Data"
date: 2009-01-24
forum: Mythbuntu
---

### Post by ghuber on 2009-01-24
Ever since I switched my Myth TV box from analog to digital and the channel numbers changed, I have been having problems with two of my channels program data.

These two channels have channel data but it is incorrect and none of it has show information (episode name, desc, etc)

If I look a few days ahead, the lineup is correct.

So I run:
mythfilldatabase --refresh-today

This works and fills today with data....  but only for a few minutes...  then it reverts back to the previous bad data.

so I ran:
mysqlcheck -r -u <username> -p <password> mythconverg

followed by:
mythfilldatabase --refresh-today

Still no change.
Next I ran:
mythfilldatabase --do-channel-updates

followed by a refresh
still get the same problem.
I ran a --refresh-all
still get the same error.


HELP!!
:D

---

### Post by ghuber on 2009-01-24
PS
Even though the data is correct in the future.  When the day arrives, the data changes to bad data.

---

