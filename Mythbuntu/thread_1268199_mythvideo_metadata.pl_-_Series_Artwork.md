---
title: "mythvideo_metadata.pl - Series Artwork?"
date: 2009-09-16
forum: Mythbuntu
---

### Post by SiHa on 2009-09-16
So I've just started playing with the above script, and I have to say I'm impressed.

Just one thing, I'd like to have it find artwork for the TV season folders (Friends Season 2 etc. (for my wife, you understand!)).

Is there a specific naming convention I should use, as with the episodes (Friends_S02E01) so that the script will pull in the season artwork from TMDB? 

I suppose Friends_S02 might do it, now that I think of it :oops:

TIA,

Simon

---

### Post by sfp on 2009-09-16
Naming Convension 
<Series Name> / <Series Number> /

eg

Friends/Season 02/Friends - S02E01.avi

---

### Post by williammanda on 2009-09-16
Not to dumb down the thread but is tmdb working ok? I got this working a couple of weeks ago and a couple of days ago it no longer works. I don't get any metadata for any of the the video's now.

---

### Post by SiHa on 2009-09-17
> **sfp said:**
> Naming Convension 
<Series Name> / <Series Number> /

eg

Friends/Season 02/Friends - S02E01.avi

Great, thanks!

> Not to dumb down the thread but is tmdb working ok?

Well I installed **mythvideo_metadata.pl** for the first time last night, and it worked like a charm. Got a few funny matches (ZZ Top -> Jazz Club?), but I suppose that's to be expected.
Although, I just noticed that the script I have is dated two days ago, version 1.0.8.4, perhaps you need to update?

---

### Post by williammanda on 2009-09-17
SiHa
Please specify how you installed mythvideo_metadata.pl?
Thanks

---

### Post by SiHa on 2009-09-17
I downloaded the latest version, by following the link from the MythTV wiki(Actually, I just Googled Mythvideo Metadata) [http://www.mythtv.org/wiki/Fill_mythvideo_metadata.pl](http://www.mythtv.org/wiki/Fill_mythvideo_metadata.pl)
Right click -> Save As -> fill_mythvideo_metadata.pl

So far, I'm just running from the commandline: ```
perl /PATH/TO/fill_mythvideo_metadata.pl
```

---

### Post by williammanda on 2009-09-17
This script references the imdb website [http://www.imdb.com/]("http://www.imdb.com/"). My understanding is that they are being replaced by tmdb [http://www.themoviedb.org/]("http://www.themoviedb.org/").
Is this script working for you?

---

### Post by silverdulcet on 2009-09-17
It uses thetvdb.com, imdb, tvsubtitles.net and they just recently added tmdb as a grabber as well. 
The script usually works perfect for me. Although the past couple days it seems thetvdb.com has had a bit of downtime, so when it falls back to imdb for getting tv show metadata it doesn't do so well. It provides switches for rescanning specific files or directories to correct any mismatches or instances where certain websites were down when trying to retrieve data. 

> **SiHa said:**
> 
Well I installed **mythvideo_metadata.pl** for the first time last night, and it worked like a charm. Got a few funny matches (ZZ Top -> Jazz Club?), but I suppose that's to be expected.
Although, I just noticed that the script I have is dated two days ago, version 1.0.8.4, perhaps you need to update?

If it has problems selecting the proper tv show or movie I'd encourage you to make use of the NFO files where you can tell the script that a whole directory (and subdirectories) are a certain show by providing the thetvdb.com show id number or imdb id number. Check out the mythtv.org wiki page on it or just read the comments in the beginning of the script for the proper syntax. You can even make them hidden files so that you wouldn't normally see them when browsing the directory.

---

### Post by sfp on 2009-09-18
to use tmdb as the movie grabber you will need to add  -tmdb 1 to the command line.
eg 
fill_mythvideo_metadata.pl -tmdb 1

---

### Post by SiHa on 2009-09-18
> **silverdulcet said:**
> 
If it has problems selecting the proper tv show or movie I'd encourage you to make use of the NFO files where you can tell the script that a whole directory (and subdirectories) are a certain show by providing the thetvdb.com show id number or imdb id number. Check out the mythtv.org wiki page on it or just read the comments in the beginning of the script for the proper syntax. You can even make them hidden files so that you wouldn't normally see them when browsing the directory.
Thanks, I'll try that.

[QUOTE=sfp]to use tmdb as the movie grabber you will need to add -tmdb 1 to the command line.
eg 
fill_mythvideo_metadata.pl -tmdb 1 [/QUOTE]

Also, it will use motechnet for the posters, I think that's where most of mine came from

[QUOTE=sfp]Naming Convension 
<Series Name> / <Series Number> /

eg

Friends/Season 02/Friends - S02E01.avi [/QUOTE]
Again, thanks - worked a treat.

---

### Post by williammanda on 2009-09-18
I review the wiki [http://www.mythtv.org/wiki/Fill_mythvideo_metadata.pl]("http://www.mythtv.org/wiki/Fill_mythvideo_metadata.pl")
But I don't see how to setup the file for use. I don't know perl. Do I just copy the file from the website and save it. Then just invoke the perl file in terminal? Also can the file be executed upon startup of mythtv?
Thanks

---

### Post by joho500 on 2009-09-19
I've just set it up last week. It seems to work ok. I saved the file in /usr/bin and set up an new file in cron.daily with these lines:
```

#!/bin/sh
/usr/bin/fill_mythvideo_metadata.pl -TMDB 1

```

This way it will run every day and use [www.themoviedb.org](www.themoviedb.org). That's all.

Cheers,
Joost

---

### Post by williammanda on 2009-09-19
> **joho500 said:**
> I've just set it up last week. It seems to work ok. I saved the file in /usr/bin and set up an new file in cron.daily with these lines:
```

#!/bin/sh
/usr/bin/fill_mythvideo_metadata.pl -TMDB 1

```

This way it will run every day and use [www.themoviedb.org](www.themoviedb.org). That's all.

Cheers,
Joost

What did you do to prep the the file? As I stated earlier....did you copy and paste the contents into a new file and name it fill_mythviceo_metadata.pl and make it executable? Also if what I have stated is correct shouldn't I be able to run it from the desktop?

---

### Post by silverdulcet on 2009-09-19
> **williammanda said:**
> I review the wiki [http://www.mythtv.org/wiki/Fill_mythvideo_metadata.pl]("http://www.mythtv.org/wiki/Fill_mythvideo_metadata.pl")
But I don't see how to setup the file for use. I don't know perl. Do I just copy the file from the website and save it. Then just invoke the perl file in terminal? Also can the file be executed upon startup of mythtv?
Thanks

To set it up, open a Terminal window and change to the directory where you'd like to place the script. It makes it much easier to run if you place it in a directory that is part of your PATH. For example, I placed it in /usr/local/bin

```
cd /usr/local/bin
```

Then you fetch the file from the download link with the command wget. Since that directory is by default only writable by root, I must use sudo before the wget command and to make it executable.

```
sudo wget http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl
```

make it executable

```
sudo chmod +x fill-mythvideo-metadata.pl
```

Once you've done that you can run it from any directory. Probably a good idea to double check that you are part of the mythtv user group so that you can make changes to your videos directory. It obtains the database password from the mysql.txt file and your videos directory from the mythtv database. The script only has a few options to change. Most you can leave default. For example, changing whether it fetches movie posters from imdb or tmdb. The format that it uses for naming your tv shows or movies when it adds them to the database. 

If you supply the script with the command-line switches it will override what you have set up inside the script file itself.

> Also if what I have stated is correct shouldn't I be able to run it from the desktop?

You could run it from the desktop. The script does provides a lot of output when looking up videos and matching metadata. If you run it from the desktop, I'd recommend piping the output to some sort of log file so that if it matches the wrong metadata for a video, or there is some sort of permission problem you can find out what went wrong.

---

### Post by williammanda on 2009-09-20
> **silverdulcet said:**
> To set it up, open a Terminal window and change to the directory where you'd like to place the script. It makes it much easier to run if you place it in a directory that is part of your PATH. For example, I placed it in /usr/local/bin

```
cd /usr/local/bin
```

Then you fetch the file from the download link with the command wget. Since that directory is by default only writable by root, I must use sudo before the wget command and to make it executable.

```
sudo wget http://fill-mythvideo-metadata.googlecode.com/svn/trunk/fill_mythvideo_metadata.pl
```

make it executable

```
sudo chmod +x fill-mythvideo-metadata.pl
```

Once you've done that you can run it from any directory. Probably a good idea to double check that you are part of the mythtv user group so that you can make changes to your videos directory. It obtains the database password from the mysql.txt file and your videos directory from the mythtv database. The script only has a few options to change. Most you can leave default. For example, changing whether it fetches movie posters from imdb or tmdb. The format that it uses for naming your tv shows or movies when it adds them to the database. 

If you supply the script with the command-line switches it will override what you have set up inside the script file itself.



You could run it from the desktop. The script does provides a lot of output when looking up videos and matching metadata. If you run it from the desktop, I'd recommend piping the output to some sort of log file so that if it matches the wrong metadata for a video, or there is some sort of permission problem you can find out what went wrong.

Thanks for the input! Just one last question. Right now I'm using this script...

[http://www.mythtv.org/wiki/Tmdb.pl]("http://www.mythtv.org/wiki/Tmdb.pl")

and it gives me the ability to edit each movie individually via the frontend. It seems using the fill_mythvideo_metadata.pl script...it is command line only?

---

### Post by silverdulcet on 2009-09-21
> **williammanda said:**
> Thanks for the input! Just one last question. Right now I'm using this script...

[http://www.mythtv.org/wiki/Tmdb.pl]("http://www.mythtv.org/wiki/Tmdb.pl")

and it gives me the ability to edit each movie individually via the frontend. It seems using the fill_mythvideo_metadata.pl script...it is command line only?

Yes, it is designed to be run from the command line manually or added to your crontab so that it runs every X days/hours/minutes, etc. I usually run it manually when I've added new TV shows or Movies. I've also created seperate shell scripts with the command line switches for rescanning (via the scan as new file switch) a single directory or a specific video. If you just run the script alone it will automatically add any new video files to the database and search for metadata for it. Any files that already have existing metadata will be skipped, unless you use the command switch to scan them as a new files.

The advantage of this script is that it works for both movies and tv show metadata. You also don't need to edit each movie individually. If it doesn't match correctly you can tell it the correct show or movie by creating nfo files on the individual file level and/or the folder level. In my experience as long as you follow the well known naming conventions for tv show and movie files it rarely comes up with the wrong metadata. The only time I often see problems is when there are multiple movies by the same name.

---

