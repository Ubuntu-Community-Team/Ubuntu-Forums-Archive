---
title: "Orphans script not in 0.27?"
date: 2014-10-10
forum: Mythbuntu
---

### Post by mattlach on 2014-10-10
Hey all,

I was looking to do a cleanup of orphans, but the maintenance folder doesn't seem to contain this script in 14.04...

Is there a way to do this on this version?

Thanks,
Matt

---

### Post by aelfric55 on 2014-10-10
> **mattlach said:**
> Hey all,

I was looking to do a cleanup of orphans, but the maintenance folder doesn't seem to contain this script in 14.04...

Is there a way to do this on this version?

Thanks,
Matt

The script is available on the wiki: [http://www.mythtv.org/wiki/Find_orphans.py](http://www.mythtv.org/wiki/Find_orphans.py)

Though it is listed as supported only on Mythtv 0.24-0.26, I use it frequently on 0.27.3, and it works fine. As the wiki says, check your python version if it errors out on line 27.

---

### Post by mattlach on 2014-10-10
Thank you.

What - exactly - does the script do.

Does it just remove database entries for missing files, or does it also add database entries for files without them?

Also, if you manually move a recording from one location to another, the back end will look for it in this new location.

Does the orphans script also do this? (Look in other folders) or does it just remove the database entry if it is not where expected?

Thank you,
Matt

---

### Post by aelfric55 on 2014-10-15
> **mattlach said:**
> Thank you.

What - exactly - does the script do.

Does it just remove database entries for missing files, or does it also add database entries for files without them?

Also, if you manually move a recording from one location to another, the back end will look for it in this new location.

Does the orphans script also do this? (Look in other folders) or does it just remove the database entry if it is not where expected?

Thank you,
Matt

The primary backend and all secondary backends should be running and connected. The script searches the primary and secondary backends' named storage directories and mythtv directories for: 1) orphaned database entries without surviving recordings files. 2) orphaned recordings files where the database metadata has been deleted (the detritus left over from watching live tv, and otherwise when mythtv has simply failed to delete the recordings files selected for deletion, which appears to happen fairly frequently), and 3) "other" files, which include things like leftover .png preview files from deleted recordings, 0-byte files, .tmp files leftover from transcoding, and extra automatic weekly database backups.

The script reports back its findings and gives you the option of deleting any category from the various categories of orphans it has found, or refreshing the search. After you have selected a category to delete, the script deletes the category and reports back again, allowing you to select any of the remaining categories for deletion. When you're done, you exit the script with a ctrl-c.

The script does not add database entries to mythconverg. The old myth_rebuilddb perl script used to do this, but it unfortunately ceased to be a  viable option after about Mythtv 0.25. Nowadays orphaned recordings without mythconverg entries that you want to keep are just supposed to be moved into "videos". A bit annoying, to be sure.  

In general, you can move recordings from directory to directory within a storage group without any issue at all, but you can't from backend to backend and have mythtv find them. The find_orphans script doesn't change this.

---

