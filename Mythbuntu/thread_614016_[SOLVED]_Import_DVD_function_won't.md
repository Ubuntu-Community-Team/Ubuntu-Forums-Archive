---
title: "[SOLVED] Import DVD function won't"
date: 2007-11-15
forum: Mythbuntu
---

### Post by meanmrmustard on 2007-11-15
I have used the Import DVD function once a couple days ago and it worked flawlessly. Today I'm attempting to import another dvd and it just keeps telling me:
"No jobs or anything else to do. You could hit 0 to rip a dvd"

Anyone have a clue what's wrong?

---

### Post by superm1 on 2007-11-15
Check and see if mtd is running.  It should start when you hit 0.  If not, check out /var/log/mythtv/mythfrontend.log and ~/.xsession-errors.

---

### Post by meanmrmustard on 2007-11-15
> **superm1 said:**
> Check and see if mtd is running.  It should start when you hit 0.  If not, check out /var/log/mythtv/mythfrontend.log and ~/.xsession-errors.

Well, 'top' reports mtd is sleeping - which I guess it should be until I press 0, yes?
Logs and errors file showed nothing suspicious.

---

### Post by superm1 on 2007-11-16
> **meanmrmustard said:**
> Well, 'top' reports mtd is sleeping - which I guess it should be until I press 0, yes?
Logs and errors file showed nothing suspicious.
Perhaps try killing it and launching it manually in a terminal to see if you catch mtd output.

---

### Post by gsrcrxsi on 2007-11-16
i had this problem and it was that i did not have the dvd decoder installed. do you have libdvdcss2 installed?

---

### Post by meanmrmustard on 2008-01-03
Tried again a couple days later and it worked fine.
go figure!?

---

