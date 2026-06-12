---
title: "/dev/sda1 disk full"
date: 2008-07-21
forum: Mythbuntu
---

### Post by Caps18 on 2008-07-21
I've been running my Mythbuntu box since February without too many problems.  But something happened recently and I'm not sure what to remove to free up space.  When I use df in the command line, I get this:

> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              9843276   9840156         0 100% /
varrun                  517748       212    517536   1% /var/run
varlock                 517748         0    517748   0% /var/lock
udev                    517748        92    517656   1% /dev
devshm                  517748         0    517748   0% /dev/shm
lrm                     517748     34696    483052   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda2            720516512 659277092  61239420  92% /var/lib
overflow                  1024        16      1008   2% /tmp

I know I need to remove a few shows from sda2, but I thought the only thing on sda1 was the OS.  But it looks like something else is on there.  I could have sworn I had 5GB free on sda1 back in Feb, and the only thing running on this computer is MythTV.  What can I do to free up some disk space, as it is keeping mysql from running MythTV.

Thanks.

---

### Post by tgm4883 on 2008-07-21
check /var/log/mythtv

You might have something producing super huge logs

---

### Post by nickrout on 2008-07-21
> **tgm4883 said:**
> check /var/log/mythtv

You might have something producing super huge logs

The other thing is that when you update the .deb files go in /var/cache/apt/archive. To clean it up use:

```
apt-get clean
``` or

```
apt-get autoclean
```

from the man page:

> **clean**
    clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When APT is used as a dselect(8) method, clean is run automatically. Those who do not use dselect will likely want to run apt-get clean from time to time to free up disk space. 

**autoclean**
    Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless. This allows a cache to be maintained over a long period without it growing out of control. The configuration option APT::Clean-Installed will prevent installed packages from being erased if it is set to off.

---

### Post by Caps18 on 2008-07-21
> **tgm4883 said:**
> check /var/log/mythtv

You might have something producing super huge logs

That looks like it.  Can I remove these or limit their size in the future?

I bet there are plenty of errors with droppd internet connections, display issues, and full recording disk space, but the logs should be cleared out so only the past week or so is saved.  And I hope they wouldn't get to this size in one week. :)

-rw-r--r--  1 mythtv       mythtv 6270177280 2008-07-21 20:13 **mythbackend.log = 5.8 GB**
-rw-r--r--  1 mythtv       mythtv 1318313984 2008-07-21 06:26 **mythbackend.log.1 = 1.2 GB**
-rw-r--r--  1 mythtv       mythtv  795989779 2008-07-08 06:25 **mythbackend.log.2 = 795 MB**

It goes to .8, but that is only 100MB of data.The frontend log is only 8 MB.

---

### Post by tgm4883 on 2008-07-21
> **Caps18 said:**
> That looks like it.  Can I remove these or limit their size in the future?

I bet there are plenty of errors with droppd internet connections, display issues, and full recording disk space, but the logs should be cleared out so only the past week or so is saved.  And I hope they wouldn't get to this size in one week. :)

-rw-r--r--  1 mythtv       mythtv 6270177280 2008-07-21 20:13 **mythbackend.log = 5.8 GB**
-rw-r--r--  1 mythtv       mythtv 1318313984 2008-07-21 06:26 **mythbackend.log.1 = 1.2 GB**
-rw-r--r--  1 mythtv       mythtv  795989779 2008-07-08 06:25 **mythbackend.log.2 = 795 MB**

It goes to .8, but that is only 100MB of data.The frontend log is only 8 MB.

Note the dates on the biggest 2.  Your log grew to 5.8 GB in less that 1 day.  Thats a very serious issue.  I'd like to look at the end of that most recent log.  

Do 
```
tail -n 500 /var/log/mythtv/mythbackend.log > paste.log
``` 

Then paste that log file (paste.log) here so we can see whats going on.  After that, you can safely delete that file as well as the mythbackend.log and mythbackend.log.1

---

### Post by nickrout on 2008-07-21
is logrotate properly set up?

have a look at the logs and see what is taking up so much room. fix it. then the logs won't grow so fast :-)

---

### Post by tgm4883 on 2008-07-21
> **nickrout said:**
> is logrotate properly set up?

have a look at the logs and see what is taking up so much room. fix it. then the logs won't grow so fast :-)

Not exactly that simple, as not a whole lot of programs like to open log files that size.  Thats why I asked for the last 500 lines in the hopes that we could see whats going on and fix the issue.  The logs do rotate based on a time, not on size.

---

### Post by Caps18 on 2008-07-21
```
**2008-07-21 02:22:28.882 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.**
2008-07-21 02:23:38.374 EITScanner: Now looking for EIT data on multiplex of channel 2.1
2008-07-21 02:23:46.621 EITScanner: Added 201 EIT Events
2008-07-21 02:23:46.623 Reschedule requested for id -1.
2008-07-21 02:23:46.869 Scheduled 47 items in 0.2 = 0.05 match + 0.20 place
2008-07-21 02:24:28.901 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:25:23.869 EITScanner: Added 202 EIT Events
2008-07-21 02:25:28.910 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:26:28.922 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:27:45.503 DVBChan(1) Warning: Symbol Rate setting (0) is out of range (min/max:5056941/10762000)
**2008-07-21 02:27:45.521 EITScanner: Now looking for EIT data on multiplex of channel 2.1**
2008-07-21 02:28:28.931 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:28:59.118 EITScanner: Now looking for EIT data on multiplex of channel 2.1
2008-07-21 02:29:26.639 EITScanner: Added 200 EIT Events
2008-07-21 02:29:26.643 Reschedule requested for id -1.
2008-07-21 02:29:26.888 Scheduled 47 items in 0.2 = 0.05 match + 0.20 place
2008-07-21 02:30:15.414 EITScanner: Added 200 EIT Events
2008-07-21 02:30:28.944 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:30:28.955 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:32:28.975 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:33:06.250 DVBChan(1) Warning: Symbol Rate setting (0) is out of range (min/max:5056941/10762000)
2008-07-21 02:33:06.269 EITScanner: Now looking for EIT data on multiplex of channel 2.1
2008-07-21 02:34:18.191 EITScanner: Added 200 EIT Events
2008-07-21 02:34:18.193 Reschedule requested for id -1.
2008-07-21 02:34:18.438 Scheduled 47 items in 0.2 = 0.05 match + 0.20 place
2008-07-21 02:34:19.632 EITScanner: Now looking for EIT data on multiplex of channel 2.1
2008-07-21 02:34:28.983 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:35:28.997 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:35:55.118 EITScanner: Added 200 EIT Events
2008-07-21 02:36:29.005 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:38:27.037 DVBChan(1) Warning: Symbol Rate setting (0) is out of range (min/max:5056941/10762000)
2008-07-21 02:38:27.053 EITScanner: Now looking for EIT data on multiplex of channel 2.1
2008-07-21 02:38:29.018 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:39:40.362 EITScanner: Now looking for EIT data on multiplex of channel 2.1
2008-07-21 02:39:58.171 EITScanner: Added 201 EIT Events
2008-07-21 02:39:58.175 Reschedule requested for id -1.
2008-07-21 02:39:58.404 Scheduled 47 items in 0.2 = 0.03 match + 0.20 place
2008-07-21 02:40:29.035 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:40:29.043 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:41:30.730 EITScanner: Added 200 EIT Events
2008-07-21 02:42:29.059 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:43:47.830 DVBChan(1) Warning: Symbol Rate setting (0) is out of range (min/max:5056941/10762000)
2008-07-21 02:43:47.850 EITScanner: Now looking for EIT data on multiplex of channel 2.1
2008-07-21 02:44:29.075 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:45:01.184 EITScanner: Now looking for EIT data on multiplex of channel 2.1
2008-07-21 02:45:29.089 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.
2008-07-21 02:45:38.171 EITScanner: Added 200 EIT Events
2008-07-21 02:45:38.175 Reschedule requested for id -1.
2008-07-21 02:45:38.407 Scheduled 47 items in 0.2 = 0.03 match + 0.20 place
2008-07-21 02:46:26.813 EITScanner: Added 200 EIT Events
2008-07-21 02:46:29.102 AutoExpire: ERROR when trying to autoexpire file: /var/lib/mythtv/recordings/1451_20080505195631.mpg. File doesn't exist.  Database metadata will not be removed.

```

That's interesting.  Does it not like me manually deleting files without using MythTV?  I would bet that file was the first one I deleted when my recording partition became full and had the manually delete a file using the command line.  I have been known to delete a few more files like that since then.

The other one is interesting because I use schedule direct, and may have selected to try and get EIT data, butthought it would only do that if schedules direct didn't update for 2 weeks because of no interent connection.

---

### Post by tgm4883 on 2008-07-21
yea i wouldn't try to manually delete files like that.  Always use mythtv or mythweb

---

### Post by nickrout on 2008-07-21
> **tgm4883 said:**
> yea i wouldn't try to manually delete files like that.  Always use mythtv or mythweb

ditto. You should be able to tidy it up using 

[http://www.mythtv.org/wiki/index.php/Myth.find_orphans.pl](http://www.mythtv.org/wiki/index.php/Myth.find_orphans.pl)

or maybe

[http://www.mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl](http://www.mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl)

---

### Post by Caps18 on 2008-07-22
This might be a silly question, but where are those perl scripts located at usually?

---

### Post by nickrout on 2008-07-22
looks like mythbuntu puts them in 

```
/usr/share/doc/mythtv-backend/contrib/
```

---

### Post by Caps18 on 2008-07-22
Is the find orphans perl script there too, or is it in one of the .gz files?


file:///usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl

file:///usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl.gz

plus a few other files...

I will probably rebuild the database when I get home from work tonight.  Will I have to delete one of those old logs in order to have enough disk space to do this?

---

### Post by tgm4883 on 2008-07-22
go ahead and delete those two log files and free up the space

---

### Post by Caps18 on 2008-07-22
Now I have an issue where I don't have permission to run that perl script because it belogs to root.

I did find a place in the mythtv control center where I check a box to allow it to optimize the database everyday.  Maybe I'll wait a day to see if that works.

I'm still not quite sure why the mythbuntu icon I had for my start menu has been replaced with the xfce one, even though I have free space now and have rebooted a few times since.

---

### Post by nickrout on 2008-07-22
well thats what sudo is for!

---

### Post by Caps18 on 2008-07-23
I've never seen it do this before though. And I know I entered the right password for the mythbuntu user.  I've used su before, but something changed or was corrupted. I was trying to setup a stable computer, but it doesn't seem to want to stay consistant regardless of what the user does.

$ su
Password: 
su: Authentication failure
Sorry.

---

### Post by nickrout on 2008-07-23
I said sudo not su.

all the contrib scripts on my mythbuntu are owned by root and are NOT executable. I guess these scripts are not mainstream and are to be used at the owners discretion. Nevertheless most of them seem well used and tested.

So, if you want to use one I suggest copying it to (eg) /usr/local/bin, marking it executable, and then giving it a spin:

```
sudo cp /usr/share/doc/mythtv-backend/contrib/myth.find_orphans.pl /usr/local/bin
sudo chmod 755 /usr/local/bin/myth.find_orphans.pl
myth.find_orphans.pl
```

---

