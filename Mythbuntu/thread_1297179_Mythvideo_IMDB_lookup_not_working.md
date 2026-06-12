---
title: "Mythvideo IMDB lookup not working"
date: 2009-10-21
forum: Mythbuntu
---

### Post by dfinn on 2009-10-21
This is a pretty much vanilla Mythbuntu 9.04 install.  I've uploaded videos to /var/lib/mythtv/videos and they show up when I have mythweb scan my video collection.  I can watch them fine from within myth.  I'd like to get IMDB movie lookups working so that I have info for the movies.  

I'm going to imbdb.org, getting the move id # (minus the tt in front) and then putting this into the IMDB section when I edit the video data from whithin mythweb.  According to the wiki this should cause the imdb perl script to go and grab the data but it's not happening.

Am I doing something wrong?

---

### Post by klc5555 on 2009-10-21
> **dfinn said:**
> This is a pretty much vanilla Mythbuntu 9.04 install.  I've uploaded videos to /var/lib/mythtv/videos and they show up when I have mythweb scan my video collection.  I can watch them fine from within myth.  I'd like to get IMDB movie lookups working so that I have info for the movies.  

I'm going to imbdb.org, getting the move id # (minus the tt in front) and then putting this into the IMDB section when I edit the video data from whithin mythweb.  According to the wiki this should cause the imdb perl script to go and grab the data but it's not happening.

Am I doing something wrong?

I found in my installation that I have to actually open Settings/Utilities -> Video Manager in the front end, and then it goes out and gets the IMDB information based on the IMDB numbers I had edited in earlier via MythWeb. Perhaps the same is true for you.

---

### Post by dfinn on 2009-10-21
> **klc5555 said:**
> I found in my installation that I have to actually open Settings/Utilities -> Video Manager in the front end, and then it goes out and gets the IMDB information based on the IMDB numbers I had edited in earlier via MythWeb. Perhaps the same is true for you.

I tried that and it didn't seem to do anything.  I get an IMDB window that is in the foreground for each video but when I hit the number keys on my remote to type in the movie ID nothing happens.

---

### Post by fenian on 2009-10-21
You can  use the Fill mythvideo metadata.pl script to automatically grab the info from IMDB.Right click on [this link]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl") and choose save link as... option.Next go to the file and right click on it choose properties click the permissions tab and check the Allow executing file as program box.Click close.Double click the file choose run in terminal,it should open a terminal and grab metadata for your videos.

---

### Post by klc5555 on 2009-10-22
> **dfinn said:**
> I tried that and it didn't seem to do anything.  I get an IMDB window that is in the foreground for each video but when I hit the number keys on my remote to type in the movie ID nothing happens.

There is a known bug in the way the video-ui.xml files were set up for each of the themes in 9.04 that produce that uneditable IMDB box that won't go away.

To fix (basically changing one character), see the thread [http://ohioloco.ubuntuforums.org/showthread.php?t=1167783&highlight=imdb](http://ohioloco.ubuntuforums.org/showthread.php?t=1167783&highlight=imdb)

---

### Post by miststlkr on 2009-10-31
> **fenian said:**
> You can  use the Fill mythvideo metadata.pl script to automatically grab the info from IMDB.Right click on [this link]("http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl") and choose save link as... option.Next go to the file and right click on it choose properties click the permissions tab and check the Allow executing file as program box.Click close.Double click the file choose run in terminal,it should open a terminal and grab metadata for your videos.


When I ran that script the TV shows kind-of-worked but none of the movies worked.  Each TV show is set up in a directory with the show name with subdirectories by season [[ie// /movies/mythbusters/season 1/...]] and each season folder has an image, presumably from the dvd boxed set, but individual files are still the default squres, just like the movies. 

 I had previously run the following to get rid of the IMDB screen when I go to movie manager, it that makes a difference:

```

find /usr/share/mythtv/themes/ -name "video-ui.xml" -print | xargs sudo sed -i 's/enterimdb/entertmdb/g'

```

Also, files are not in the default location.  The mythtv settings have the correct location and they show up in the gallery fine, but as black boxen instead of posters.  I have some error messages from the above "fill" script that I will got through when I get time this week, but if this is a known issue with an easy fix by all means please let me know.


Thanks for your time!

---

### Post by miststlkr on 2009-11-03
Going through the output from the script, I keep getting "Incorrect file format 'videometadata' " at various line locations among other errors:
[INDENT]           [SIZE=3]DBD::mysql::st execute failed: Incorrect file format 'videometadata' at ./fill_mythvideo_metadata.pl line 1977.
DBD::mysql::st bind_columns failed: Statement has no result columns to bind (perhaps you need to successfully call execute first) at ./fill_mythvideo_metadata.pl line 1980.
DBD::mysql::st fetch failed: fetch() without execute() at ./fill_mythvideo_metadata.pl line 1982.
Video file 'Hackers.avi' does not exist in the DB metadata. Inserting dummy row...
DBD::mysql::st execute failed: Incorrect file format 'videometadata' at ./fill_mythvideo_metadata.pl line 1988.

[/SIZE][/INDENT]Also, the mythbuntu pastebin has several instances of the same error, incorrect file format 'videometadata'.  To me it would look like the database never got set up correctly in the first place. I let the installer do what it wanted rather than messing with it as this was my first attempt at installing; maybe I missed something.


I am going to try a fresh install using Karmic later this week, but if someone can give me an idea why this happened in the first place, I'd appreciate it.  

Cheers-

---

