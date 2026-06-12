---
title: "HowTo Copy channel setted list (xmltv) on another system??"
date: 2008-12-15
forum: Mythbuntu
---

### Post by impossibilechecisiaquesto on 2008-12-15
Hi i've a working mythtv system with my satellite box ( SKY Italy) where i alredy setted and edited the channel list and the channel numbers grabbed by xmltv.

Now i installed another mythtv system in my father's house, he has also another Satellite Receivers (SKY) the same of mine.

How can i copy the settings i alredy made in my mythtv system, saving, believ me,  a lot of time??

Thanks.
Martino.

---

### Post by dmfrey on 2008-12-15
> **impossibilechecisiaquesto said:**
> Hi i've a working mythtv system with my satellite box ( SKY Italy) where i alredy setted and edited the channel list and the channel numbers grabbed by xmltv.

Now i installed another mythtv system in my father's house, he has also another Satellite Receivers (SKY) the same of mine.

How can i copy the settings i alredy made in my mythtv system, saving, believ me,  a lot of time??

Thanks.
Martino.

I use these db backup and restore scripts.  Download them and execute the backup on your machine and the restore on your father's machine.

[http://www.mythtv.org/wiki/index.php/Database_Backup_and_Restore](http://www.mythtv.org/wiki/index.php/Database_Backup_and_Restore)

The restore script allows you to do a partial restore which just does the recording information.  I believe you can also specify specific tables to restore.  This is where you would want to restore your channel data.  You may have to play with the mappings in the database once they are restored.

I hope this helps.

---

### Post by impossibilechecisiaquesto on 2008-12-15
thanks, i try this way!


THANK YOU. WAS SO USEFUL!

---

