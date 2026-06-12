---
title: "Video Manager empty"
date: 2008-12-31
forum: Mythbuntu
---

### Post by rastoboy on 2008-12-31
I'm losing my mind trying to figure this out--and surprisingly can't find anything in the forums about it.  

When I go to the Video Manger, it's blank, and doesn't find videos I've stuck in /var/lib/mythtv/videos.  Do they need any funky special permissions or ownership or anything?

I have the exact same issue with music.  I put mp3's into /var/lib/mythtv/music, and then hit "scan for music" and it just instantly comes back.

Any ideas what I'm doing wrong?  Any input would be greatly appreciated!

---

### Post by tgm4883 on 2008-12-31
the mythtv group should have at least read access to the folder

---

### Post by newlinux on 2009-01-01
You might want to take a look at your frontend logs when you do the scan to see what is happening.

---

### Post by rastoboy on 2009-01-01
@tgm4883: I've even tried opening them up 777, no luck.

@newlinux: That's a very reasonable idea--thanks.  Another thing I've been wondering is where the frontend log might be?  I see these links for "generating logs" and such but I'd like to get at them via CLI for greppy and awkish purposes...?

---

### Post by newlinux on 2009-01-01
IF you start mythfrontend from the terminal, the log will printout to the terminal. If you start it from the menu or with the --service option, it will be in /var/log/mythtv/mythfrontend.log

---

### Post by rastoboy on 2009-01-01
Awesome, thanks so much!  I guess I should have looked there--I've just gotten so used to apps using some random place for their logs I didn't think to check the obvious :-( my bad.

Strangely, it appears doing a tail -f on mythfrontend.log got the music scanning to work.  As it were.  The only thing that's changed (to my knowledge) is I rebooted since the last time I'd tried it.  Weird.  I'm going to try not to think about it for now :-)

Videos are another story.  I got this sort of thing for each video in the directory (presumeably):

2009-01-01 20:50:25.998 DB Error (Querying video metadata):
Query was:
SELECT title, director, plot, rating, year, userrating,length, filename, showlevel, coverfile, inetref, childid,browse, playcommand, category, intid FROM videometadata
Driver error was [2/130]:
QMYSQL3: Unable to execute query
Database error was:
Incorrect file format 'videometadata'

2009-01-01 20:50:26.357 DB Error (video metadata update):
Query was:
INSERT INTO videometadata (title,director,plot,rating,year,userrating,length,filename,showlevel,coverfile,inetref,browse) VALUES ('1008 - Make Love, Not Warcraft', 'Unknown', 'None', 'NR', 1895, 0, 0, '/var/lib/mythtv/videos/1008 - Make Love, Not Warcraft.avi', 1, 'No Cover', '00000000', 1)
Driver error was [2/130]:
QMYSQL3: Unable to execute query
Database error was:
Incorrect file format 'videometadata'

2009-01-01 20:50:26.359 DB Error (video metadata update):
Query was:
INSERT INTO videometadata (title,director,plot,rating,year,userrating,length,filename,showlevel,coverfile,inetref,browse) VALUES ('A man for all seasons', 'Unknown', 'None', 'NR', 1895, 0, 0, '/var/lib/mythtv/videos/A man for all seasons (DivX).avi', 1, 'No Cover', '00000000', 1)
Driver error was [2/130]:
QMYSQL3: Unable to execute query
Database error was:
Incorrect file format 'videometadata'


Personally, I'm not interested in having the metadata available--I just want to be able to pick out files and play any random thing.  Is there a way to disable this?

---

### Post by newlinux on 2009-01-01
looks like you need to repair your database - There is an optimize_mythdb.pl that will do it in the contrib directory of your mythtv install (/usr/share/doc/mythtv-backend/contrib/). You can also do it from mythweb. Otherwise there is a setting that allows mythvideo to browse by files instead of what has been scanned into the database. It's in the video settings somewhere. 

I recommend you run repair and optimize on the db regularly. I think mythbuntu-control-centre can set this up. I run nightly cron job that runs optimize_mythdb.pl as well as backs up the DB everyday.

---

### Post by rastoboy on 2009-01-03
Thanks again Newlinux!

I got the same results after running the db optimization script.  However, I found the setting (I had stared at it several times without realizing what it was) that let me just browse the files.

I gotta say--it's pretty sweet.  MythTV automagically handled every format I had, including mkv, and even automounted some iso's!  Totally awesome.

Now if I could just get sound, I'd have all the basic functions working!  It's looking like maybe I need to pass a commandline parameter to mplayer?  I guess I should probably ask that in a new thread really. (or uh, search for it first )

---

