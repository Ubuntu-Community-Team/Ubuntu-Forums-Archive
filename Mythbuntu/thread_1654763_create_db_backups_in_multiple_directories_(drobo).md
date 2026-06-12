---
title: "create db backups in multiple directories (drobo)"
date: 2010-12-28
forum: Mythbuntu
---

### Post by iitywygms on 2010-12-28
Hi All:

I have a cron job that backs up my database to a specified directory.
It works great. However, I would like to add another location for backups. Redundancy. (I want the data backed up to two different locations at the same time)
I have a drobo that I would like to use.  The directory I would like to use on the drobo is at /media/usb0/backups.
This is my current backuprc
DBBackupDirectory=/D2/backups This works fine.

How can I add the drobo directory to this?

thanks

---

### Post by newlinux on 2010-12-29
I don't use the built in backup capabilities, I have my own scripts so I can't help you with that. But in case no one answers you consider running your own backup script that backs it up to both places or use cron to copy the initial backup to your additional location.

Good luck.

---

