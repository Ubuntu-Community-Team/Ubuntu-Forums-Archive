---
title: "Myth backup"
date: 2010-12-10
forum: Mythbuntu
---

### Post by williammanda on 2010-12-10
I was going to do a clean install of mythtv but wanted to use the backup function to cut down on the setup. If I have recordings, videos, etc... Will the backup contain that info? If so how would I handle this info when applying the backup to the new installation?

---

### Post by williammanda on 2010-12-10
Also if I backup from a remote frontend... will the backend get saved?

---

### Post by tgm4883 on 2010-12-10
Backup only saves settings, not media. You can backup the database from a frontend only machine. I believe to restore it you would need to restore it from the backend

---

### Post by williammanda on 2010-12-10
Is there any information on the backup function? I would like to see how to restore. Also I don't have the backup / restore option on my FE / MBE computer in MCC. It's only on a remote FE.

---

### Post by tgm4883 on 2010-12-10
> **williammanda said:**
> Is there any information on the backup function? I would like to see how to restore. Also I don't have the backup / restore option on my FE / MBE computer in MCC. It's only on a remote FE.

It's only in 10.10. I don't think i've written any documentation on it yet as it's still pretty young. Basically what it does is backup certain files and the database, then to restore it just copies the files back to their original location. The database backup/restore just uses the backup and restore scripts from MythTV

---

### Post by williammanda on 2010-12-10
OK thanks for the update. I have a FE running 10.10 and a FE / MBE runing 10.4, both with the latest .24 mythtv. I ran the backup function on the FE running 10.10 so could I install 10.10 on the FE / MBE and then restore the backup and have my original database?

---

### Post by tgm4883 on 2010-12-10
> **williammanda said:**
> OK thanks for the update. I have a FE running 10.10 and a FE / MBE runing 10.4, both with the latest .24 mythtv. I ran the backup function on the FE running 10.10 so could I install 10.10 on the FE / MBE and then restore the backup and have my original database?

If you checked the option to backup the database then yes.

I'd have to check the code but IIRC it will reset the mythtv password for you.

---

### Post by williammanda on 2010-12-10
Well I tried to restore the backup once I got mythtv installed and got this error (see attached png).

---

### Post by tgm4883 on 2010-12-10
> **williammanda said:**
> Well I tried to restore the backup once I got mythtv installed and got this error (see attached png).

Can you send me the exact steps you took to get that? I've seen a bug report on it and two people report it (you are the third), but I cannot reproduce it at all :(

---

### Post by williammanda on 2010-12-12
1st I tried to re-install the backup before I installed mythtv then I waited until I installed mythtv. I got the error before and after I tried to install the backup.

---

