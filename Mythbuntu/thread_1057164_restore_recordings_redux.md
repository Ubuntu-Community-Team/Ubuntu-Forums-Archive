---
title: "restore recordings redux"
date: 2009-02-01
forum: Mythbuntu
---

### Post by itlarson on 2009-02-01
I've posted about this previously, and thought I had that answer, but no.
   I had to replace my motherboard and processor and now my mythtv install (suse based) won't boot.  Since I have wanted to try mythubuntu anyway I would like to install it,  but I can't figure out to restore my recordings.  If I had the mythconverg.sql file I could restore from this, but it doesn't exist.  How do I procede?

---

### Post by liquidhot on 2009-02-03
Perhaps this will help you?
[http://www.mythpvr.com/mythtv/tips/migrate-recordings.html](http://www.mythpvr.com/mythtv/tips/migrate-recordings.html)

---

### Post by klc5555 on 2009-02-03
> **itlarson said:**
> I've posted about this previously, and thought I had that answer, but no.
   I had to replace my motherboard and processor and now my mythtv install (suse based) won't boot.  Since I have wanted to try mythubuntu anyway I would like to install it,  but I can't figure out to restore my recordings.  If I had the mythconverg.sql file I could restore from this, but it doesn't exist.  How do I procede?

If you've got the recordings themselves, but no old database or backup to restore information from, you're still kind of OK.

After properly configuring your new Mythbuntu installation and its backend with a brand-new mythconverg so that your machine functions, records, etc., and once you are doing database backups, you can add your old recordings to this new mythconverg by using the script myth.rebuilddatabase.pl which is found in your /contrib directory,or online from here: 
[http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib/](http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib/)  

The instructions for using the script have to be squeezed out of the comments in the script itself, since it's not documented very well. It will go through every file in the designated directory and hunt for files that mythconverg doesn't know about. So it will have to be run once on each directory that may be included in your storage group.

For each hit it finds, the script will look for information in the current listings, and then will give you a series of dialogues to enter in the pertinent information for the recording file. (Name, episode name, length of episode, channel name, etc.) Then the script will offer to index and commflag the recording for you (which you'll need to have done). Then it will move on to the next hit it finds.

As you might expect, the dialogs and commflagging make the whole process kinda ... slow, depending on how many recordings it's readding. Plus, if you don't know what some of your recordings actually are, you may wish to preview the files in some player like xine, so that you have the information ready to go for the dialogues. Because while the script is happy to enter default information into the dialogues, once the information is in mythconverg, it becomes hard to edit.

Finally, mythcommflag has a hard time building indexes for dvb recordings. If you later find that you can't skip forward and backward in any of your restored dvb recordings, you will need to run mythtranscode --buildindex --mpeg2 on these recordings individually later.

Good luck.

---

