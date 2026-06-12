---
title: "How to Backup a Whole Directory with Mythbackup.py"
date: 2014-03-16
forum: Mythbuntu
---

### Post by martin41 on 2014-03-16
I am sure this is a real simple thing to do but I am not sure of the syntax.  I use mythbackup.py in Mythbuntu to backup my MythTV database and a few select files.  I would like the ability to backup all the files in a directory and thought by just using a wildard * would allow this but it doesn't work.  You can see the code below and I am referring to the the ("/usr/local/bin/*",) portion.  If someone could tell me how to do this properly I would really appreciate it, thanks. 


```
 ## Array of files to Backup
        BACKUPFILES = [
        "/etc/mythtv/config.xml",
        "/home/hartmanmythtv/.mythtv/config.xml",
        "/etc/mythtv/mysql.txt",
        "/etc/lirc/lircd.conf",
        "/etc/lirc/hardware.conf",
        "/usr/local/bin/*",
        "/etc/hostname",
        "/etc/hosts",
        ]
```

---

### Post by tgm4883 on 2014-03-17
> **martin41 said:**
> I am sure this is a real simple thing to do but I am not sure of the syntax.  I use mythbackup.py in Mythbuntu to backup my MythTV database and a few select files.  I would like the ability to backup all the files in a directory and thought by just using a wildard * would allow this but it doesn't work.  You can see the code below and I am referring to the the ("/usr/local/bin/*",) portion.  If someone could tell me how to do this properly I would really appreciate it, thanks. 


```
 ## Array of files to Backup
        BACKUPFILES = [
        "/etc/mythtv/config.xml",
        "/home/hartmanmythtv/.mythtv/config.xml",
        "/etc/mythtv/mysql.txt",
        "/etc/lirc/lircd.conf",
        "/etc/lirc/hardware.conf",
        "/usr/local/bin/*",
        "/etc/hostname",
        "/etc/hosts",
        ]
```


Hmm, I hadn't anticipated that someone would want to do that. Currently there isn't a way to add a whole directory using just *. Have you tried just adding 
```
/usr/local/bin
```

---

### Post by martin41 on 2014-03-17
What do you know that worked, I guess the simplest way is sometimes the correct way.

One other question, is there a way to rotate backups and have files delete after a certain number of backups ie 7?

---

### Post by tgm4883 on 2014-03-17
> **martin41 said:**
> What do you know that worked, I guess the simplest way is sometimes the correct way.

One other question, is there a way to rotate backups and have files delete after a certain number of backups ie 7?

I don't believe these is currently a way to do that. Best you could do would be to make a cron job that deletes files older than X

---

### Post by martin41 on 2014-03-18
I will have to look into that as I have been deleting them manually.  Thanks again for your help.

---

