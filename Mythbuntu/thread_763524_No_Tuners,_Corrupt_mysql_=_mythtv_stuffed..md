---
title: "No Tuners, Corrupt mysql? = mythtv stuffed."
date: 2008-04-23
forum: Mythbuntu
---

### Post by ubuntme on 2008-04-23
I have managed to break my mythbuntu.

I was setting up a frontend on an eeepc.

And it updated the backend schema apparently.

It said it made a backup of the database, but I forgot the name and can't find it.

The problem is that the tuners have disappeared.  i.e. it says I don't have any tuners avaliable, and no tuners are listed in status, or in mythtv-setup.  Mythtv-setup can see the tuners, but you can't add and name them.

The previous recordings are still there...

Any ideas what I have done and how to fix it???

Thanks

I could be in trouble for breaking the telly!

edit: More info from the backend log:

2008-04-23 17:27:25.022 Using runtime prefix = /usr
2008-04-23 17:27:25.081 New DB connection, total: 1
2008-04-23 17:27:25.086 Connected to database 'mythconverg' at host: localhost
2008-04-23 17:27:25.089 Current Schema Version: 1214
2008-04-23 17:27:25.091 New DB connection, total: 2
2008-04-23 17:27:25.092 Connected to database 'mythconverg' at host: localhost
2008-04-23 17:27:25.093 Newest Schema Version : 1160
2008-04-23 17:27:25.095 New DB connection, total: 3
2008-04-23 17:27:25.096 Connected to database 'mythconverg' at host: localhost
2008-04-23 17:27:25.097 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2008-04-23 17:27:25.098 New DB connection, total: 4
2008-04-23 17:27:25.099 Connected to database 'mythconverg' at host: localhost
2008-04-23 17:27:25.116 Database Schema upgrade complete, unlocking.
Starting up as the master server.
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?

---

### Post by ubuntme on 2008-04-23
Well, I fixed the tuner problem.

Using this:
[http://http://www.avsforum.com/avs-vb/archive/index.php/t-839718.html]("http://www.avsforum.com/avs-vb/archive/index.php/t-839718.html")

Except know I have lost:

1) The list of my previous recordings
2) mythvideo doesn't browse
3) no mythmusic whatsoever

Any ideas?

---

### Post by ubuntme on 2008-04-23
2) and 3) are fixed.  1) I might be stuck with.

---

### Post by elj4176 on 2008-04-23
Do you still have your recorded files? If so you can use the mythrebuild.pl script to import the files back into the db.

---

### Post by pseudo-random on 2008-04-23
I gave up on Myth. It's good if you watch a lot of telly but I don't so I settled for Me-tv. It does recording/scheduled recording, Network broadcast etc without an SQL backend.
[http://www.youtube.com/watch?v=4l2RrRNpPgw](http://www.youtube.com/watch?v=4l2RrRNpPgw)

---

### Post by klc5555 on 2008-04-23
> **elj4176 said:**
> Do you still have your recorded files? If so you can use the mythrebuild.pl script to import the files back into the db.

The mythrebuild.pl script doesn't seem to be well-documented.

How do you work it (in 20.2 on 7.10)?

In my particular case, mythtv .21 (Gutsy) broke a lot more stuff than it fixed. In particular, I as my recording space dwindled, I needed an actual working mytharchive plugin. So I decided to backlevel to 20.2. The brute force way: I consolidated all recordings into one directory on my 2nd drive (along with my daily mythconverg backups), blew away the installation on the first drive, reformatted, reinstalled from 7.10 iso, etc. etc....and restored the database. It was successful, and, of course, mytharchive .20.2 also worked.

But it turns out that the tuner card information appears to be stored in .21 mythconverg in a way which is incompatible with the way it was done in .20.2 So, if I restore the database, I have my recordings, but tuner card configuration info can't be saved. If I drop mythconverg and make a new one, I can add and configure tuner cards (in .20.2) normally, but of course I can't see the recordings.

So I've been archiving (since that works again in 20.2) everything worth archiving, in preparation for dropping mythconverg again and making another new one in order to configure the tuning cards and start fresh. I had planned on dumping the remaining unarchived recordings, but it appears that mythrebuild.pl could add them to the new mythconverg? True?

It makes one wonder why there is only the one giant mythconverg in mythtv. It would seem that breaking it into, say, two databases --one just for all hardware/software settings and a second one for all the channel/recordings information-- would make the entire setup more robust and more portable.

---

### Post by ubuntme on 2008-04-23
> **elj4176 said:**
> Do you still have your recorded files? If so you can use the mythrebuild.pl script to import the files back into the db.

Yes.

There is no mythrebuild.pl on my system.

There is a myth.rebuilddatabase.pl....

However, I think I just found the mythconverg database backup...

---

### Post by elj4176 on 2008-04-24
It's been awhile since i have used that script and I have only used it once so you may be better off doing a google for better info.
IIRC - I just had to run the script and tell it which files to import. It went through them one by one.

[http://ubuntuforums.org/showthread.php?t=375566](http://ubuntuforums.org/showthread.php?t=375566)
[http://mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl](http://mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl)


Hope that helps

---

### Post by klc5555 on 2008-04-25
> **elj4176 said:**
> It's been awhile since i have used that script and I have only used it once so you may be better off doing a google for better info.
IIRC - I just had to run the script and tell it which files to import. It went through them one by one.

[http://ubuntuforums.org/showthread.php?t=375566](http://ubuntuforums.org/showthread.php?t=375566)
[http://mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl](http://mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl)


Hope that helps

Thanks! 

I'll give it a try this weekend on my now happily-backleveled 7.10/0.20.2 system, which still has some of the old recorded files that I did not archive to DVD before dropping and creating a new mythconverg

Cheers. :)

---

