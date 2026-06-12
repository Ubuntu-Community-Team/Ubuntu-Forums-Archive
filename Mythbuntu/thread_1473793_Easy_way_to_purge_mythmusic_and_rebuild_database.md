---
title: "Easy way to purge mythmusic and rebuild database?"
date: 2010-05-05
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-05-05
I have totally reformated my MP3 ID tags recently and a rescan in mythmusic hasnt carried across all of my updates.  I tried TOUCH to update the modify times of the files but some of the old mp3 tag ID3 data is still coming up in myth (but not in rhythmbox on my laptop so I know the file is ok). 

How do i clean out the entire mythmusic database and rebuild from scratch?

Thanks

---

### Post by Lepy on 2010-05-05
I had to do the same thing a while back on .22
I found the answer on the mailing list, as it is a very helpful resource: [http://www.gossamer-threads.com/lists/mythtv/users/407460](http://www.gossamer-threads.com/lists/mythtv/users/407460)

As always, backup your database before you attempt this!

```
cat << "EOF" | mysql -umythtv -p mythconverg 
DROP TABLE IF EXISTS musicmetadata; 
DROP TABLE IF EXISTS musicplaylist; 
DROP TABLE IF EXISTS smartplaylistcategory; 
DROP TABLE IF EXISTS smartplaylist; 
DROP TABLE IF EXISTS smartplaylistitem; 
DROP TABLE IF EXISTS music_albums; 
DROP TABLE IF EXISTS music_artists; 
DROP TABLE IF EXISTS music_genres; 
DROP TABLE IF EXISTS music_playlists; 
DROP TABLE IF EXISTS music_songs; 
DROP TABLE IF EXISTS music_stats; 
DROP TABLE IF EXISTS music_smartplaylists; 
DROP TABLE IF EXISTS music_smartplaylist_items; 
DROP TABLE IF EXISTS music_smartplaylist_categories; 
DROP TABLE IF EXISTS music_directories; 
DROP TABLE IF EXISTS music_albumart; 
DELETE FROM settings WHERE value = 'MusicDBSchemaVer'; 
EOF 
```

Then restart the frontend.

---

### Post by geekyhawkes on 2010-05-07
Great thanks,

next problem is what is my password for my sql?  I have found plenty of guides to reset it but what implications does that have within myth?

I have looked here etc/mythtv/mysql.txt but the password at the end of the file doesnt work...

---

### Post by novellahub on 2010-05-07
> **geekyhawkes said:**
> Great thanks,

next problem is what is my password for my sql?  I have found plenty of guides to reset it but what implications does that have within myth?

I have looked here etc/mythtv/mysql.txt but the password at the end of the file doesnt work...

```

grep DBPassword /etc/mythtv/config.xml

```

Or you can use the root user instead of mythtv.  The root password is your login password.

---

### Post by geekyhawkes on 2010-05-08
Thats got it thanks.

---

### Post by geekyhawkes on 2010-05-08
Except, strangly i am having problems getting my music back into myth!  If i run an inport then all 7500 mp3s are listed as imported but then when i go to play music it goes through another full scan and then i have no music listed.

Any idea how i can get my music back in myth?

---

### Post by geekyhawkes on 2010-05-10
Any thoughts on the above?  Is theere a log file i can check that might give me a clue what is going on?

---

### Post by geekyhawkes on 2010-05-10
Im just wondering if somehow its a permissions issue, I was thinking of running the following;

sudo chmod uo+rw -R /media/MP3/

Should that work or am i opening up all sorts of other problems?

---

### Post by matt06 on 2010-05-10
> **geekyhawkes said:**
> Im just wondering if somehow its a permissions issue

That was my initial thought reading your post, but was reluctant to give advice on changing permissions.

---

### Post by geekyhawkes on 2010-05-11
Right nothing to do with permissions as far as i can see, see attached file (seems to be an issue regarding the tables i dropped as above.  how do i create them again?)

Clearly I need to create the tables again so mythmusic can populate them once the search is complete.

---

### Post by geekyhawkes on 2010-05-11
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=156465&stc=1&d=1273596403[/IMG]

---

### Post by nickrout on 2010-05-12
Have you stopped all frontends and started again? I believe the frontend starting may trigger fixing the database. Not sure though. You could also try restarting the backend.

---

### Post by geekyhawkes on 2010-05-12
I have tried exiting the front end as well as restarting the machine with no changes.  Maybe i should close the frontend, redelete the tables then restart the machine and start again?

Guess it cant hurt?

---

### Post by geekyhawkes on 2010-05-12
Right,  doesnt work restarting the front end.

I just went back and re dropped the tables from myth with the front end closed, reloaded the front end and the music import process comes up with all the errors as listed in the screen shot above. 

The backend is recording atm so I cannot restart it although I am pretty sure that wont do anything (i have tried it before i am sure).

This is driving me crazy, bad ID3 tags was better than no music in myth!

How do i get these tables back in/fix the issue?

Thanks

---

### Post by nickrout on 2010-05-12
I would go to the mailing list and ask there. The myth database guru does not frequent this forum, but is always happy to help on the mailing list.

---

### Post by geekyhawkes on 2010-05-13
Thanks, I will post back any reply i get if i can fix the issue in case anyone else finds themselves with this issue.

---

### Post by geekyhawkes on 2010-05-14
I sent a message day before yesterday but how do i know if it has entered the mailing list?

I sent it to [email]mythtv-users@mythtv.org[/email]  is that all i need to do?

---

### Post by geekyhawkes on 2010-05-15
Also, anyone think that upgrading to .23 and 10.04 might fix the issue?  This has been going on for a while now and i would really like my music back in myth

---

### Post by matt06 on 2010-05-15
Upgrading might be a bit drastic unless you have a known good backup first.  If you don't care about saving your db/mythmusic prefs try disabling MythMusic in Mythbuntu Control Center and/or purging mythmusic in synaptic and then tryr reinstalling mythmusic.

---

### Post by kja999 on 2010-05-15
You could recreate the tables by taking the relevant create statements (for each of the dropped tables) from the scripts in /usr/share/mythtv/sql.

---

### Post by geekyhawkes on 2010-05-16
> You could recreate the tables by taking the relevant create statements (for each of the dropped tables) from the scripts in /usr/share/mythtv/sql.

Perfect, worked a treat thanks

---

### Post by w1ll1am on 2012-02-04
I know that this thread is old but I am having the same issues. I could not get mythmusic to show my album art so I dropped the files and now I can not import music. Any ideas on who to fix this? How do I use the CREATE statements in the .sql files?

---

