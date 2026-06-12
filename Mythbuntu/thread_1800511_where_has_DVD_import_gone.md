---
title: "where has DVD import gone"
date: 2011-07-09
forum: Mythbuntu
---

### Post by chipppy on 2011-07-09
Good evening

I feel silly asking but where has DVD import gone in 11.04???

fresh 11.04 install have added in all the extra stuff (ticked all the boxes) and went to import (rip) DVD and it not in the optical disc menu.
There is import CD but no import DVD.

Am i missing something really simple or has it been remove from the application??

Cheers
chipppy

---

### Post by klc5555 on 2011-07-09
Mtd and the myth dvd ripper have been tossed overboard in 0.24. Too difficult to get working with storage groups it would appear: [http://www.mythtv.org/wiki/Mtd](http://www.mythtv.org/wiki/Mtd)

Handbrake and vobcopy are among the recommended (if much less convenient) substitutes. Makes you glad you upgraded...

---

### Post by chipppy on 2011-07-11
nope think i might regress

---

### Post by itlarson on 2011-07-17
Vobcopy is outdated, use dvdbackup instead.  Use "dvdbackup -i /dev/dvd -o ~/my_recordings -M" to mirror the entire DVD onto your hard-drive.  There's no reason to transcode when you can get a 2tb drive for $80, unless you are planning to watch the movie on your phone or something. 

 Note that you need to set the path to ~/my_recordings in the front-end settings, not the storage groups.  Dvdbackup just copies the directory structure of the disk into a newly created directory on your hard drive.  If you set the path in the front-end, mythtv will recognise this DVD directory as being a DVD. It will show up under recordings as a single item, and play from there just as you were playing the actual disk.  If you set the path in storage groups instead, mythtv just sees the directory as a collection of files, and each .vob will show up under recordings.  At least that's the case under 10.4, which I use.  

You will need to manually scan for the newly ripped DVD to show up in "videos".  You can do this by entering "m" on your keyboard while in "videos" and selecting "scan for changes".   You probably can also get this menu on most remotes.

VLC can play the DVD directories properly, although mplayer cannot.  If you need to transcode after all, handbrake is fine with the data being on your hard-drive instead of an optical disk.  K3B can burn a disk identical to the original from this data, although it is the only burner I have found which can do so.   

Be sure to test play the DVD directory.  Skip through it all the way to the end.  I've found there are some disks that aren't playable on Linux by any method, so it's good to keep a dedicated DVD player around.  

I have often wondered if there is a way to add the dvdbackup command to the mythtv menus, so I wouldn't have to switch to a terminal.  Does anyone have any thoughts on this?

---

