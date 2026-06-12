---
title: "[SOLVED] Unable to schedule recordings after power outage"
date: 2008-10-18
forum: Mythbuntu
---

### Post by toddk111 on 2008-10-18
I'm running a frontend/backend using Ubuntu Hardy with Mythbuntu contol center.  I have two Dvico Fusion5 USB tuners and an HDhomerun unit.  

My set up was working and was in the middle of recording a show when I bumped the power cord resulting in a reboot.  Now when I try to schedule a recording, it doesn't show up in the upcoming recordings list and it doesn't record.  Also, when I try too watch live tv, I get bumped back to the menu.  What can I do to fix this problem?

Thanks,
Todd

---

### Post by ian dobson on 2008-10-19
Hi,

Sounds like database corruption. Try repairing your database.

mysqlcheck -u root -p --auto-repair --check --optimize --all-databases

The run mythtv-setup to check that everything is still there.

Regards
Ian Dobson

---

### Post by toddk111 on 2008-11-10
That worked, thanks!

---

### Post by zzztownsend on 2009-01-03
fixed it for me too after I accidentally filled my root file system up to 100% and got same symptoms

cheers

matt

---

### Post by PeteCress on 2009-01-20
Please ignore this stub of a post.

It finally dawned on me that "[SOLVED]" in the thread name probably means nobody's looking at the thread anymore.   Consequently I moved my post to a new thread: "Unable To Schedule Recordings & Cannot Repair DB".

---

