---
title: "Unable to delete recorded programs"
date: 2010-06-23
forum: Mythbuntu
---

### Post by Deborah Armstrong on 2010-06-23
We are running Mythbuntu karmic. We can delete recordings but they never actually get removed.

We have tried deleting the recordings using mythweb, and we've also tried deleting using mythfrontend. Either way, the recordings disappear from the mythweb or frontend displays which show the listings of recorded programs, but the files are not removed.

After we exit the interface and restart either mythweb or the mythtv frontend, the list of recorded programs continues to show all recordings we attempted to delete before.

According to the documentation, recordings aren't actually deleted, but instead moved to a deleted recordings group. However we see no such group in the drop-down list of groups that appears in either interface. And I find nothing in the mythtv documentation or wikis that tells you how to make the deleted recordings group visible or how to really remove a program from the database and physically from the hard disk. Also the script "flush_deleted_recgroup.pl" reports no deleted recordings.

I did find the three perl scripts flush_deleted_recgroup.pl, myth.find_orphans.pl and optimize_mythdb.pl. They do seem to remove old stuff and make the database smaller and faster, but it was my impression they were mainly used if you moved or copied the database, or if your database became corrupted. As far as we know, our database isn't corrupted; the problem is simply that deleting doesn't work. If we delete and then run these scripts, some things do disappear, but not every program we deleted goes away. What does get removed seems to be random.

I don't think this is a permissions problem because I've tried successfully deleting media files of recordings using rm. And that works fine, no matter which username I'm logged in as. That creates orphans in the database, but the scripts do clean those orphans out. 

Ideally I want to have delete work in the frontend and in mythweb as expected. All suggestions are welcome.

-- Deborah Armstrong

---

### Post by David Grigor on 2010-06-23
Sounds like a similiar behavior I had where it wasn't a permissions issue. 

If you haven't done so already first try turning off the slow delete setting:

The slow delete setting is under mythtv-setup on the backend under the general settings.


For more details:
[http://ubuntuforums.org/showthread.php?t=1319699&highlight=slow+delete+setting](http://ubuntuforums.org/showthread.php?t=1319699&highlight=slow+delete+setting)

---

