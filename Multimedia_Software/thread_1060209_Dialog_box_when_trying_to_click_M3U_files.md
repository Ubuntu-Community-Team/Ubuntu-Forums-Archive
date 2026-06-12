---
title: "Dialog box when trying to click M3U files"
date: 2009-02-04
forum: Multimedia Software
---

### Post by dimanche on 2009-02-04
Hi.

I am having the same problem as discussed in this thread.

> [http://ubuntuforums.org/showthread.php?t=190462](http://ubuntuforums.org/showthread.php?t=190462)

All of my music is stored on a septate hard drive in ntfs format. I am unable to double click an .m3u file and have it open in Rhythmbox. It always asks" Do you want to run "play-list-name.m3u", or display its contents?" I have the option to Run in terminal, Display, Cancel, Run. Clicking Run does nothing.

Is it possible to change this so I can double click an .m3u file and have it open in my preferred application?

---

### Post by mc4man on 2009-02-04
Use that other thread as a guide to setting the file association, but what your going to need to also do is remove the execute flag on your .m3u's or on all your music files if you wish. 
If it's on another drive, or partition that's owned by root then one way to do that is to run gksudo nautilus, browse to your partition and r. click -> properties -> permissions on the folder(s) inside.

Clear the execute box, click on 'Apply permissions to enclosed files'.(works on all files inside, even if in subdirectories. 

The execute box will refill orange with a - , doesn't matter, all the files inside will have had the execute removed.

---

### Post by dimanche on 2009-02-05
hmmm.

Ok, I run gksudo nautilus. The file browser opens and I go to the partition with the mp3 albums, right click the folder and go to permissions. When I go to change - on the execute option it changes back in the blink of an eye by itself. Even if I go to change the owner or access it just changes back by itself.


It wont let me change it :(

any ideas?

---

### Post by mc4man on 2009-02-05
If you do the change on the folder then (from previous post
> The execute box will refill orange with a - , doesn't matter,

but you need to click on the 
> 'Apply permissions to enclosed files'.

Then open the folder and ck. the permissions on individual files, the execute should have been removed.

Otherwise just go in and do each .m3u individually (though doing the folder should work.

For instance on another drive I have a "Music" partition, inside are 2 folders, each ATM has 15 or so sub folders inside.
Simply removing the execute on the 2 main folders removes it for all the files inside, tracks and the .m3u's

---

