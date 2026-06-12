---
title: "Mass MP3 renamer"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by dmorlow on 2006-11-12
How do I rename a large amount of MP3s quickly?  I would like the program to use an Internet database and compare a few seconds of each MP3 to the internet database to rename it to the correct name and make all the names consistent.  The tags have seemed to disappeared from a lot of my MP3s, so a renamer based on tags will not work.  I have Ubuntu 6.06.

Thanks,

David

---

### Post by Matt Yun on 2006-11-13
[Audio Tag Tool]("http://pwp.netcabo.pt/paol/tagtool/")

---

### Post by Buffalo Soldier on 2006-11-13
> **Matt Yun said:**
> [Audio Tag Tool]("http://pwp.netcabo.pt/paol/tagtool/")My tool of choice too. But I don't see any recent development/update. Just hope it's not dying.

---

### Post by sethmahoney on 2006-11-13
> **Buffalo Soldier said:**
> My tool of choice too. But I don't see any recent development/update. Just hope it's not dying.

An other suggestions?  Audio tag tool totally borked my filenames and folders.

---

### Post by songo on 2006-11-13
[easy tag]("http://easytag.sourceforge.net/")

---

### Post by dmorlow on 2006-11-13
But all those renamers rely on the tag in the audio file, don't they?  The tags are missing from a lot of my MP3s.  I know some CD programs listen to a few seconds of the song and go on the internet to compare it with a database and then gives it the title and artist name.  I was hoping the same features would be built into an MP3 renamer.

---

### Post by sethmahoney on 2006-11-13
> **dmorlow said:**
> But all those renamers rely on the tag in the audio file, don't they?  The tags are missing from a lot of my MP3s.  I know some CD programs listen to a few seconds of the song and go on the internet to compare it with a database and then gives it the title and artist name.  I was hoping the same features would be built into an MP3 renamer.

It looks like easytag can do something like what you want, but after playing around with it a little, it doesn't seem too reliable - it seemed to want to label all my music as Blink 182 (and none of it is).

---

### Post by Sarisar on 2006-12-08
I used Easytag to rename around 10 gigs of music to /music/<artist>/<album>/<track number> - <song title>.mp3 from tags.

I then ripped off more CDs and it didn't write any tags, but did directories and filenames correctly so I used Easytag again to fill in the tags from the filenames:

Sorting by tag:
[LIST=1]
[*]Load up Easytag
[*]Pick the directory you wish to change MP3s in on left hand pane
[*]Click on the right hand pane somewhere to select all music files
[*]Press **Ctrl**+**A** to select all files
[*]From the toolbar click the green icon (Tool tip is Scan Files)
[*]Select the "**Rename File and Directory**" scanner option
[*]In the "Rename File and Directory" text box, type in "**~/music/%a/%b/%n - %t**" (or wherever you want to output the files)
[*]Click the green icon in the window to scan files
[*]Click the exit icon to close window down
[*]Click on the right hand pane somewhere to select amended music files (they should all be in red meaning they have changed and need to be saved)
[*]Press **Ctrl**+**A** to select all files
[*]Press **Ctrl**+**S** to save all files
[*]Wait a while depending on how many files you've done.
[*]Send me 10 bucks as a thank you :)
[/LIST]
(the last one is optional)

Filling tag by filename:
[LIST=1]
[*]Load up Easytag
[*]Pick the directory you wish to change MP3s in on left hand pane
[*]Click on the right hand pane somewhere to select all music files
[*]Press **Ctrl**+**A** to select all files
[*]From the toolbar click the green icon (Tool tip is Scan Files)
[*]Select the "**Fill Tag**" scanner option
[*]In the "Fill Tag" text box, type in "**~/music/%a/%b/%n - %t**" (or wherever your files are).  It tells you what it thinks it's found underneath so you can check
[*]Click the green icon in the window to scan files
[*]Click the exit icon to close window down
[*]Click on the right hand pane somewhere to select amended music files (they should all be in red meaning they have changed and need to be saved)
[*]Press **Ctrl**+**A** to select all files
[*]Press **Ctrl**+**S** to save all files
[*]Wait a while depending on how many files you've done.
[*]Send me 10 bucks as a thank you :)
[/LIST]
(the last one is optional again)

Enjoy :)

---

### Post by Matt Yun on 2006-12-18
> **dmorlow said:**
> How do I rename a large amount of MP3s quickly?  I would like the program to use an Internet database and compare a few seconds of each MP3 to the internet database to rename it to the correct name and make all the names consistent.  The tags have seemed to disappeared from a lot of my MP3s, so a renamer based on tags will not work.  I have Ubuntu 6.06.

Thanks,

David

I've been recently trying to organize my collection, and I've been dissatisfied with EasyTag etc.  I came across a KDE application called [JuK]("http://kde-apps.org/content/show.php?content=10575"), that seems to do everything the parent poster wanted.

JuK has [MusicBrainz]("http://www.musicbrainz.org") integration.  MusicBrainz is an opensource audio cd identification database, unlike the closed cddb, and apparently has [audio fingerprinting technology.]("http://blog.musicbrainz.org/archives/2006/03/new_fingerprint.html")

I just installed it (apt-get install juk) and will give this a spin.

---

### Post by arsenic23 on 2007-01-12
Musicbrainz has it's own stand alone tagger, Picard.

Find out more here>>> [http://wiki.musicbrainz.org/PicardLinuxInstall#head-5f60c040c32c67c304b335181b88678ad34149c2](http://wiki.musicbrainz.org/PicardLinuxInstall#head-5f60c040c32c67c304b335181b88678ad34149c2)

---

### Post by akba0012 on 2007-09-27
> **Sarisar said:**
> I used Easytag to rename around 10 gigs of music to /music/<artist>/<album>/<track number> - <song title>.mp3 from tags.

I then ripped off more CDs and it didn't write any tags, but did directories and filenames correctly so I used Easytag again to fill in the tags from the filenames:

Sorting by tag:
[LIST=1]
[*]Load up Easytag
[*]Pick the directory you wish to change MP3s in on left hand pane
[*]Click on the right hand pane somewhere to select all music files
[*]Press **Ctrl**+**A** to select all files
[*]From the toolbar click the green icon (Tool tip is Scan Files)
[*]Select the "**Rename File and Directory**" scanner option
[*]In the "Rename File and Directory" text box, type in "**~/music/%a/%b/%n - %t**" (or wherever you want to output the files)
[*]Click the green icon in the window to scan files
[*]Click the exit icon to close window down
[*]Click on the right hand pane somewhere to select amended music files (they should all be in red meaning they have changed and need to be saved)
[*]Press **Ctrl**+**A** to select all files
[*]Press **Ctrl**+**S** to save all files
[*]Wait a while depending on how many files you've done.
[*]Send me 10 bucks as a thank you :)
[/LIST]
(the last one is optional)

Filling tag by filename:
[LIST=1]
[*]Load up Easytag
[*]Pick the directory you wish to change MP3s in on left hand pane
[*]Click on the right hand pane somewhere to select all music files
[*]Press **Ctrl**+**A** to select all files
[*]From the toolbar click the green icon (Tool tip is Scan Files)
[*]Select the "**Fill Tag**" scanner option
[*]In the "Fill Tag" text box, type in "**~/music/%a/%b/%n - %t**" (or wherever your files are).  It tells you what it thinks it's found underneath so you can check
[*]Click the green icon in the window to scan files
[*]Click the exit icon to close window down
[*]Click on the right hand pane somewhere to select amended music files (they should all be in red meaning they have changed and need to be saved)
[*]Press **Ctrl**+**A** to select all files
[*]Press **Ctrl**+**S** to save all files
[*]Wait a while depending on how many files you've done.
[*]Send me 10 bucks as a thank you :)
[/LIST]
(the last one is optional again)

Enjoy :)

Dude thank you so much! I have done this over and over again, but i just didn't know you had to press CTRL-S to actually save it, that is like sooo MS Word. But whatever it works! Thanks!

---

