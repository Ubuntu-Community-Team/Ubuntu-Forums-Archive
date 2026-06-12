---
title: "How to copy a channel list on a new system??"
date: 2009-01-30
forum: Mythbuntu
---

### Post by maxpower_italy on 2009-01-30
Hi, i build a new mythtv system in a other house, how can i copy my channel list (found with xmltv) in this system? saving a lot of time??

Thanks.

---

### Post by liquidhot on 2009-01-30
I think all of that data is stored in the SQL backend. So theoretically you could copy the data by exporting/importing through a SQL tool. But it's not for the faint of heart and I wouldn't recommend it. Is there no Internet access on the new PC?

---

### Post by ian dobson on 2009-01-31
Hi,

The "normal" channhel data is stored in the "channel" table (For analog and digital channels) and for digital channels there are extra tables "dtv_multiplex" and "dtv_privatetypes" whichhold the multiplex data.

I would recommend setting up a new myth system normally rather than trying to copy bits together.

Regards
Ian Dobson

---

### Post by impossibilechecisiaquesto on 2009-01-31
SO i have to set again any channel number manually?? We have the same channels, there isn't a way to copY??

---

### Post by ian dobson on 2009-01-31
Hi,

Yes you can copy the chanels, I just don't recommend it.

If you really want to copy the channel data just use mysqldump to export the data to a file then import it with mysqladmin

see [http://www.sixapart.com/movabletype/docs/3.2/01_installation_and_upgrade/mysql_backup_restore.html](http://www.sixapart.com/movabletype/docs/3.2/01_installation_and_upgrade/mysql_backup_restore.html)

You need to export/import the followig tables  "channel","dtv_multiplex" and "dtv_privatetypes"

Don't blame me if it brakes.

Regards
Ian Dobson

---

