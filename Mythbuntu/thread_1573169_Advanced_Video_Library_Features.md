---
title: "Advanced Video Library Features"
date: 2010-09-12
forum: Mythbuntu
---

### Post by Just4Fun20 on 2010-09-12
It appears the Video Library has the capability to have trailers, cover art and a number of other features.  Is there an automated way to use these features or populate that information?

A couple of releases ago I manually made the necessary images, named them properly and placed them in the proper directory.  My movies showed up with their cover art.  Very nice. 

I've seen many posts to suggest that there are better (automated) ways to do this but I can't find the beginning instructions.  That is, how do I set it up?  What steps and what information is needed?

I apologize up front if I've missed something obvious.  A pointer to the setup instructions would be great.  If they're not well defined then any assistance would be appreciated.  

Thank you in advance.

---

### Post by DemonBob on 2010-09-12
If you ether click i or m, goto metadata options -> download metadata. It should automatically use it's built in scripts to look for the information on themoviedb.com.

---

### Post by Just4Fun20 on 2010-09-13
I tried that.  As indicated i or m brings up a menu.  I went into the metadata menu.  I tried "Download Metadata" but it didn't return anything.  I tried "Manually Enter Video" and got the same results.  

How do I use "Manually Enter Video #" or more importantly how do I get the appropriate number?

Thank you.

---

### Post by joho500 on 2010-09-14
'Download Metadata' only fills the database with the data of the movie AFAIK. The jamu.pl script fetches the coverart and is called in an hourly and a daily cron job called mythvideo. So you have to wait a while or you could run the script manually (with the correct parameters;see the jamu.pl wiki). You can check the jamu.log in /var/log/mythtv to see whether it has run correctly.

Cheers,
Joost

---

### Post by joshoekstra on 2010-09-14
Err, nope, download metadata fetches cover and fanart for use as background...

---

### Post by Just4Fun20 on 2010-09-18
Well, it's not running (successfully) in a chon job and I can't get it to run manually, or at least I can't manage to get cover art or any of the other metadata.  This has never worked through probably 6 release levels.  

Any thoughts on how to troubleshoot?  

Pick a movie, say Star Trek (2009), how can I manually invoke a process to flood all the metadata for this movie?  It is IMDB movie tt0796366. 

Thank you for any assistance.

---

### Post by tgm4883 on 2010-09-18
> **Just4Fun20 said:**
> Well, it's not running (successfully) in a chon job and I can't get it to run manually, or at least I can't manage to get cover art or any of the other metadata.  This has never worked through probably 6 release levels.  

Any thoughts on how to troubleshoot?  

Pick a movie, say Star Trek (2009), how can I manually invoke a process to flood all the metadata for this movie?  It is IMDB movie tt0796366. 

Thank you for any assistance.

You open the menu and go to download metadata, works for me every time. If it doesn't work for you, then frontend/backend logs would be much more helpful. Also, FYI, IMDB is only used as a fallback. tmdb is used now.

---

### Post by Just4Fun20 on 2010-09-19
Well, I'm not sure what's different but it's working now.  I reinstalled, from the ISO, and it's working now.  

Is there a way to automatically invoke the process?   It would be nice, if the movies had the appropriate TMDB names, to run a routine that would automatically import the metadata for all of the files/movies (instead of going through and invoking it on each movie, one at a time).  

Thanks again for your help.  This is a very cool feature which I'm very glad to have working.

---

### Post by joshoekstra on 2010-09-20
For that latest part there's a cronjob called mythvideo whcih uses jamu and it logs to /var/log/mythtv/jamu.log, there you might be able to find a reason why it doesn't work as expected...

---

