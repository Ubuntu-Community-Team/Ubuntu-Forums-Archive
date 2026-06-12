---
title: "Best way to backup my mythbuntu setup?"
date: 2010-02-05
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-02-05
Pretty much as per the title really, what is the "best" way to back up my mythbuntu setup?  

Can i just use my ubuntu back up?

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

If not, whats the best way to back up the basic system?  (Im not too bothered about backing up any recordings more just the core system setup).

---

### Post by JohnYYC on 2010-02-07
Well I store my recordings on a separate drive so I use [_Clonezilla_]("http://clonezilla.org/") to just image my OS drive. It is a very powerful tool.

---

### Post by kja999 on 2010-02-07
Include a mysqldump of the database somewhere. I have it hourly to a NAS for safekeeping.

---

### Post by geekyhawkes on 2010-02-07
Im not too fussed about the sql database, its more the OS setup i am concerned about.  I will give clonzilla a look see.

Thanks.

---

### Post by JohnYYC on 2010-02-07
At first glance it may seem to be a complex tool to use but if you read all the prompts it is actually easy to use in my mind.

---

### Post by AKADAP on 2010-02-07
> **geekyhawkes said:**
> Im not too fussed about the sql database, its more the OS setup i am concerned about.  I will give clonzilla a look see.

Thanks.

The database is important because that is what keeps a record of the TV episodes you have already watched so it won't re-record them.

---

