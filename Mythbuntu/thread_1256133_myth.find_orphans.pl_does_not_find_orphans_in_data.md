---
title: "myth.find_orphans.pl does not find orphans in database"
date: 2009-09-02
forum: Mythbuntu
---

### Post by bauner on 2009-09-02
My recording harddisk was died. Since July 2009 I have a new one, but in the database are all of the old recordings still present.

I tried
./myth.find_orphans.pl --user=mythtv --pass=5ygpvR0M --database=mythconverg --dodbdelete

It gives me the output:
Summary:
  Host: bauner-backend, Directories: /var/lib/mythtv/recordings
  881 valid recordings, 0 missing recordings
  1758 known media files using 346.7GB
  0 orphaned thumbnails with no corresponding recording
  0 unknown files using 0B

The numbers shows the correct count of files in the directory, but the old entries in the db are not deleted.

What can I do to remove the old database entries?

Thanks for your help

---

