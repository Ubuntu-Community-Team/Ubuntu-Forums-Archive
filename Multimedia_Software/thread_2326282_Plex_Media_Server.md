---
title: "Plex Media Server"
date: 2016-05-30
forum: Multimedia Software
---

### Post by Andrew_Hays on 2016-05-30
I have moved my usb external hard drives from my windows box to my ubuntu box, set up plex media server, have it all loaded and working, added my libraries, waited for them to scan down, now every movie or tv episode i try to watch i get a "sorry there was a problem playing this file" or if i try to look at the movie/tvshow info, i get a "media not found" error.

the libraries are visible and all the meta data seems to be downloaded (covers for movies and tv shows are show up on screen).

i thought it might have been a permissions thing but i have been playing with that and having no success   even with a chmod 777.

the drives are still ntfs, is that my problem?   or anyone else got any ideas?

many thanks


EDIT: i seem to beable to get around the issue with a fresh restart fo hte plexmediacenter service... but it doesn't work with 100% of my content and if i leave the service go idle for too long i cant play anything again...   so i'm guessing that means its nothing to do with the partition type...   

still open to suggestions to try.

thanks

---

### Post by TheFu on 2016-05-30
Welcome to the forums.

Yes. NTFS is the most likely issue.  There are many ways to fix it 
1) mount options which make the media files readable by the plex userid.  No GUI for this that I know.
or
2) setup Windows-to-Linux userid mapping files on the NTFS partition, then chmod will work.
or
3) convert the file system to a Linux compatible file system that supports chmod natively - ext4 is probably best.  You'll need to use the backups for this, since there isn't any "in-place conversion" possible, at least not that I'm aware and that works 100%.

I've been using Plex and XBMC for years. Never ran into any permissions issues that weren't trivially solved, but all my media is on ext4 file systems.

---

### Post by Andrew_Hays on 2016-05-31
> **TheFu said:**
> Welcome to the forums.

Yes. NTFS is the most likely issue.  There are many ways to fix it 
1) mount options which make the media files readable by the plex userid.  No GUI for this that I know.
or
2) setup Windows-to-Linux userid mapping files on the NTFS partition, then chmod will work.
or
3) convert the file system to a Linux compatible file system that supports chmod natively - ext4 is probably best.  You'll need to use the backups for this, since there isn't any "in-place conversion" possible, at least not that I'm aware and that works 100%.

I've been using Plex and XBMC for years. Never ran into any permissions issues that weren't trivially solved, but all my media is on ext4 file systems.


1) i'm ruining a headless ubuntu 16.04 server distro anyways so no gui is not an issue...   it the some sort of guide to explain how to do this?

2)i'm also interested in a guide to try this

3) this option i really want to avoid as the drives are too full to convert them to another file system with out buying another hard drive to have enough spare space to do it. they are 2 4tb and a 3 tb drive.    I also like that idea that if i can get ntfs to run stable in nix for my needs, it give me the option to easily plug them back into a windows box for what ever reason.


thanks

EDIT: another thought...  could smbd be clashing?... that same drives are shared so i can access them from my windows box to add new content.

---

### Post by TheFu on 2016-05-31
[http://ubuntuforums.org/showthread.php?t=2285434](http://ubuntuforums.org/showthread.php?t=2285434) has some info and links.

Not having a backup is a bad idea. You'll learn about this the hard way, just like I did. Oh, well. 

NTFS will always be a poor choice (hack) under Unix.

---

### Post by ajgreeny on 2016-05-31
Make sure you are added to group plex and that user plex is added to your username group; that may also help if you use ext4 formatted drives, though I don't think it makes any difference with ntfs drives as they do not accept or enable Linux permissions.

---

### Post by TheFu on 2016-05-31
2) [http://www.tuxera.com/community/ntfs-3g-advanced/user-mapping/](http://www.tuxera.com/community/ntfs-3g-advanced/user-mapping/) describes the Windows to Unix userid mapping techniques. Non-trivial, IMHO and not worth the effort in a home environment.

---

### Post by Andrew_Hays on 2016-06-01
after my last post i found some stuff about uuid's when mounting ntfs drivers.   2 of my drives have the same uuid for some reason and its one of those drives that are refusing to work at all.     i'm assuming this is once of the causes of my problems...   haven't as of yet managed to find a solution to this but i havent had much time today too look

---

### Post by TheFu on 2016-06-01
You have 2 choices.
a) don´t use uuid for the mount command - this is how we mounted storage for 20+ yrs, but sometimes the device changes at boot. That´s why UUIDs became the default method around 2006.
b) force one of the disks to get a new uuid - I don´t know the exact command. Shouldn´t be hard to find. Then use the new UUID to mount it.  The only way I´ve heard of UUIDs being identical is if someone cloned the same brand, size, model, disks.  We´re talking cloning the entire device, not just a partition.  [http://manpages.ubuntu.com/manpages/xenial/man1/uuidgen.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/uuidgen.1.html) is the command.

---

### Post by Andrew_Hays on 2016-06-01
[COLOR=#C61919][FONT=Ubuntubeta]**ajgreeny: **[/FONT][/COLOR]can confirm i have already checked that. found a stack exchange page suggesting that might fix my issue. but it hasn't.


[COLOR=#000000][FONT=Ubuntubeta]**TheFu:  **[/FONT][/COLOR]it doesn't make sense to me why they would have the same uuid. they aren't a clone. they are identical model usb drives i bought at the same time.  but anyways i have fixed the uuid issue using a hex editor and just gave it a new one.

i was mounting from /dev/sdXX anyway. but i thought i'd address it still.

referring to the ownership stuff according to [COLOR=#333333][FONT=monospace]ntfs-3g.usermap[/FONT][/COLOR] none of the directories on any of the drives are owned buy anyone.   do i need to make it so my user owns them or the plex user owns them.  i'm assuming my user is the best option as the plex user and my user are all in the same groups.

---

### Post by Andrew_Hays on 2016-06-04
seems i have come across a solution that so far has worked beautifully, my drives no longer seem to time out and become inaccessible to plex

i set my auto-mounting of my usb drives like this

UUID="201E39B91E398934" /media/media ntfs-3g rw,auto,user,fmask=0111,dmask=0000 0 0
UUID="13BC0ACAEB0ACAA2" /media/movies ntfs-3g rw,auto,user,fmask=0111,dmask=0000 0 0
UUID="A2CA0AEBCA0ABC13" /media/tvshows ntfs-3g rw,auto,user,fmask=0111,dmask=0000 0 0

---

