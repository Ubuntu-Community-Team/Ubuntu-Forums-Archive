---
title: "[SOLVED] Mythmusic borked after ripping several cd's"
date: 2007-12-31
forum: Mythbuntu
---

### Post by volkswagner on 2007-12-31
Mythmusic was working fine.  I could browse music previously ripped a couple of days ago.  Yesterday I ripped about twenty albums.  One CD gave me problems at about 75% locked up machine.  Had to reset.

Now I cannot access music via Mythmusic.  It shows only active play queue.  When entering "Play music" the "scan for new music" seems to cut way short at about 10% of progress then goes straight to update database.  Could I have added too many CD's in a row.  I did see successive database updates after a new cd was imported.

Is there a command to force mythmusic to scan for new music?

When ripping I used myth frontend ripper.  I also manually edited the GENRE field to taste.  Do I need to add these new fields to mysql manually?

I browsed the new folders and the owner permissions.  The owner is listed as my user login, and mythtv is group read only.  I can play files directly although vlc seems to be the default player when browsing via thunar.

---

### Post by laga on 2008-01-01
Hi,

it's possible that your database got broken when you reset your computer. 

If you run mythbuntu-control-centre -> advanced management -> optimize tables, it might just work again ;). If it's still broken, I'd suggest you check the log files in /var/log/mysql/

---

### Post by volkswagner on 2008-01-01
Thanks for the reply.  I enabled the myql optimize tables.  No change.

I checked logs, nothing in mysql.log, nor mysql.err

Found this in mythfrontend.log
```

SELECT artist_id FROM music_artists WHERE artist_name = 'London Symphony Orchestra' ;
Driver error was [2/145]:
QMYSQL3: Unable to execute query
Database error was:
Table './mythconverg/music_artists' is marked as crashed and should be repaired

metadata.o: You don't seem to have any tracks. That's ok with me if it's ok with you.
2008-01-01 18:53:59.140 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/music-ui.xml
playlist.o: Taking a 0 (zero) off a playlist
            If this happens on repeated invocations of mythmusic, then something is really wrong
```

I do have in ripper setting replace empty space with underscore.


I relocated all but one folder within music folder.  I happened to leave the classical folder which included the above mentioned London Symphony.  After reading the log I removed classical and replaced with Blues containing only one artist/album.  Still no change.  It seems to me the scan for music is broken.  Can I remove the mythmusic plugin and reinstall?  Any ideas on log contents?

---

### Post by volkswagner on 2008-01-02
I uninstalled mythmusic and reintalled, still no joy.

---

### Post by volkswagner on 2008-01-02
Well I found this via Google

```
mysqlcheck --auto-repair -A -u mythtv -pmysqlpass
```

This repaired the three DB sections, artist, album, song

I also discovered I left off the trailing / for music directory.

I can now access all music,  new problem I can't navigate.  When play music is selected the first song is automatically played and navigation is limited to play buttons.  I have changed the settings for how to sort music, "directory, genre artist splitartist album title, various combinations.  These changes don't seem to do anything.  I have run mythfill database and restart machine still can't navigate music directory.  I think the major cause was due to special characters in ripped music.  I have sorted through and changed entries using sudo thunar but still no joy.  I think I should not have removed and reinstalled mythmusic plugin.

When I change play mode in playback settings it does not take,  when I go back into playback settings it always says None.

---

### Post by Vincent_Lin on 2008-01-02
Hi,
I also use mythmusic to play mp3 etc stuff, mostly for my kids music collections, as they like to dance in the living-room in front of the TV set.  They are 2 and 4 years old girls!  I also experience the problem in playing music as you described.  

I found this screen-shot from mythtv .org and it shows exactly what I want the interface to be like - sorted by album, and you can go into each album and play each piece of music at will.

[http://mythtv.org/mythimages/newmusic2.jpg](http://mythtv.org/mythimages/newmusic2.jpg)

The problem is, I do not know how I can configure mythtv setup to get mythmusic look like this.

Any help?

Vincent Lin

---

### Post by volkswagner on 2008-01-02
Vincent,

Are you able to navigate music within the play screen at all?  How do you navigate?  Do you choose "select music"?  Did you check the box "show entire music tree", in setup>music player settings?  What does the field "tree sorting" have in it?  This is also found in setup>media settings>music settings>general.

[http://www.mythtv.org/wiki/index.php/MythMusic]("http://www.mythtv.org/wiki/index.php/MythMusic")

---

### Post by volkswagner on 2008-01-02
Well I figured out the problem.  In music player settings check box for "use keyboard/remote acclerated buttons"  must be selected.  If not the navigation keys are used play, pause, ff, rew., etc.

This is the confusion one gets when randomly changes stuff to fix stuff and not keeping track of STUFF!

---

