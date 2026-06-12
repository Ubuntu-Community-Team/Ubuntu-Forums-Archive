---
title: "Fresh 10.04 - Cover art disappears overnight"
date: 2010-05-17
forum: Mythbuntu
---

### Post by brian_hammerhead on 2010-05-17
I just installed a fresh, 64-bit version of Mythbuntu 10.04 Release.  I use .iso  files, so I disabled storage groups.  The .iso files play pretty well.   I spent quite a bit of time selecting my meta data by pressing "w" for  each of my 150+ videos.  Ahhh... Looks very nice - except for the fact  that none of the movie ratings were coming down with the rest of the  meta data.  I did some digging into the grabber script (tmdb.py), but I  don't know Python.  As best as I could tell, the script was looking for a  key pair called "MovieRating", but tmdb was sending back  "Certification".  Oh well.  I guess I just do without movie ratings.  :(

The next day, ALL MY COVER ART WAS MISSING!  Dang. :mad:    I checked the MythTV database using phpmyadmin and found that all of the full paths to my cover art were  changed so that the path was completely missing.  All that was showing  was the filename for the cover art graphic with no path.  The previous day, I had manually entered the coverart for  some of my videos that were missing in tmdb.  All those files still had their  cover art - and their full path names in the MythTV database.

I added a few of the cover art files back by reseting the metadata and  then pressing "w" again.  The next day, THOSE COVER ART PICTURES WERE  MISSING.

I haven't had much experience with jamu, but after scouring the net for  quite a while I figured that it was the culprit.  I checked my configuration and found:

```
/usr/share/mythtv/mythvideo/scripts$ ./jamu.py -MVf

There was no default Jamu configuration file found  (/home/stonefam/.mythtv/jamu.conf)

2010-05-17 19:08:20.429 Python Database Connection: Using connection  settings from /home/stonefam/.mythtv/config.xml

==========================================================================================
Listed below are the types and base directories Jamu will use for  processing.
The list reflects your current configuration for the 'mythtv' back end
and whether a directory is a 'SG' (storage group) or not.
Note: All directories are from settings in the MythDB specific to  hostname (mythtv).
Note: Screenshot directories are not listed as Jamu does not process  Screenshots.
------------------------------------------------------------------------------------------
Type: Fan art     - SG-YES - Directory: (/var/lib/mythtv/fanart)
Type: Video       - SG-NO  - Directory: (/var/lib/mythtv/videos)
Type: Cover art   - SG-YES - Directory: (/var/lib/mythtv/coverart)
Type: Banners     - SG-YES - Directory: (/var/lib/mythtv/banners)
------------------------------------------------------------------------------------------
```The  configuration looks correct, but the paths still get deleted in the  database.

jamu -v returns version 0.7.3


Q1. Does anyone know how to keep jamu from deleting the path info from  the MythTV database?

Q2. Does anyone know how to fix the tmdb.py script so that it grabs the  movie ratings?

---

### Post by iamlindoro on 2010-05-17
If you are not using the video storage group, you will need to remove the coverart, fanart, banner, and screenshot storage groups in mythtv-setup.  Highlight each directory in each group and press "d" until they are all gone.

---

### Post by brian_hammerhead on 2010-05-18
> **iamlindoro said:**
> If you are not using the video storage group, you will need to remove the coverart, fanart, banner, and screenshot storage groups in mythtv-setup.  Highlight each directory in each group and press "d" until they are all gone.

I deleted the coverart, fanart, banner, and screenshot storage groups as instructed.  Voila.  By the end of the day, all of the coverart magically reappeared!  

Jamu must have run and fixed the directory paths in the MythTV database.

The TV ratings still aren't downloading.  All of the ratings are NR.  However, I will post a new thread with this issue if it ends up bugging me too much.

Thanks very much, Iamlindoro!

---

### Post by iamlindoro on 2010-05-18
There is no source of TV ratings, and thus nowhere from which to fill them.

---

### Post by brian_hammerhead on 2010-05-19
> **iamlindoro said:**
> There is no source of TV ratings, and thus nowhere from which to fill them.

Iamlindoro,

  Thanks again for your reply.  I mis-typed.  I don't care about TV Ratings.  What I am looking for is Movie ratings.

  If I run tmdb.py from the command line, I can see the movie ratings listed as "Certification".  However, when I execute the tmdb.py grabber from within MythVideo ("w" key), the movie ratings are not returned.  I don't know Python, but when I looked at the tmdb.py code, it looks like it was expecting the movie ratings to be returned from TMDB as "Movie Rating" rather than "Certification".

  It seems to me that this would be a bug that would affect everyone, but as I have searched the web, I couldn't find anyone else reporting this problem.  Perhaps I don't know how to search as well as I need to, or perhaps it is a simple fix that most don't bother to report, or perhaps people don't care about movie ratings very much.

  If anyone happens to know the answer to the issue of movie ratings not being grabbed correctly via tmdb.py, I would love to know it.   As I mentioned, I may start a new thread if no one replies, but I wanted to clear up my mistaken post when I asked for "TV" ratings.  :)

---

### Post by iamlindoro on 2010-05-19
TMDB ratings support was only added about two weeks ago, and I applied the fix to support them to .23-fixes then.  If you are not getting movie ratings, then you are not on current fixes.  If that's the case, it means you are running the original packages of .23 distributed fir Mythbuntu 10.04, which is definitely not a good thing.  .23 was released last monday, which means everyone running the stock packages is running an early pre-release of .23.  You should enable auto-builds and get to current fixes, and then movie ratings will work properly.

---

### Post by moz_21 on 2010-06-03
> **brian_hammerhead said:**
> I deleted the coverart, fanart, banner, and screenshot storage groups as instructed.  Voila.  By the end of the day, all of the coverart magically reappeared!  

Jamu must have run and fixed the directory paths in the MythTV database.

The TV ratings still aren't downloading.  All of the ratings are NR.  However, I will post a new thread with this issue if it ends up bugging me too much.

Thanks very much, Iamlindoro!

I'm having this problem also. I deleted the storage groups as advised. I wasn't using a storage group for my videos folder. I am on the lastest fixes. Is there a cron job that needs to be ran to re-update the missing cover art? Thanks!

---

### Post by geekyhawkes on 2010-06-05
Excuse my ignorance, how do i set my myth to get the latest fixes?  I am also having problems with metadata and movies but it seems pointless to go forward without the latest builds.  Thanks.


EDIT:  [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)  search, its a wonderful thing!

---

### Post by d-pearson on 2010-06-14
Hey iamlindoro,

Sorry for jumping in a couple of weeks later but could you help me also!
I have the exact same issue except I use an external HDD for my media. In the config file my config is as follows:

> Type: Fan art     - SG-YES - Directory: (/var/lib/mythtv/fanart)
Type: Video       - SG-YES  - Directory: (/var/lib/mythtv/videos)
Type: Video       - SG-NO  - Directory: (/media/MEDIA)
Type: Cover art   - SG-YES - Directory: (/var/lib/mythtv/coverart)
Type: Banners     - SG-YES - Directory: (/var/lib/mythtv/banners)

Could you please explain where to go in my issue to do the following:

> **iamlindoro said:**
> If you are not using the video storage group, you will need to remove the coverart, fanart, banner, and screenshot storage groups in mythtv-setup.  Highlight each directory in each group and press "d" until they are all gone.

Bear in mind I do use the /var/lib/mythtv/videos directory!

Thanks
Dan

---

