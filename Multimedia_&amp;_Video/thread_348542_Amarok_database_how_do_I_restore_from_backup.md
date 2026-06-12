---
title: "Amarok database: how do I restore from backup?"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by catfishy on 2007-01-28
Hi there!  Here is my problem, if anyone can help:

Amarok is the best-ever music program for any OS in my opinion.  So I've been using it for a year.  I have a 500 gb external hdd, so sometimes I would, by mistake, start up amarok before I plugged in the drive, and BAM!, amarok wouldn't obviously see the music, create a new database and I'd be frustrated.  It never refused to restore the whole database when I would quickly quit and started up Amarok again (this time with the usb drive plugged in!).  So, a month ago I got the amarok script to backup mysqlite databases (DatabaseScripts (v0.2)!  I backupped the database into a nice .db file.  Great!  So, today I was re-tagging annoying genres in amarok and it crashed, or rather it got hung up so bad that I had to restart.  Upon starting up Amarok again, it re-built the collection (which had happened before, but I had never lost my **statistics!**)  So now, it's as if I have a fresh new Amarok but I want to restore the database from a month ago; assuming that it has statistical info (number of plays, etc).  My questions are:

Does the .db created by the script have stats like number of plays or does it only have the song titles/artists etc?

How do I restore the .db for amarok?  Where is the database stored?
and
Will restoring a database from a month ago, mess up amarok or the OS in any way?

People talk about restoring a database but not *how*, in this thread:
[http://ubuntuforums.org/showthread.php?t=249144&highlight=restore+amarok+database](http://ubuntuforums.org/showthread.php?t=249144&highlight=restore+amarok+database)


I'm willing to try anything.  I really really want those stats back!  Thank you so much for any help you can give!
catfish  :D

---

### Post by catfishy on 2007-01-28
Yay!  It seems that all I had to do to replace the db was REPLACE it!  The .db backup i made a month ago was in my home folder.  The command to replace it was:

```
sudo mv /home/sea-cow/collection.db ~/.kde/share/apps/amarok/collection.db
```

Also, though, it may be beneficial to first look in ~/.kde/share/apps/amarok/collection.db because in there are many many .db backups apparently.  Older ones.  It may be possible to just go into that folder and rename an older db, one that is better than your now-blank db.  Mine was mysqlite.  I lost two months of music-listening-stats, but that is better than starting over, and the collection updates completely within a few minutes!  I hope that helps someone, it's annoying to lose that much information, i'll be backing up all the time now!
Thanks for listening.
catfish

Amarok, I love you.

---

### Post by catfishy on 2007-03-14
Okay, one last thing!  When migrating or backing up or whatever, you should probably copy the whole amarok folder:  I only backedup the database because it was working fine, but now, in feisty from scratch, I find that I didn't copy **collection_scan.files** from the folder and it keeps trying to rebuild my collection (but not in a good way, it keeps downgrading the database).  So I have to find a little prog that'll simply list all the files scanned.  Just now, I unticked the "watch folders for changes" option and quickly quit amarok.  Upon restart, amarok didn't try to update and I can listen to all that music!  We'll see about that....

edit: rather than painstakingly formating a giant list of my music, I've decided to let amarok add genre by genre to the database/collection.scan.files, and then, when it's done (tomorrow sometime!), I'll backup the collection.scan and also replace the db with my old one....

---

### Post by catfishy on 2007-03-15
Okay, I lied, I couldn't help asking for help on one thing:  So, does anyone know how to get a directory listing of just mp3s for my amarok file named "collection_scan.db"?
Here is the format:

/media/BICYCLE/MEDIA/music_uncategorizable and experimental/Hawk And A Handsaw - Hawk And A Handsaw (2003)/03 Hawk And A Handsaw - Romceasca.mp3

It needs to be one long line with nothing but the path and the mp3 at the end (ie no directory names or attributes or anything).  I've tried all sorts of commands in terminal but I can't figure it out!  If I need my root to be /media how do I configure terminal to list it?  Or is there an appropriate program?  I just wasted over two hours trying to simply list the files using a windows program that ultimately died under the stress of formating backslashes to forwardslashes!!!  Any help would be wonderful!  Thanks!


Amarok refuses to build the file itself, it gets too worked up and flustered.

Edit:  How I got a list with full paths for your music collection (but you should read the slocate man to make sure it's for you):
sudo slocate -U /media/BICYCLE/MEDIA/ -o ~/database -v                     (so that made the little 2mb database and put it in my home)
updatedb             (i don't know if that's necessary)
slocate --database=/home/sea-cow/database .mp3 > /home/sea-cow/Desktop/mp3s

Now I have a 7 mb text file named 'mp3s' that I need to whittle away at to be just the mp3s in my amarok database....
hmmmm.....
FUN!

Edit:  Not fun.  And it didn't work to make my own "collection_scan.files"  Aw well....

Could someone please end this soliloquy with some advice as to how to build a database on a machine that tries to write (i think) collection.db-journal but doesn't actually update the database and just hangs there....

Ended up learning that I need to backup the whole amarok folder (and amarokrc) if I migrate/upgrade to a new system.  Ended up losing all my stats, but that's okay because I made playlists that'll work, and stats are what last.fm are for anyhow!  FUN!

---

