---
title: "Come test Mythvideo-bulk-updater"
date: 2008-08-26
forum: Mythbuntu
---

### Post by tgm4883 on 2008-08-26
Come test Mythvideo-bulk-updater, it can be grabbed by either adding the repo listed here [http://launchpad.net/~mythbuntu-testing/+archive](http://launchpad.net/~mythbuntu-testing/+archive)  or by going into the repo and manually downloading the .deb.

Mythvideo-bulk-updater only needs to be installed on a single machine and will look for the videos in /var/lib/mythtv/videos.

Installing mythvideo-bulk-updater will install a cron job in /etc/cron.hourly and scan your video collection every hour for new files and update.

Please report any problems here.

---

### Post by tgm4883 on 2008-08-28
In an effort to consolidate testing software, a Mythbuntu-testing PPA has been formed.  This PPA will contain software that is targeted for the next release, but should also backport it to the current release (it also will be software not in the current release repos)

The new PPA is located here
[http://launchpad.net/~mythbuntu-testing/+archive](http://launchpad.net/~mythbuntu-testing/+archive)


Sorry for the confusion.

---

### Post by bmwman on 2008-08-29
Can another video folder be added into the script? I have a second 500gb HDD and I mount it to /home/backend/Media and that's where most of my videos are.

---

### Post by tgm4883 on 2008-08-29
> **bmwman said:**
> Can another video folder be added into the script? I have a second 500gb HDD and I mount it to /home/backend/Media and that's where most of my videos are.

Do you have multiple video directories?  the script should grab your video directory from the db

---

### Post by bmwman on 2008-08-29
I just built my new HTPC and I'm still configuring stuff. But yes, i will use the defaut /var/lib/mythtv/videos folder and the rest it's in /home/backend/Media which is actually my second HDD mounted in there. Would the script monitor both folders?

---

### Post by tgm4883 on 2008-08-30
Good question.  It's not my script, I'm just packaging it, although I would think that it does.  As long as you list both directories in mythvideo settings.  The correct syntax for this would be /myth/video:/myth/video1

---

### Post by pisani on 2008-09-02
> The correct syntax for this would be /myth/video:/myth/video1

The script will honour multiple video directories as long as they are listed in the mythvideo settings in this format. It will alternatively follow links if you create a symlink to your main video folder to your secondary one.

---

### Post by Lindsay.Mathieson on 2008-10-29
Do you still want testers for this package?

---

### Post by tgm4883 on 2008-10-29
> **Lindsay.Mathieson said:**
> Do you still want testers for this package?

Yes

---

### Post by Lindsay.Mathieson on 2008-10-29
> **tgm4883 said:**
> Yes

Cool. Dumb question - if I add the [http://launchpad.net/~mythbuntu-testing/+archive](http://launchpad.net/~mythbuntu-testing/+archive) will it update anything else other than mythvideo-bulk-updater?

---

### Post by Lindsay.Mathieson on 2008-10-29
Also - reports results here?

---

### Post by tgm4883 on 2008-10-29
It will only update things that are in that repo if you do an apt-get upgrade.  I'd like to say that the only things in there are mythnettv, mythvideo-bulk-updater, and mythexport stuff, but 2 mythtv files got in there somehow.  Let me figure those out and report back.

---

### Post by tgm4883 on 2008-10-29
Ok, those mythtv packages have been removed.

---

### Post by Lindsay.Mathieson on 2008-10-29
Thanks,

installed no problems and the script is in cron.hourly. I'll test adding videos next.

---

### Post by Lindsay.Mathieson on 2008-10-29
Ok, I ripped a DVD to ISO. The log shows that the scan ran at 9:17 but the iso did not get registered in the video list.

When I ran a scan via the myth menus it was picked up.

---

### Post by Lindsay.Mathieson on 2008-10-30
I have tried the same with a .AVI file - same problem, not picked up. A manual scan from Myth did.

---

### Post by tgm4883 on 2008-10-30
> **Lindsay.Mathieson said:**
> I have tried the same with a .AVI file - same problem, not picked up. A manual scan from Myth did.

Can you paste the contents of /var/log/mythtv/mythvideoupdate.log in here?

---

### Post by Lindsay.Mathieson on 2008-10-30
Sure

```


***** Starting update at 08:17 10/30/2008*****




***** Starting update at 09:17 10/30/2008*****




***** Starting update at 10:17 10/30/2008*****




***** Starting update at 11:17 10/30/2008*****




***** Starting update at 12:17 10/30/2008*****




***** Starting update at 13:17 10/30/2008*****




***** Starting update at 14:17 10/30/2008*****




***** Starting update at 15:17 10/30/2008*****




***** Starting update at 16:17 10/30/2008*****




***** Starting update at 17:17 10/30/2008*****




***** Starting update at 18:17 10/30/2008*****




***** Starting update at 19:17 10/30/2008*****




***** Starting update at 20:17 10/30/2008*****




***** Starting update at 21:17 10/30/2008*****




***** Starting update at 22:17 10/30/2008*****




***** Starting update at 23:17 10/30/2008*****




***** Starting update at 00:17 10/31/2008*****




***** Starting update at 01:17 10/31/2008*****




***** Starting update at 02:17 10/31/2008*****




***** Starting update at 03:17 10/31/2008*****




***** Starting update at 04:17 10/31/2008*****




***** Starting update at 05:17 10/31/2008*****




```

---

### Post by orduek on 2008-10-30
I think it has something to do with the update of Myth video manager.
Only after updating through the video manager Myth "understands" it has new video files.
There has to be a way to automate this process also.

---

### Post by Lindsay.Mathieson on 2008-10-30
> **orduek said:**
> I think it has something to do with the update of Myth video manager.
Only after updating through the video manager Myth "understands" it has new video files.


Ok, now I'm confused - that's what I thought mythvideo-bulk-updater was supposed to do, otherwise what's the point?

---

### Post by orduek on 2008-10-30
He just creating a connection between the name of the file and the description from IMDB.
BUt looks like he doesn't searches for new files unless Myth already did it.

---

### Post by Lindsay.Mathieson on 2008-10-30
> **orduek said:**
> He just creating a connection between the name of the file and the description from IMDB.
BUt looks like he doesn't searches for new files unless Myth already did it.

Ok, I see. Thanks.

---

### Post by tgm4883 on 2008-10-31
That is not correct.  Mythvideo-bulk-update is suppose to search for new files also.  I'll dig into this a little more and see what I can find.

---

### Post by orduek on 2008-10-31
OK, Thanks.

---

### Post by orduek on 2008-10-31
> **Lindsay.Mathieson said:**
> I have tried the same with a .AVI file - same problem, not picked up. A manual scan from Myth did.

Same problem here.
even after I did a manual scan, the script didn't add the data and picture of the movies / series.

---

### Post by tgm4883 on 2008-11-01
I think I have found the problem.  Could you edit /usr/share/mythvideo-bulk-updater 

Change this line 

```
command = "/usr/share/mythvideo-bulk-updater/imdb-bulk-update.pl -N -Dupskip -Exclude -Host "+hostname+" -Password "+password
```

to this line

```
command = "/usr/share/mythvideo-bulk-updater/imdb-bulk-update.pl -N -Dupskip -Exclude -Fileup -Host "+hostname+" -Password "+password
```

Let me know if that works.

---

### Post by orduek on 2008-11-01
since i changed the command - according to the log file it doesn't run anymore.
last run time was before change.

---

### Post by Lindsay.Mathieson on 2008-11-03
Ok, the command change runs for me, but still no update.

As a test I  logged on remotely as my normal user (lindsay) and ran the (expanded) command &#8211; that worked, picked up the new videos with no errors

I then ran it as the mythtv user (as per the cron script) and got this error:

```

=============================================================================  
Retrieving Video Path for this mythserver from mythconverg.settings            
=============================================================================  
Retrieving ignored files extensions from mythconverg.videometadata             
=============================================================================  
Retrieving allowable file extensions from mythconverg.videometadata            
=============================================================================  
Found 57 total videos in /var/lib/mythtv/videos                                
=============================================================================  
Retrieving a list of known videos from mythconverg.videometadata               
=============================================================================  
Scrubbing the database for any videos that no longer exist in /var/lib/mythtv/videos                                                                            
=============================================================================   
Found no new videos to be added to database                                     

Error: Posters path: /home/lindsay/.mythtv/MythVideo doesn't exist or is not writable                  

```

I made the directory in question world writeable and tried again. This time it worked. I suspect as I typically grab imdb info as a std user (lindsay) it trying to update the ~/lindsay/.mythtv/MythVideo directory and failing because its the mythtv user.

I'll see if the cron job picks up a new video now but that will have to wait a few hours as I'm off to bed :)

---

### Post by orduek on 2008-11-10
Any updates on the success of these trials?
Is it working now?

---

### Post by Lindsay.Mathieson on 2008-11-10
Nope, still not working

---

### Post by tgm4883 on 2008-11-10
hmm

Lets try this.  Make a posters directory at /var/lib/mythtv/posters  Then make do

```
chown mythtv:mythtv /var/lib/mythtv/posters
```

then 

```
chmod 775 /var/lib/mythtv/posters
```

Then add the following code to /usr/share/mythvideo-bulk-updater/mythvideo-bulk-updater.py (replacing the command line that is currently in there with the code provided.)

```
posterdir="/var/lib/mythtv/posters"

command = "/usr/share/mythvideo-bulk-updater/imdb-bulk-update.pl -N -Dupskip -Exclude -Fileup -Host "+hostname+" -Password "+password+" -Posters "+posterdir
```

---

### Post by Lindsay.Mathieson on 2008-11-10
Done, will let you know how it goes.

---

### Post by orduek on 2008-11-12
> **Lindsay.Mathieson said:**
> Done, will let you know how it goes.

any progress?

---

### Post by Lindsay.Mathieson on 2008-11-12
Sorry, been busy at work :(

No progress I'm afraid. Still not picking up videos.

---

### Post by tgm4883 on 2008-11-16
This is very odd, I just ran a test and it picked up my movies fine.  I'll remove them all and do another test.  If this one works as well, I'll post back with the content of all my files and dir permissions for this.

Also, it's worth noting that mythvideo-bulk-updater does not resolve conflicts.  If you have a movie name that comes back with multiple possibilities then those movies will not get info and must be manually scanned (ie Short Circuit will come back with Short Circuit and Short Circuit 2.  Ocean's Eleven will come back with the old version from the 60's and with the new version).  Is this possibly what is happening?

---

### Post by tgm4883 on 2008-11-16
Yep, it ran fine again (missing movies that return dups (like starwars)).  Here are all my relevant files in hoping that they will help us find the issues.


/etc/cron.hourly/
-rwxr-xr-x 1 root root 502 2008-10-21 17:07 mythvideo-bulk-updater
```
#!/bin/bash

DATE=`date '+%R %m/%d/%Y'`

su mythtv -c "echo ''" >> /var/log/mythtv/mythvideoupdate.log
su mythtv -c "echo '***** Starting update at '$DATE'*****'" >> /var/log/mythtv/mythvideoupdate.log
su mythtv -c "echo ''" >> /var/log/mythtv/mythvideoupdate.log
su mythtv -c "/usr/share/mythvideo-bulk-updater/mythvideo-bulk-updater.py" >> /var/log/mythtv/mythvideoupdate.log
su mythtv -c "echo ''" >> /var/log/mythtv/mythvideoupdate.log
su mythtv -c "echo ''" >> /var/log/mythtv/mythvideoupdate.log
```


/usr/share/mythvideo-bulk-updater/
-rwxr-xr-x 1 root root   877 2008-11-10 09:35 mythvideo-bulk-updater.py
```
#!/usr/bin/python

import os
import re
import string

home = os.environ.get('HOME')
if os.path.exists(home+'/.mythtv/mysql.txt'):
	dbinfo = home+'/.mythtv/mysql.txt'
elif os.path.exists('/usr/share/mythtv/mysql.txt'):
	dbinfo = '/usr/share/mythtv/mysql.txt'
else:
	dbinfo = '/etc/mythtv/mysql.txt'

fi = open(dbinfo)	
for line in fi:
     	if re.compile("^DBHostName").search(line):
                    text=string.split(string.split(line,"=")[1],'\n')[0]
                    hostname = text
     	elif re.compile("^DBPassword").search(line):
                    text=string.split(string.split(line,"=")[1],'\n')[0]
                    password = text
fi.close()

posterdir="/var/lib/mythtv/posters"

command = "/usr/share/mythvideo-bulk-updater/imdb-bulk-update.pl -N -Dupskip -Exclude -Fileup -Host "+hostname+" -Password "+password+" -Posters "+posterdir
os.system(command)
```


It might also be worth noting that this only searches for videos not currently in the db.  This means that if you can see it when you go to "Media Library > Watch Videos" then this will not update that movie.(even if the movie has no info about it, if you can view it here I don't think the script thinks it's new)

---

### Post by tgm4883 on 2008-11-16
> **Lindsay.Mathieson said:**
> Ok, the command change runs for me, but still no update.

As a test I  logged on remotely as my normal user (lindsay) and ran the (expanded) command – that worked, picked up the new videos with no errors

I then ran it as the mythtv user (as per the cron script) and got this error:

```

=============================================================================  
Retrieving Video Path for this mythserver from mythconverg.settings            
=============================================================================  
Retrieving ignored files extensions from mythconverg.videometadata             
=============================================================================  
Retrieving allowable file extensions from mythconverg.videometadata            
=============================================================================  
Found 57 total videos in /var/lib/mythtv/videos                                
=============================================================================  
Retrieving a list of known videos from mythconverg.videometadata               
=============================================================================  
Scrubbing the database for any videos that no longer exist in /var/lib/mythtv/videos                                                                            
=============================================================================   
Found no new videos to be added to database                                     

Error: Posters path: /home/lindsay/.mythtv/MythVideo doesn't exist or is not writable                  

```

I made the directory in question world writeable and tried again. This time it worked. I suspect as I typically grab imdb info as a std user (lindsay) it trying to update the ~/lindsay/.mythtv/MythVideo directory and failing because its the mythtv user.

I'll see if the cron job picks up a new video now but that will have to wait a few hours as I'm off to bed :)

Probably also worth noting is that besides the posters error, this log seems to be running fine

---

### Post by tgm4883 on 2008-11-20
Well I haven't heard back from anyone, does that mean the program is now working?

---

### Post by Lindsay.Mathieson on 2008-11-20
Nope, not working

---

### Post by Archmage on 2008-12-01
Okay. I did test it. It is doing the update every hour, but isn't doing anything at all, although there are new videos.

What should I do?

---

### Post by p2k on 2008-12-24
Works great for me!

I first had problems because the mythtv user could not access my video files. Those are accessed over the network using FUSE and sshfs, and adding the allow_other option solved it.

Best regards,
Patrick.

---

### Post by uMuppet on 2009-01-19
I have built a Bulk Meta Updater for MythVideo much like yours but with a graphical front end.  Both our scripts are different both with their own advantages, can we combine them together to make some sort of super script :grin:

I have only had a quick look through yours but here is what I can see could be added to it from mine,

[LIST]
[*]Can use any MythVideo path.  It finds the current one from the database
[*]Same with posters path, but if it doesn't exist it will create one.
[*]Has a button to scan and look for new videos in folder and add them to the database.
[*]Uses the TVRage script if it detects that it is a TV program rather than a Movie, and uses MPlayer to create a poster
[*]A Few options in the GUI to alter the way the IMDB script works like 'set and forget' and only videos without data
[/LIST]

I have borrowed a few pieces of your code to improve mine too.

I'm just learning Python so my code is a lot messier than yours and missing some of the fancy tricks you use to do the same thing.

You can find the code in the [download section of MythKiwi.com]("http://mythkiwi.com/index.php/remository?func=fileinfo&id=12")

---

