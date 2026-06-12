---
title: "Remove Hosts/FrontEnds from Database"
date: 2009-10-16
forum: Mythbuntu
---

### Post by bsntech on 2009-10-16
Hi folks -

I noticed that over the time of me playing with several front-ends, I have four in the database now (I see this when going to the MythWeb Settings under MythTV and see the "Edit Settings For: " box in the upper right corner.

Is there a quick way to delete the extra hosts and configuration out of the database that is no longer needed?  That would help to optimize the database a bit.

Thank you.

---

### Post by ian dobson on 2009-10-16
Hi,

Just manually edit your settings table, deleting all entries for host XXX.


To optimise your database just do mysqlcheck --optimize -A from a terminal window.

Regards
Ian Dobson

---

### Post by bsntech on 2009-10-16
Easy enough, thank you Ian.

---

