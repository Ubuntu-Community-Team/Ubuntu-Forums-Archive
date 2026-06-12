---
title: "I filled up my root partition. :("
date: 2009-01-27
forum: Mythbuntu
---

### Post by Meph1st0 on 2009-01-27
So I allocated apparently 18 GB for my root partition.  I thought that would be enough as I figured most of the storage needed would be on my other partition mounted at /var/lib/mythtv.  But turns out I need to resize my root partition.  

I can't seem to resize my partitions at all, gparted won't let me.  I've attached a screenshots of how I partitioned my drive.  It allows me to open the resize/move window, but it doesn't allow me to make any changes to the partition sizes.

I figure I've got to resize/shrink /dev/sda6 first to create unallocated space and then I should be able to resize/grow /dev/sda5 to occupy that space.

Notice in the screenshots that the minimum sizes are the same as the maximum sizes for both partitions, therefore, it won't let me resize them.

Any ideas about how I can do this?  Also, is there a way I can see what it taking so much space on my root partition?  18 GB should be enough for the root partition of a mythbuntu box...I'm assuming of course.  Could it also be that I'm using my Gutsy 7.10 liveCD to use gparted and I'm actually Intrepid?

---

### Post by bgerlich on 2009-01-27
Xfs was designed for speed - it doesn't have shrinking capability. You'll have to backup your data and recreate the partition to shrink it.

18 gb is somewhat a lot for a root partition, have you tried cleaning the /tmp and sudo apt-get autoclean ?

To check which dir is taking how much space use the command "du". If yomu don't want the system to list all dirs use either --max-depth=? (how many directories "below") or --summarize (just dirs in directly in the folder you typed the command in) options.

---

### Post by cdtech on 2009-01-27
This command will give you the top disk usage:
```
sudo du -s * | sort -k1,1rn | head
```
You should be able to drag the arrows (left or right) at the top of the resize screen to shrink the partition. Then you can drag the arrow on the other partition to grow......

**UPDATE::.**
Good call bgerlich, I just seen the **Xfs**.......

---

### Post by movieman on 2009-01-27
By default, the Mythtv front-end sticks a load of stuff on the root partition, including temporary files for Mytharchive... that could be quite a few gigabytes by itself.

There's almost certainly a load of junk you can get rid of without needing to free up disk space; you may need to change the paths used by Mythtv to ensure they all go to /var/lib/mythtv.

---

### Post by rodercot on 2009-01-27
I think I am in the same boat.

 I setup my drive as

 / - 20GB
swap - 2gb
/var/lib - 298Gb

 Myth seems to be using my / partition. I look at the size data and it always says it is using /var/lib/mythtv for recordings but the size is only 18Gb not 298gb

 Thanks,
 
 Dave

---

### Post by zzztownsend on 2009-01-27
I got some very big log files following errors

take a look in /var/log/mythtv

cheers

matt

---

### Post by Caps18 on 2009-01-28
> **zzztownsend said:**
> I got some very big log files following errors

take a look in /var/log/mythtv

cheers

matt

This is what I was going to say.  I only have a 10 GB root partition and the only time it filled up was when I had logging turned on.  Now I only log stuff when I need to, or it is limited in some way, I can't remember.

---

### Post by utar on 2009-01-28
The mythtv log files are meant to rotate so that there is only ever a weeks worth of logs.  However unless you keep your box on 24 hours a day the process that rotates the logs never runs.

If you install anacron from the package manager you should find that this does rotate the logs and the log files don't grow to ridiculous sizes.

---

### Post by Caps18 on 2009-01-29
I sometimes leave my house for weeks at a time, so it has to stay on for 24 hours a day.  I got lucky when it happened that I had just gotten back, but it is one of those things that the default settings should be so it doesn't get over 100 MB unless you tell it to.

But, I'm sure there are a lot of other things like that that we have never noticed.  The thing about good software is that you don't notice it and it just works day in and day out.  My Mythbuntu computer has been doing really good in the past 6 months.

---

### Post by Meph1st0 on 2009-04-01
I need to resurrect this thread as I've done it again! LOL  I know, you'd think I'd learn the first time.  The thing is, the first time this happened to me I ended up giving up and just reloading Mythbuntu. However; I think that's the lazy way to solve a problem.  Now I'd like to come up with a solution.  

Following some of the suggestions I had received previously I found that my mythfrontend.log file was about 14 GBs in size.  So I deleted it.  Maybe I shouldn't have done that, idk.  But my partition now has free space again.  Now my problem appears to be related to the mysql database.  My box can't seem to connect to the backend database.  I found from other posts on the internet that other people who've filled up their root partition weren't able to connect to their master backend anymore either, but I never found a solution.

I can go into phpmyadmin and see that I do still have a mythconverg database and that nothing appears to be missing.  If I go to [http://localhost/mythweb](http://localhost/mythweb) I get an error message saying, "Error, unable to connect to the master backend at 127.0.0.1:6543. Is it running?"

one strange thing I've noticed is if I look at /home/myname/.mythtv/mysql.txt the database information is missing.  All the text and comments are there but the DBUsername, DBPassword, DBName, and DBType are empty parameters.  I don't even remember what the DBPassword was before this got all messed up.

Anyway, I think all I need to do is get mysql running again and I should be good to go.  But of course, I'm only making assumptions now.  Anybody have any ideas?

---

### Post by Meph1st0 on 2009-04-02
Okay, I've solved my problem.  I can genuinely mark this thread as solved.  Here's what happened.  The mythfrontend.log file found at /var/log/mythtv grew to consume my root partition.  I didn't know anything was wrong though until after I had rebooted after installing an update.  When it came back up I got the mythtv setup window asking about database information.  I thought this was strange and remembered that this was a symptom that I had noticed the first time I filled up my partition but I just canceled out of it.  Well apparently what this did is it replaced my previous mysql.txt file with a blank one that is found at /etc/mythtv.  Having a blank mysql.txt file prevented mythtv from being able to connect to the mythconverg database.  But of course I didn't notice this until a few days later of fussing.  During the fussing process I did eventually delete the bloated mythfrontend.log file to free up needed space.  Last night I just edited the mysql.txt file and reentered the information that belongs in it. (I miraculously remembered off the top of my head what the mysql password was for the mythtv user)  After that mythtv was able to reconnect to the mythconverg database with no problems and my system is happy again.

---

### Post by utar on 2009-04-02
The Myth logs are meant to automatically rotated and be deleted.  However unless you keep your Myth box on 24 hrs a day the process tends not to run.

If you install anacron you will find that this solves the problem going forward.

---

### Post by Meph1st0 on 2009-04-02
yes, I keep my mythbox on 24hrs a day.  So I just need to install anacron and that's it?  no configuring of said anacron program?  Is it just sudo apt-get install anacron?  I'll give that a try and see what happens, thanks!

---

### Post by utar on 2009-04-02
If the box is on 24 hours a day there is no need to install anacron, since your logs should rotate.  Wouldn't hurt to install it though.

I assume it was a one-off event that caused your log to grow, and not a case of the old logs growing because they had never been automatically deleted.

---

### Post by agamotto on 2009-04-04
I just check both of my boxes for this, and the log files were quite large.  Thankfully, I set aside 30Gb for the main partition.  I installed anacron, and I will see what happens from there.  Curiosity question, could this have something to do with recordings not being deleted off the hd after you delete them using the frontend?

---

### Post by neutron68 on 2009-04-05
> **utar said:**
> If the box is on 24 hours a day there is no need to install anacron, since your logs should rotate.  Wouldn't hurt to install it though.

I assume it was a one-off event that caused your log to grow, and not a case of the old logs growing because they had never been automatically deleted.
Do the logs rotate because logrotate is installed on our Mythbuntu systems?  
I see there is a /etc/logrotate.conf file on my 8.10 system and it is set to keep only 4 weeks of logs on the machine at any given time.  I also see that logrotate is being called in /etc/cron.weekly, so it only runs one time per week.
```
# see "man logrotate" for details
# rotate log files weekly
weekly

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    monthly
    create 0660 root utmp
    rotate 1
}

# system-specific logs may be configured here
```

I just read [http://en.wikipedia.org/wiki/Anacron]("http://en.wikipedia.org/wiki/Anacron") that anacron should only be necessary on a machine that doesn't run 24/7.  If the machine isn't left on for a solid week at a time, the weekly cron jobs (like logrotate) never get a chance to run.

So, I think that means that Meph1st0 either has a cronic error problem that is filling up his logs quickly or he isn't running his machine for at least 7 consecutive days in a row, and logrotate isn't being allowed to run once a week?

Eric

---

### Post by Meph1st0 on 2009-04-11
Hi Eric,

Well with regard to the rotating logs, I haven't dedicated much time to it.  However, from what I have found by going to mythweb and looking at the backend logs there, is a constantly reoccuring instance of the following:

62	25298	mythbackend	7	0	2009-04-11 04:20:59	browndvr	Running housekeeping thread	
63	25297	mythbackend	4	0	2009-04-11 04:19:57	browndvr	Delete Recording	File myth://127.0.0.1:6543/1051_20081114080000.mpg does not exist for chanid 1051 at Fri Nov 14 08:00:00 2008 when trying to delete recording.
64	25296	mythbackend	4	0	2009-04-11 04:19:57	browndvr	Last message repeated 2 times	Running housekeeping thread

That appears many, many, many times.  I don't believe that the file, 1051_20081114080000.mpg, is found on my computer but a record for the file is still in my mythconverg database.  And because there's a record of the file in the database myth thinks it still needs to delete it.  Due to the fact that the box is constantly trying to delete it and is unable to it's filling up my log files.  My guess is I just need to go into the mythconverg database and remove the record manually.

I'm going to go ahead and add this information to the thread for others to see as well.

Another question I have is, how do I check to see if the log rotation is working properly? can I check some sort of cron job log file to see if the task completes successfully or not?

I had actually put this off about a week or 2 ago.  It's possible that my hard drive is filling itself up as I write this.  It went about 2 months or so since this last time I filled up my partition and the first time.

Thanks,

Jonathan

---

