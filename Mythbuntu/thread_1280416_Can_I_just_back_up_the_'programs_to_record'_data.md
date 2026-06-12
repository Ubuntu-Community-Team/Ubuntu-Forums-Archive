---
title: "Can I just back up the 'programs to record' data?"
date: 2009-10-02
forum: Mythbuntu
---

### Post by ubnewbie2 on 2009-10-02
I want to start fresh with a new install of 9.10 when it is released.  

Can I just keep the database info from my old system, that tells mythtv which programs to record?  I was thinking I could just use mysql tools to save that table (is it only one table?) and restore it after my new install is done.  Would there be any issues due to the table definition changing, or is it stable between recent mythtv schemas?

---

### Post by Caysho on 2009-10-02
[Yes, have a read]("http://ubuntuforums.org/showthread.php?t=1029248") :)
The schema is not consistent between releases, but for the additional data you will need to fill in the blanks.
I had to update the chanel ID's and default storage location for my recording data.

---

### Post by ubnewbie2 on 2009-10-02
> **Caysho said:**
> [Yes, have a read]("http://ubuntuforums.org/showthread.php?t=1029248") :)
The schema is not consistent between releases, but for the additional data you will need to fill in the blanks.
I had to update the chanel ID's and default storage location for my recording data.

Thanks, with that info, I hope I can figure it out.

---

