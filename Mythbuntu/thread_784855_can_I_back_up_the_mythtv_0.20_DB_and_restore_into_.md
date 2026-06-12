---
title: "can I back up the mythtv 0.20 DB and restore into 0.21?"
date: 2008-05-06
forum: Mythbuntu
---

### Post by bareflix on 2008-05-06
I have a working mythdora install running mythtv 0.20. I would like to re-install it with the new mythbuntu since I am more familiar with ubuntu than fedora. I only went with fedora, because at the time mythbuntu had bad nvidia drivers.
Anyway, all my videos are on their own partition, so that's not a problem, but I need to know what to do to move my database. Some of the notes I've seen indicate that there are schema changes between 0.20 and 0.21, but since this will not be an upgrade, but a re-install, I haven't seen anything that describes how to handle this situation.
Any suggestions?
--
Chris

---

### Post by sessions on 2008-05-07
Gday.

I beleive you can do this.

I just migrated from a 0.19 Ubuntu MythTV installation to the new Mythbuntu release with 0.21.

I did a DB backup of only the recordings and schedules according to                        [this page]("http://www.mythpvr.com/mythtv/tips/migrate-recordings.html").                                              

During the backup of the data, I used the -c switch (read the comments of the linked article for details. My attempts without the -c failed).

Then I did a complete fresh installation (on a new HDD just to be safe!) and imported the data once I was finished.

I got all my recordings back, along with schedules.

There may well be an easier way - but this took me hardly any time and worked. So, the basic answer is I would assume on the basis I migrated from 0.19, you can do it from 0.20

HTH.

---

### Post by bla2000 on 2008-05-07
Section 23.5 and 23.7 should help.

[http://www.mythtv.org/docs/mythtv-HOWTO-23.html#backupdb]("http://www.mythtv.org/docs/mythtv-HOWTO-23.html#backupdb")

---

### Post by murchball on 2008-05-07
Personally, I'd try it in a virtual machine first. Even though you tuners and whatnot aren't there, it should give you a good indication of how the database upgrade will go.

---

