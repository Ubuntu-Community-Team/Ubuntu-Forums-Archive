---
title: "cronjob for firefox"
date: 2015-01-17
forum: Mythbuntu
---

### Post by deanie44 on 2015-01-17
Hi everyone.  I would like to configure a cronjob to backup firefox.  I have read several articles, but I am still lost.  Can someone please give me instructions on how to perform this task?  Any assistance will be helpful.  deanie 44

---

### Post by ajgreeny on 2015-01-17
To backup what of firefox?

To backup the configuration and profile that you currently have you will need to backup the hidden **.mozilla** folder in your home; if you also want to backup the firefox cache, though I can't see any good reason for doing so, you'll also need to backup the hidden **.cache/mozilla** folder in your home.

What application do you use, or want to use to backup these folders? I suspect rsync is probably the easiest to use to make a backup that is incremental, but it depends what hardware you use for the backups you make, etc etc. so more info please.

---

### Post by deanie44 on 2015-01-17
Hi ajgreeny.  I quess I would use rsync.  I do not understand the about what hadrware would I use?  I frequently use deja dup for backups. How would I configure a cronjob for deja dup?  Thanks for your help.  deanie44

---

### Post by ajgreeny on 2015-01-17
My hardware query related to what you store the backup on; there is little point in making a backup but keeping it on the same disk as the original.

So do you keep backups on a separate disk away from the computer;do you use cloud storage?  I do not even know if rsync works with the cloud as I don't store anything in the cloud.

---

### Post by deanie44 on 2015-01-17
ajgreeny, I would store the backup on a usb external harddrive. Thanks again.  deanie44

---

