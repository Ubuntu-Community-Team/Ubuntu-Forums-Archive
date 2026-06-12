---
title: "What backup?"
date: 2011-10-29
forum: Mythbuntu
---

### Post by zaurus on 2011-10-29
After unsuccessful upgrade to 11.10 I decided to do a fresh install of 11.10. I need your advise what to backup before doing this. I have backed up /var/lib/mythtv and home directory. I have a lot of recordings then I used this machine to download files, then mail, then there are some special settings.
I am unhappy of cause to do that, but I cannot get GUI after upgrade, that is why this decision.

Any help appreciated.

---

### Post by nickrout on 2011-10-30
> **zaurus said:**
> After unsuccessful upgrade to 11.10 I decided to do a fresh install of 11.10. I need your advise what to backup before doing this. I have backed up /var/lib/mythtv and home directory. I have a lot of recordings then I used this machine to download files, then mail, then there are some special settings.
I am unhappy of cause to do that, but I cannot get GUI after upgrade, that is why this decision.

Any help appreciated.

From the mythtv perspective you need to backup your database [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

And your data, by default in /var/lib/mythtv (which you have covered).

As far as your mail is concerned, this is outside the scope of this forum, it depends on where you downloaded it to etc. Do you have a mail server that you are running, or is it simply running a mail client like thunderbird?

---

### Post by zaurus on 2011-10-30
> **nickrout said:**
> From the mythtv perspective you need to backup your database [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

And your data, by default in /var/lib/mythtv (which you have covered).

As far as your mail is concerned, this is outside the scope of this forum, it depends on where you downloaded it to etc. Do you have a mail server that you are running, or is it simply running a mail client like thunderbird?

Thanks for your answer.
I am running just mail client.
What about all special settings proper to my system. What directories are important? /etc, any other?

---

### Post by nickrout on 2011-10-30
Then your mail is probably in your home directory somewhere.

/etc contains many system settings, but ask yourself how many you have actually changed? Back it up,, but don't restore it blindly.

---

