---
title: "[SOLVED] cannot delete some shows"
date: 2009-01-03
forum: Mythbuntu
---

### Post by iitywygms on 2009-01-03
I messed up my system today but have mostly everything back and running as normal.  (I messed up the database/mysql)
I still have this issue
1.  When I was fixing the backend, I used root as the username in general setup.  During this time some shows recorded.  Now that I am back to using my original setup, I cannot delete the shows.  How can I manually delete these specific shows without deleting everything?  (when I delete them in the frontend they disappear for 5 seconds then re-appear.)
Thanks

---

### Post by newlinux on 2009-01-03
Find the actual files in your storage directory and change them to be world writeable (chmod a+r) or change the owner to mythtv. Then you should be able to delete them. If you use mythweb, an easy way to find out the filename look at the  backend logs which should show you the filenames that couldn't be deleted when you tried. Or you could use mythrename.pl as another quick way.

---

### Post by iitywygms on 2009-01-03
> **newlinux said:**
> Find the actual files in your storage directory and change them to be world writeable (chmod a+r) or change the owner to mythtv. Then you should be able to delete them. If you use mythweb, an easy way to find out the filename look at the  backend logs which should show you the filenames that couldn't be deleted when you tried. Or you could use mythrename.pl as another quick way.

Thank you very much that worked.  Now if I could only get mythweb to work.

---

### Post by newlinux on 2009-01-03
you're welcome, and that probably should have been chmod a+w instead of chmod a+r for others... My mistake.

---

