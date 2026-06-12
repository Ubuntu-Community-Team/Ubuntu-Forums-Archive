---
title: "Moving all MythTV info to a new OS"
date: 2009-04-18
forum: Mythbuntu
---

### Post by Weidbrewer on 2009-04-18
Hi, all.   I'm trying to migrate my system over to Ubuntu 64, and have hit a stag migrating Mythtv - I can't get the database to move over.  As I have over a thousand individual video files, I *really* don't want to have to do all the metadata over again by hand.  It would be enough of a pain that I'd scrap this migration all together if I had to do that.

I have tried backing the DB up with MySQL Administrator with no luck.  I have also tried the dump and restore commands found here:  [http://www.mythtv.org/wiki/Backup_your_database]("http://www.mythtv.org/wiki/Backup_your_database"), also with no luck.   I even tried opening both DBs as text files and manually C&Ping over.  Nothing.

Is there a way to get all the posters, metadata, etc from one partition to the other?

Two additional notes:

[LIST=1]
[*]The files play just fine in Myth right now, so we're good there.
[*]For reasons unknown, I named the DB "mythtv" rather than "mythconverg" originally, but I am sticking with "mythconverg" on this installation.
[/LIST]

---

### Post by barney_1 on 2009-04-18
I just did this myself and it worked. I hope you have the same outcome that I did.

First off, I like to use phpmyadmin... makes things a bit easier.  Either way, I would try the following:

(important tables = record recorded oldrecorded recordedprogram recordedrating recordedmarkup recordedseek)

1. Create a new database (named anything ie: tempDatabase).
2. Import your mythconverg (or you said yours is named mythtv?) database backup into the database you just created.
3. From this temporary database export each of the important tables individually.
4. Go to your new mythconverg database. Drop each of the important tables and import the table exports you made in step 3.

---

### Post by Weidbrewer on 2009-04-18
Thanks for the quick response.

I just installed phpMyAdmin from the repos, but can't seem to get it to run.  I'm not sure that I'm going to be able to learn a whole new program today, especially if I can't even figure out how to get it to run. :P (Website says that there is a web interface only, and I'm not finding it.)


Also, just to make sure we're on the same page - you said below that the recording tables are the most important.  Just in case phpMyAdmin for some reason only deals with those, let me clarify:  my videos are the files that I'm interested in.  I pretty much never use Myth to record anything.  I use it as a media library.

---

### Post by barney_1 on 2009-04-18
The tables that I listed store all of the meta information for recordings in mythtv.  This means that those tables are what stores and links title and description data to the actual video files.  These tables also store data about what programs are scheduled to record, have already recorded, etc. (sounds like this part you don't need).

phpMyAdmin is basically a web-based frontend for mySql.  I think it makes the grunt work of mySql a lot easier.  That being said, everything it can do, you can also do for the mySql prompt.

So anyway, you must have the video files backed up.  In order to access them (and their metadata) with mythtv you need to restore the tables to your new mythconverg.

---

### Post by Weidbrewer on 2009-04-18
> **barney_1 said:**
> The tables that I listed store all of the meta information for recordings in mythtv.  This means that those tables are what stores and links title and description data to the actual video files.  These tables also store data about what programs are scheduled to record, have already recorded, etc. (sounds like this part you don't need).

As I suspected, we are talking about two different things...like I said, I don't record anything with this box at all.  I'm referring to my video files, not recordings - old VHSes that I put on a harddrive, movies, TV downloads, etc.  (You're right, I don't need that part.  Yeah, I can't do anything the easy way, can I? :) )  

> phpMyAdmin is basically a web-based frontend for mySql.  I think it makes the grunt work of mySql a lot easier.  That being said, everything it can do, you can also do for the mySql prompt.

My issue here is, I have no idea how to access it now that it is installed.  There's no link in the applications menu, no supplied web address or something to go to, etc.  For example, for mythweb administration, I go to [http://localhost/mythweb/status...I](http://localhost/mythweb/status...I) don't know where to go for phpmyadmin.  Make sense?

---

### Post by tgm4883 on 2009-04-18
> **Weidbrewer said:**
> As I suspected, we are talking about two different things...like I said, I don't record anything with this box at all.  I'm referring to my video files, not recordings - old VHSes that I put on a harddrive, movies, TV downloads, etc.  (You're right, I don't need that part.  Yeah, I can't do anything the easy way, can I? :) )  



My issue here is, I have no idea how to access it now that it is installed.  There's no link in the applications menu, no supplied web address or something to go to, etc.  For example, for mythweb administration, I go to [http://localhost/mythweb/status...I](http://localhost/mythweb/status...I) don't know where to go for phpmyadmin.  Make sense?

You should be able to backup your whole db from there.  The web address you are looking for is [http://backendip/phpmyadmin](http://backendip/phpmyadmin)

IIRC, You will need to use the mysql root user and password to login correctly.  Once in there, backup your whole db (if you want just the mythvideo tables, I believe they are there under videometadata)

---

### Post by Weidbrewer on 2009-04-18
Awesome.   Although that address itself didn't work, changing it to [http://**localhost](http://**localhost)**/phpmyadmin did.  I'll play around with that a bit tonight.   Thanks for the pointers, everyone.   I'll post back if (when) I screw something up.

---

### Post by nickrout on 2009-04-18
the best scripts are here:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

Note, the videometadata table is the key one but you really should bring in the whole database.

The covers etc are not stored in the database, the filename of the cover image is. You will need to transfer those individual picture files over too.

Are you upgrading myth versions too? That can bring hassles if the database schema has changed.

---

### Post by Weidbrewer on 2009-04-18
> **nickrout said:**
> 
Are you upgrading myth versions too? That can bring hassles if the database schema has changed.

Well...I'm going from Ubuntu 8.10 to Ubuntu 8.10 64.  That should keep the same schema, I believe.

Thanks for the pointers.  I'll give it a go tomorrow.  (When the Pens aren't playing.  :) )

---

### Post by Weidbrewer on 2009-07-12
> **barney_1 said:**
> I just did this myself and it worked. I hope you have the same outcome that I did.

First off, I like to use phpmyadmin... makes things a bit easier.  Either way, I would try the following:

(important tables = record recorded oldrecorded recordedprogram recordedrating recordedmarkup recordedseek)

1. Create a new database (named anything ie: tempDatabase).
2. Import your mythconverg (or you said yours is named mythtv?) database backup into the database you just created.
3. From this temporary database export each of the important tables individually.
4. Go to your new mythconverg database. Drop each of the important tables and import the table exports you made in step 3.

OK, well...stuff happened and I got taken away from this project for a long time.  I can only hope you might still be monitoring this...

I tried following your instructions above, but I'm having no luck.  

Step 1:  I created "tempattempt" and tried to import "mythtv.sql" and I get the message, "ERROR: No data was received to import. Either no file name was submitted, or the file size exceeded the maximum size permitted by your PHP configuration. See FAQ 1.16."  (since I couldn't find the FAQs, I couldn't get details.)  Also, when I import, it is asking for a *text* file...so I made a copy and an changed it over to a txt.  Same deal.  Now, this data base is fairly large, so maybe that's it...

For giggles, I brought up the Mythtv DB in this app and exported it from there to a new file, in case there were issues...same results as above.

Are there any options from any of the drop downs on any of the screens that I should be selecting along the line?  I hate to ask you to all but write a tutorial for this program, but I'm getting bupkiss and might just be missing something very obvious.

---

