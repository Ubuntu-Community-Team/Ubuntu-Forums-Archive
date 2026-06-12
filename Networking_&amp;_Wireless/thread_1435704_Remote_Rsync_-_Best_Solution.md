---
title: "Remote Rsync - Best Solution?"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-03-21
I currently have Ubuntu with Samba running. The XP boxes here back up to my rig via SyncBack SE - a Windows application that simply backs up source to destination. Since SyncBack allows me to put in credentials for it to auto-login, and then sync, it works out.

But someone here wants to switch from XP as their main OS to Ubuntu. Okay, fine. But I still want to have these users automatically back their stuff up in the same manner. The only difference is we're working with Ubuntu/Ubuntu instead of XP/Ubuntu.

What's the best solution for this department? I've used rsync, but only from drive to drive. Is there a way I can handle these tasks with an rsync frontend application or by any other means?

---

### Post by 98cwitr on 2010-03-21
first off you need to define "backup"

I use Simple Backup Suite to backup my /var /home /usr/local and /etc dirs, but you can customize it however you want, and with Samba, you can do it via your network and current box. 

 [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

### Post by Roasted on 2010-03-21
By backup I just mean for the data to be replicated on the network drive (samba drive) in my computer. I never got into the zipped backup packages... I just prefer the data to be sync'd over in its raw form.

---

