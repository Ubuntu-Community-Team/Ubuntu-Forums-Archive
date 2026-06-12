---
title: "hdd died, now trying to clean up database"
date: 2009-02-11
forum: Mythbuntu
---

### Post by dannyboy79 on 2009-02-11
SOLVED-Read entire thread.

Hopefully someone can help me. My hdd died and whenever I open Mythweb, it still shows those recordings as being there, the .png (thumbnail) isn't present but the recording shows like it's still there but I know it's not because I removed the hdd. How can I clean up the database so that mythweb shows the correct actual recordings? Any help would be much appreciated. thank you.

I am running the following system:
```
sudo aptitude show mythtv
```
0.20.2-0ubuntu0.7.04.1

```
sudo aptitude show mythweb
```
0.20.2-0ubuntu0.7.04.1

---

### Post by klc5555 on 2009-02-11
> **dannyboy79 said:**
> Hopefully someone can help me. My hdd died and whenever I open Mythweb, it still shows those recordings as being there, the .png (thumbnail) isn't present but the recording shows like it's still there but I know it's not because I removed the hdd. How can I clean up the database so that mythweb shows the correct actual recordings? Any help would be much appreciated. thank you.

I am running the following system:
```
sudo aptitude show mythtv
```
0.20.2-0ubuntu0.7.04.1

```
sudo aptitude show mythweb
```
0.20.2-0ubuntu0.7.04.1

Easiest way to clean phantom recordings out of the db is from the front end. In Watch Recordings, right click on the phantom title, and Myth protests recording not found. You can then delete the listings metadata for the phantom from there. 

This also works for LiveTV phantoms in the AutoExpire List, which cannot be deleted directly from that list. Instead move the phantom from AutoExpire to the Default group, and delete as above.

In the case of a skazillion recording phantoms, the cleanup script myth.find_orphans.pl (from the /contrib directory) may be the easier solution, though you'll likely have to download/install some extra perl modules to run it. Actually, I'm not sure 7.04 even _has_ a /contrib directory; the current version of the script is available here: 
[http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib](http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib)

It should still run on Mythtv 0.20.2, once the appropriate perl modules are installed, but you would want to give it a couple of trial runs before you actually let it modify anything.

Cheers! :)

---

### Post by dannyboy79 on 2009-02-11
thanks

---

### Post by dannyboy79 on 2009-02-12
> **klc5555 said:**
> Easiest way to clean phantom recordings out of the db is from the front end. In Watch Recordings, right click on the phantom title, and Myth protests recording not found. You can then delete the listings metadata for the phantom from there. 

This also works for LiveTV phantoms in the AutoExpire List, which cannot be deleted directly from that list. Instead move the phantom from AutoExpire to the Default group, and delete as above.

In the case of a skazillion recording phantoms, the cleanup script myth.find_orphans.pl (from the /contrib directory) may be the easier solution, though you'll likely have to download/install some extra perl modules to run it. Actually, I'm not sure 7.04 even _has_ a /contrib directory; the current version of the script is available here: 
[http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib](http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib)

It should still run on Mythtv 0.20.2, once the appropriate perl modules are installed, but you would want to give it a couple of trial runs before you actually let it modify anything.

Cheers! :)
how do I run the  command? When I try to run the command I get this error:

```
sudo /home/daniel/Desktop/orphaned_files.pl
```
DBI connect('database=mythconverg:host=UBUNTU','mythtv',...) failed: Access denied for user 'mythtv'@'UBUNTU' (using password: YES) at /home/daniel/Desktop/orphaned_files.pl line 99
Cannot connect to database mythconverg on host UBUNTU:

any suggestions?

---

### Post by klc5555 on 2009-02-12
> **dannyboy79 said:**
> how do I run the  command? When I try to run the command I get this error:

```
sudo /home/daniel/Desktop/orphaned_files.pl
```
DBI connect('database=mythconverg:host=UBUNTU','mythtv',...) failed: Access denied for user 'mythtv'@'UBUNTU' (using password: YES) at /home/daniel/Desktop/orphaned_files.pl line 99
Cannot connect to database mythconverg on host UBUNTU:

any suggestions?

You have to give it the MySQL password as a command-line parameter (--pass=whatever-your-mysql-password-is). In some versions and derivatives of this script (for example myth.rebuilddatabase.pl) you also have to give it a specific recording directory (--dir=), but as near as I recall (been about 6 months since I last used the script) you don't have to specify directory with the original "find orphan" script itself.

Cheers! :)

---

### Post by dannyboy79 on 2009-02-12
I did have to specify the password as well as the directory. I want to thank you so much!!!! Mythweb is so much faster now, I had 172 recordings missing and 2 unknown files. So now all is good to go. Thank you again!!!!!!

here's the command I ran:

/home/daniel/Desktop/orphaned_files.pl --pass=mwpnycvz --dir=/media/300gb/mythtv/ --dodbdelete

and then:

/home/daniel/Desktop/orphaned_files.pl --pass=mwpnycvz --dir=/media/300gb/mythtv/ --dodelete

Oh and by the way, I didn't find the myth.find_orphans.pl script within the mythtv contrib directory for the version of mythtv I am running.

---

### Post by chrisblue on 2009-02-14
Would this work if I wanted to move a number of recordings from a previous install to the latest install (on different HD)?

I don't have a lot of recordings but I have no idea how to get the database to update and I am uncertain that just moving recordings into the correct directories will fully integrate them with the new install.

---

### Post by dannyboy79 on 2009-02-15
no, this will mnot work for that purpose. this may help:
[http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.5](http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.5)
also this may help:
[http://thefreegeek.blogspot.com/2008/06/mythtv.html](http://thefreegeek.blogspot.com/2008/06/mythtv.html)

---

### Post by chrisblue on 2009-02-16
Thanks for the link dannyboy79, that looks like it will help. One question I have though, will it merge the data or just overwrite if I have already recorded some stuff on the new install?

---

### Post by dannyboy79 on 2009-02-16
sorry, I can't answer that. I would have to say that it will most likely overwrite it due to you having 2 differnt databases. BUT I think you could just save the recordings off somewhere that are in the new install, then drop the old database, add the new database to your new machine, then move the new recordings you had into the folder where the recordings are that you put from the old machine, then use the orphan file program and it should find the recordings from the new machine that weren't in the old machine and it should add them to the new database.  I would maybe join the mythtv mailing list and ask there or go to the mythtv IRC channel or mythbuntu orc channel. You might want to start a new thread as you're most likely not going to get an answer in this thread due you being off topic from what the subject is of the thread. Good luck.

---

### Post by klc5555 on 2009-02-17
> **dannyboy79 said:**
> sorry, I can't answer that. I would have to say that it will most likely overwrite it due to you having 2 differnt databases. BUT I think you could just save the recordings off somewhere that are in the new install, then drop the old database, add the new database to your new machine, then move the new recordings you had into the folder where the recordings are that you put from the old machine, then use the orphan file program and it should find the recordings from the new machine that weren't in the old machine and it should add them to the new database.  I would maybe join the mythtv mailing list and ask there or go to the mythtv IRC channel or mythbuntu orc channel. You might want to start a new thread as you're most likely not going to get an answer in this thread due you being off topic from what the subject is of the thread. Good luck.

When you restore a database, it overwrites what it finds. So recordings made after the last backup, but before the restore will not immediately be findable.

However, this is not a problem. The script you need is myth.rebuilddatabase.pl from the /contrib directory or from here: 
[http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib/](http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib/)

Mythbuntu may need a few extra perl module packages installed to run the script, in particular libdatetime-perl

The script needs to be run on each directory in the default storage group with the --dir=  and --pass=  parameters in the command line specified. It will find every recording in the specified directory without a database entry, will search for tv schedules information for the recording (show, title, summary, etc), will allow you to type in information for whatever it doesn't find (or offer default info), and finally will offer to compose an index and commflag the newly-databased recording (since these things went >poof< with the overwritten database and you'll need them). Then the script moves on to the next discovered recording until it finishes them all.

Cheers!

---

### Post by dannyboy79 on 2009-02-17
> **klc5555 said:**
> When you restore a database, it overwrites what it finds. So recordings made after the last backup, but before the restore will not immediately be findable.

However, this is not a problem. The script you need is myth.rebuilddatabase.pl from the /contrib directory or from here: 
[http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib/](http://svn.mythtv.org/svn/branches/release-0-21-fixes/mythtv/contrib/)

Mythbuntu may need a few extra perl module packages installed to run the script, in particular libdatetime-perl

The script needs to be run on each directory in the default storage group with the --dir=  and --pass=  parameters in the command line specified. It will find every recording in the specified directory without a database entry, will search for tv schedules information for the recording (show, title, summary, etc), will allow you to type in information for whatever it doesn't find (or offer default info), and finally will offer to compose an index and commflag the newly-databased recording (since these things went >poof< with the overwritten database and you'll need them). Then the script moves on to the next discovered recording until it finishes them all.

Cheers!
WOW, very valuable info as I may be building a new computer and upgrading to the latest Mythbuntu for my 2 machines. Possibly new hard drives to replace the one 500gb that died. Heck, it may even be under warrenty because I thought Seagate bought Western Digital? It's too bad the ATI all-in-wonder cards don't work in linux yet. I bought it long ago when I was a windows user. I still have 1 computer that has XP on it, barely gets turned on. ANyway, thanks again.

---

### Post by drifting on 2009-04-07
Oh heck !!

I followed this tread in the vain hope of sorting out the speed issues I have been having with my server, most seemed to be due to database problems. 

Summary:
  Host: vs, Directories: /media/store
  0 valid recordings, 0 missing recordings 
  0 known media files using 0B
  276 orphaned thumbnails with no corresponding recording
  192 unknown files using 649.3GB were fixed

ARG !!! That just wiped out all my recordings !

So now no recordings whatsoever in Myth, yet I still have recording files on the data storage drives?

Please tell me I am not totally nailed !! The soon it seems X wife will not be impressed.

Paul.

---

### Post by klc5555 on 2009-04-07
> **drifting said:**
> Oh heck !!

I followed this tread in the vain hope of sorting out the speed issues I have been having with my server, most seemed to be due to database problems. 

Summary:
  Host: vs, Directories: /media/store
  0 valid recordings, 0 missing recordings 
  0 known media files using 0B
  276 orphaned thumbnails with no corresponding recording
  192 unknown files using 649.3GB were fixed

ARG !!! That just wiped out all my recordings !

So now no recordings whatsoever in Myth, yet I still have recording files on the data storage drives?

Please tell me I am not totally nailed !! The soon it seems X wife will not be impressed.

Paul.

If you still have the actual recording files (*.mpg, *.nuv) on your data storage drives, then you're never totally nailed.

At this point the simplest thing by far would be to restore mythconverg from your most recent mysql database backup, and use the script myth.rebuilddatabase.pl to add back into the database anything that may have been recorded since that last backup.

If you don't have a recent regular backup of mythconverg to restore from, I bet you'll set one up pretty soon as described here: 
[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Maintaining_your_MythTV](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Maintaining_your_MythTV)
Because now you get to rebuild the entire database using myth.rebuilddatabase.pl. Better brew a pot of coffee. A big one.

Myth.rebuilddatabase.pl will go through an entire directory of recordings (you need to run it again for each separate storage group directory on each separate backend); it will check your listings data over the past 10 days for information on any recordings it finds, will allow you to type in information for recordings it has no data for, and will then make the recording appear basically where it should in myth. Before starting, you need to install the various perl libtimedate and datetime modules that the script uses.

The script will be run sudo. You will need to use the --dir=  and the --pass=  parameters to give it the path to the recordings directory and the mysql password. You'll also need to have some viewer ready to go (xine, mplayer), and a web browser for research at tv sites, because for recordings older than the 10th day, you'll need the viewer to figure out what the recording is that the script has found, so that you can type in the title, subtitle, and synopsis of the episode, as appropriate. Once the script has added the recording to the database, you can't easily edit the recording information further, so best get it right the first time. 

The script has a few quirks as it operates. It will supply only myth's 4-digit code for the channel number. Don't change this, as the script will then rename the file to fit, and other utilities (like mythtranscode) will not be able to handle the recording until its file is renamed back. The script offers a default episode length of [60] minutes. It turns out that the listed episode length will always be faulty in myth, regardless of what is put in this box, and in "watch recordings" will look something like "8:00AM-11:00PM" This quirk (like the 4-digit channel quirk) does not affect any aspect of watching or archiving the recording. Just looks odd in the Recordings index.

As each recording is added, the script will offer to create an index for it using mythcommflag. An index will be necessary and you should let the script do it. But if the recording is dvb, particularly HD, the index mythcommflag produces is generally non-functional. Each of these dvb and/or HD recordings will need to have its index built individually at some later time with mythtranscode:  mythtranscode --mpeg2 --buildindex --allkeys -c [channel] -s [starttime].  When there are a lot of dvb recordings to handle in this fashion, I've found it easier to set this command up as a user job, so I can drop a bunch of recordings into the job queue from mythfrontend and let the machine chug through the whole lot of them.

Finally, the newly indexed and viewable recordings will not be commercial flagged. If this is necessary for a particular recording, it can be done after the fact.

myth.rebuilddatabase.pl will also find all the recordings trash in the recordings directory --livetv fragments and whatnot. These are easily deleted from the Recordings menu in the usual fashion at some later time.

Good luck!

---

### Post by drifting on 2009-04-08
What a fantastic and very informative post. Thank you so much for taking the time to write that.

To be honest I gave up and deleted what was left as I just do not have the time to spend on it, and knowing that there were other issues perhaps it was time to wipe it.

Here is a couple of odd things, which makes me think a total rebuild may be in order. When I had wiped all the data, and then did another few recordings, I re ran the clean script and it promptly deleted the new recordings ? So is my database that broken or is the cleanup script ?

I would like to keep up the upcoming recordings, but not the duplicate info as I would liek to rerecord those, wonder if that is possible? Orhter than that I think I will just wipe the whole server and start again.

Paul.

---

