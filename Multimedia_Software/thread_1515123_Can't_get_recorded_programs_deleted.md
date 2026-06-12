---
title: "Can't get recorded programs deleted"
date: 2010-06-21
forum: Multimedia Software
---

### Post by Deborah Norling on 2010-06-21
We are running Mythbuntu karmic. We can delete recordings but they never actually get removed.

We have tried deleting the recordings using mythweb, and we've also tried deleting using mythfrontend. Either way, the recordings disappear from the mythweb or frontend screens which show the listings of recorded programs, but the files are not removed.

After we exit the interface and restart either mythweb or the mythtv frontend, the list of recorded programs continues to show all recordings we attempted to delete before.

According to the documentation, recordings aren't actually deleted, but instead moved to a deleted recordings group. However we see no such group in the drop-down list of groups that appears in either interface. And I find nothing in the mythtv documentation or wikis that tells you how to make the deleted recordings group visible or how to really remove a program from the database and physically from the hard disk.

I did find the three perl scripts flush_deleted_recgroup.pl, myth.find_orphans.pl and optimize_mythdb.pl. They do seem to remove old stuff and make the database smaller and faster, but it was my impression they were mainly used if you moved or copied the database, or if your database became corrupted. As far as we know, our database isn't corrupted; the problem is simply that deleting doesn't work.

Ideally I want to have delete work as expected. All suggestions are welcome.

--Deborah Norling

---

