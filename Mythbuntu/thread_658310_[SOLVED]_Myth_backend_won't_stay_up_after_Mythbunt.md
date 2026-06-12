---
title: "[SOLVED] Myth backend won't stay up after Mythbuntu update today!"
date: 2008-01-04
forum: Mythbuntu
---

### Post by jpv on 2008-01-04
EDITED: this was self-inflicted and NOT a MythTV, Mythbuntu or update problem!!!

The problem turned out to be that--right around the same time I did the update--I also added some monitoring via the excellent Monit package.  But I was too clever for my own good and the Monit packets were killing Myth.  BUT, it would only happen on a Monit polling cycle, so from my perspective it would happen at "random" times!  And of course I forgot all about that minor little tweak, as I was doing a bunch of things at once...  "What else changed in the environment?"  "Why nothing..."  AARRGGHH!!!

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I just did an aptitude upgrade on my Mythbuntu backend and now it won't stay up.  :-(

All the usual myth* stuff was upgraded, here's a partial list (aptitude dist-upgrade):
[INDENT][UPGRADE] mythtv-backend-master 0.20.2+fixes15216-0ubuntu0~mythbuntu1 -> 0.20.2+fixes15283-0ubuntu0~mythbuntu1
[UPGRADE] mythtv-common 0.20.2+fixes15216-0ubuntu0~mythbuntu1 -> 0.20.2+fixes15283-0ubuntu0~mythbuntu1
[UPGRADE] mythtv-database 0.20.2+fixes15216-0ubuntu0~mythbuntu1 -> 0.20.2+fixes15283-0ubuntu0~mythbuntu1
[UPGRADE] mythtv-frontend 0.20.2+fixes15216-0ubuntu0~mythbuntu1 -> 0.20.2+fixes15283-0ubuntu0~mythbuntu1
[/INDENT]

It *seems* to start fine, but the listeners only stay up for a few seconds.  Running "/usr/bin/mythbackend -v all" doesn't help as far as I can tell.  It comes up, but when I start poking around on a separate frontend machine, it works for a few seconds then I start getting "Could not connect to the master backend server...".  The last few lines in the "-v all" output always seem to be:
[INDENT]
2008-01-04 14:20:17.994 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillSuggestedRunTime' AND hostname = 'mythtv-be-01' ;
2008-01-04 14:20:17.995 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillSuggestedRunTime' AND hostname IS NULL;
2008-01-04 14:20:17.996 MSqlQuery: SELECT lastrun FROM housekeeping WHERE tag = 'MythFillDB' ;
2008-01-04 14:20:17.997 MSqlQuery: SELECT lastrun FROM housekeeping WHERE tag = 'DailyCleanup' ;
2008-01-04 14:20:17.998 MSqlQuery: SELECT lastrun FROM housekeeping WHERE tag = 'JobQueueRecover-mythtv-be-01' ;
[/INDENT]

~~~~~~~
Other notes, in case they are useful:

1) I've been having a problem for a while now that ubuntu-mythtv-frontend never seems to consider itself upgraded.  I'll run an update, it will say everything worked, but then if I run the same update again, it claims that the FE needs to be updated, which it just supposedly did.  For example:
[UPGRADE] ubuntu-mythtv-frontend 0.20.2+fixes15283-0ubuntu0~mythbuntu1 -> 0.20.2+fixes15283-0ubuntu0~mythbuntu1

I don't really use the FE on the BE server, so I haven't worried about it too much.

2) My "user" account is perhaps poorly named as 'mythtvuser.'  That just caused a problem in the init script, which I've submitted as [https://bugs.launchpad.net/mythbuntu/+bug/180414](https://bugs.launchpad.net/mythbuntu/+bug/180414).

3) During the upgrade I got this:
[INDENT]Setting up mythtv-database (0.20.2+fixes15283-0ubuntu0~mythbuntu1) ...
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: NO) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
[/INDENT]

"sudo dpkg-reconfigure mythtv-database" completed successfully once I reset the MySQL root password which I'd forgotten and which is *not* the same as the MythTV user password in /home/mythtvuser/.mythtv/mysql.txt.  There is also no /root/.my.cnf file, if that matters.  The DB *user* account and password are correct in /etc/mythtv/mysql.txt (and /home/mythtvuser/.mythtv/mysql.txt).


Thanks,
JP

---

### Post by jpv on 2008-01-04
I just reverted to my last known good versions and it STILL doesn't work, so I thought something about my config got mangled.

There is probably a better way to do this (thoughts please?), but I brute forced it by:

1) Manually downloading all the (old) files from [http://ppa.launchpad.net/mythbuntu/ubuntu/pool/*](http://ppa.launchpad.net/mythbuntu/ubuntu/pool/*) into a dir

2) # dpkg --force-downgrade -i *.deb
[INDENT]This resulted in unmet dependencies (WTH?), so:[/INDENT]

3) # aptitude install libjack0 libflac7
[INDENT]This gave me all kinds of feedback on bustedness (yeah, I know, thanks...) and suggested this, which I did.
Install the following packages: libjack0.100.0-0 [0.103.0-6ubuntu1 (gutsy)]
[INDENT]Upgrade the following packages: mythmusic [0.20.2+fixes14681-0ubuntu0~mythbuntu1 (now) -> 0.20.2+fixes15283-0ubuntu0~mythbuntu1 (gutsy)]
[/INDENT][/INDENT]

4) # dpkg --force-downgrade -i *.deb
[INDENT]This mostly worked except for:
[INDENT]dpkg: dependency problems prevent configuration of mythmusic:
	 mythmusic depends on libflac7; however:
	  Package libflac7 is not installed.
[/INDENT][/INDENT]

Sample of daemons just dieing.  I was using the Myth FE from another machine to try and watch live TV while running the command below:

[root@mythtv-be-01:T1:L2:C585:J0:2008-01-04_16:49:37_EST]
/root/myth-revert# netstat -lnp | grep -i '/my'
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     4508/mysqld         
tcp        0      0 0.0.0.0:6543            0.0.0.0:*               LISTEN     17860/mythbackend   
tcp        0      0 0.0.0.0:6544            0.0.0.0:*               LISTEN     17860/mythbackend   
udp        0      0 0.0.0.0:6549            0.0.0.0:*                          17860/mythbackend   
udp        0      0 255.255.255.255:1900    0.0.0.0:*                          17860/mythbackend   
udp        0      0 239.255.255.250:1900    0.0.0.0:*                          17860/mythbackend   
unix  2      [ ACC ]     STREAM     LISTENING     15300    4508/mysqld         /var/run/mysqld/mysqld.sock

[root@mythtv-be-01:T1:L2:C585:J0:2008-01-04_16:50:06_EST]
/root/myth-revert# netstat -lnp | grep -i '/my'
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     4508/mysqld         
unix  2      [ ACC ]     STREAM     LISTENING     15300    4508/mysqld         /var/run/mysqld/mysqld.sock


So I reverted to my daily DB (mysqldump) backup, and THAT didn't work either!  It lasted a little longer than the others, but the daemons are still dieing!

Can anyone help?

---

### Post by mossholderm on 2008-01-04
Hey JP...

First, make sure that all your tables are intact... there is a script in     
 /usr/share/doc/mythtv-backend/contrib named optimize_db.pl which will take care of that for you.


If that doesn't work, perhaps you might want to try backing up your mythconverg DB, dropping the DB, and letting it recreate it. Just as a troubleshooting aid, not as a fix. If the new DB seems to work fine, you can start looking for differences in table structure, etc.

   Regards,
         --Matt

---

### Post by jpv on 2008-01-04
No dice on the first idea.  I ran it and it seemed fine, but the backend only worked for a few minutes, then just died again...

[INDENT][mythtvuser@mythtv-be-01:T1:L1:C514:J0:2008-01-04_18:15:53_EST]
/home/mythtvuser/db_dumps$ perl /usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl   
Repaired/Optimized: `mythconverg`.`archiveitems`
Repaired/Optimized: `mythconverg`.`callsignnetworkmap`
Repaired/Optimized: `mythconverg`.`capturecard`
[...]
Repaired/Optimized: `mythconverg`.`videosource`
Repaired/Optimized: `mythconverg`.`videotypes`
Repaired/Optimized: `mythconverg`.`websites`
[/INDENT]


As for the second, I dropped the table and restored it from a 04:00 backup a bit ago, but that had no effect either. I've been going on the assumption that my "upgrade" did something bad, since it's been working flawlessly since the install, including the morning. I have daily and weekly backups of the DB so I can revert back for a while if that seems useful.

I'm willing to try dropping and rebuilding from scratch, what's the best way?  Drop it and use the optimize script?  Or the GUI config tool?

Thanks!

---

### Post by superm1 on 2008-01-04
Regarding the always upgrading of ubuntu-mythtv-frontend, please see [https://bugs.edge.launchpad.net/mythbuntu/+bug/165230](https://bugs.edge.launchpad.net/mythbuntu/+bug/165230)

---

### Post by mossholderm on 2008-01-04
> **jpv said:**
> 
I'm willing to try dropping and rebuilding from scratch, what's the best way?  Drop it and use the optimize script?  Or the GUI config tool?
Thanks!

If you drop the DB, and reinstall the mythtv-database package, it should lay down a new DB for you (apt-get install --reinstall mythtv-database). That, or you can use the .sql file in 
/usr/share/mythtv/sql  to do it without reinstalling.

---

### Post by jpv on 2008-01-05
re: superm1 xfre, yes, that looks like it, thanks.

re: dropping and reinstalling mythtv-database, I tried, but no luck, it still crashed.

I'm beginning to think it's not related to the update or Myth in and of itself at all, but at this point I have no idea what else it could be.  Hardware *seems* fine and is decent server-class stuff.  Nothing obvious in other logs, and Postfix, MySQL, SSH, and Apache have all been rock-solid.  (This is a dedicated Myth BE, but does run MythWeb and I have postfix for cron messages.)

What's really killing me is that mythbackend just goes away with no warning, log, or anything else I can find.  One second it's there, the next it's gone.  I thought maybe a corrupted client was killing it, so I started it and just let it sit there--it still died.  I've tried the local FE, a remote FE and a MediaMVP running mvpmc = no change.

I even tried running this, to monitor it, but it didn't tell me anything I didn't already know, one second it's there, the next it's gone:
[INDENT]# while [ 1 = 1 ]; do echo -e "\n\n" ; date ; ps vww $(cat /var/run/mythtv/mythbackend.pid) ; echo -e "\n" ; netstat -lnp | grep -i '/my' ; sleep 2 ; done | tee -a log
[/INDENT]

---

### Post by jpv on 2008-01-05
I've tried a bunch more things:

1) "rm /usr/bin/myth*" then reinstall of the *_0.20.2+fixes14681-*.debs

2) I noticed an /etc/init.d/mythtv-backend.dpkg-dist, so I switched to using that.  That *almost* looked like it worked, it stayed up for a few minutes this time.

3) Probably lots of other stuff I forget, like brand new empty DBs and various versions of my DB backups.

The only thing else I noticed is a bunch of these in /var/log/mythtv/mythbackend.log

[INDENT]ASSERT: "it.node != node" in /usr/include/qt3/qvaluelist.h (301)[/INDENT]

And once when running manually I got:
[INDENT]ASSERT: "it.node != node" in /usr/include/qt3/qvaluelist.h (301)
Segmentation fault (core dumped)[/INDENT]

Any thoughts?

---

### Post by superm1 on 2008-01-05
Have you already ran through some tests upon your memory to make sure its not going bad?

Transient issues like this tend to point at things of that nature.

---

### Post by mossholderm on 2008-01-05
I agree with superm1 ... seg faults are a good sign there is something wrong memory wise. All the other apps on the backend are fairly light on memory, so it isn't too surprising that you haven't seen them hit the theoretical bad address yet.

         --Matt

---

### Post by jpv on 2008-01-05
Memtest86+ v1.70 from the Mythbuntu grub boot menu completed 3 passes with 0 errors.

I'm setting up for a full rebuild, as this is getting really annoying.  I'd love to figure out the problem and fix it properly, but I'm getting to the point where I just want it to work again and I don't care how.

Any other thoughts or ideas, esp. on how best to rebuild without nuking 300G of recordings?  (I'll be doing a backup, of course...)

---

### Post by WhyWontThisWork on 2008-01-06
is it save to run the updates that ubuntu pushes down? i just got my system all up and running and I don't want to mess anything up.  I know with some similar programs like mythdora they say to not upgrade a thing so is it safe to update and what real advantages are there? (yeah, thats probably not the right thing to post)
thanks
-J

---

### Post by superm1 on 2008-01-06
> **WhyWontThisWork said:**
> is it save to run the updates that ubuntu pushes down? i just got my system all up and running and I don't want to mess anything up.  I know with some similar programs like mythdora they say to not upgrade a thing so is it safe to update and what real advantages are there? (yeah, thats probably not the right thing to post)
thanks
-J
Generally it should be safe.  I keep all my boxes up to date and don't run into issues very often.

---

### Post by jpv on 2008-01-06
WhyWontThisWork, I've been doing updates since my original install (fall 2007) with no problems until now.  I installed from a beta CD, and had some stuff in my sources.list maybe I shouldn't have though.  I think production updates on a production install are probably a safe bet.

---

### Post by jpv on 2008-01-06
I'm not convinced this is either a MythTV or Mythbuntu or an update problem, I just want to figure it out and fix it.  Having said that, as far as I can tell it *did* start happening right after an update. :-(

Thus far nothing I've tried has help, which is really frustrating.  The most recent thing was a fresh install into a different machine (in a VM), then a copy of everything over to the old machine.  I did that instead of a complete fresh install because I have only one partition and the installer wants to format that, so I was trying to avoid a 300G backup/restore session.

It *seems* like I get the following right before the crash, and as far as I can tell this started happening right around the time of the update:
[INDENT]"ASSERT: "it.node != node" in /usr/include/qt3/qvaluelist.h (301)"[/INDENT]

I don't have a "/usr/include/qt3" dir on my old or my new (VM) install so I assume that's a compile-time requirement though I also wonder why the backend would need anything QT GUI related.

Here's the time line and details:

2008-01-04:
[LIST]
[*]Upgrade machine = now mythbackend crashes [1]
[*]	Revert to older debs
[*]	perl /usr/share/doc/mythtv-backend/contrib/optimize_db.pl
[*]	Revert to older DB
[/LIST]

2008-01-05:
[LIST]
[*]Memtest86+ v1.70 from the Mythbuntu grub boot menu completed 3 passes with 0 errors.
[*]	New install and file copy [2]
[*]	Fixed ownership problems (ntp --> mythtv) on various myth files and dirs
[*]		Probably caused by previous file copy?
[/LIST]

2008-01-06 (TODO after posting this):
[LIST]
[*]Research "ASSERT: "it.node != node" in /usr/include/qt3/qvaluelist.h" message
[*]	Backup and full reinstall :-(
[*]	Swap hard drive into replacement machine
[/LIST]
_________________________________________
Footnotes

[1] Upgrade machine = now mythbackend crashes

I nuked my /var/log/aptitude log in the file copy [2], but I started this thread (January 5th, 2008 03:15 PM EST) an hor or two after I did the upgrade that *seems* to have broken everything.

# When are the logs for?
$ ll /var/log/mythtv/mythbackend.log*               
-rw-r--r-- 1 mythtv mythtv      0 2008-01-06 06:27 /var/log/mythtv/mythbackend.log
-rw-r--r-- 1 mythtv mythtv 325023 2008-01-06 06:27 /var/log/mythtv/mythbackend.log.1
-rw-r--r-- 1 mythtv mythtv  74993 2008-01-05 06:25 /var/log/mythtv/mythbackend.log.2
-rw-r--r-- 1 mythtv mythtv  41198 2008-01-04 06:25 /var/log/mythtv/mythbackend.log.3
-rw-r--r-- 1 mythtv mythtv  15278 2008-01-03 06:25 /var/log/mythtv/mythbackend.log.4
-rw-r--r-- 1 mythtv mythtv   1084 2008-01-02 06:25 /var/log/mythtv/mythbackend.log.5
-rw-r--r-- 1 mythtv mythtv  26451 2008-01-01 09:05 /var/log/mythtv/mythbackend.log.6
-rw-r--r-- 1 mythtv mythtv  19105 2007-12-31 09:05 /var/log/mythtv/mythbackend.log.7

# When did the "ASSERT" error start showing up?
$ grep -c '^ASSERT' /var/log/mythtv/mythbackend.log*        
/var/log/mythtv/mythbackend.log:0
/var/log/mythtv/mythbackend.log.1:5
/var/log/mythtv/mythbackend.log.2:20
/var/log/mythtv/mythbackend.log.3:0
/var/log/mythtv/mythbackend.log.4:0
/var/log/mythtv/mythbackend.log.5:0
/var/log/mythtv/mythbackend.log.6:0
/var/log/mythtv/mythbackend.log.7:0


# OK, that's *right* before/during/after the upgrade, what's the first one look like
$ grep -B8 '^ASSERT' /var/log/mythtv/mythbackend.log.2 | head 
2008-01-04 12:34:17.732 Unknown socket closing
2008-01-04 12:37:48.599 Unknown socket closing
2008-01-04 12:40:55.443 MainServer::HandleAnnounce Monitor
2008-01-04 12:40:55.448 adding: foster-host as a client (events: 0)
2008-01-04 12:40:55.450 MainServer::HandleAnnounce Monitor
2008-01-04 12:40:55.452 adding: foster-host as a client (events: 1)
2008-01-04 12:41:03.873 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 2
2008-01-04 12:41:18.943 Unknown socket closing
ASSERT: "it.node != node" in /usr/include/qt3/qvaluelist.h (301)
--



[2] New install and file copy

x svnsync & svn checkin
x Build new machine in VMware
x Update new machine
x Boot old machine in a LiveCD
x Mount filesystem in LiveCD:/mnt/myth
[INDENT]	sudo bash
	cd /mnt
	mkdir myth
	mount /dev/sda1 myth[/INDENT]
x Can't mv /mnt/myth/etc/ /mnt/myth/etc.old as that will mess up SVN
[INDENT]	cp -a /mnt/myth/etc  /mnt/myth/etc.old
	cp -a /mnt/myth/boot /mnt/myth/boot.old
	find /mnt/myth/etc/ -type f -print0 | grep -v '\.svn' | xargs -0 rm
	find /mnt/myth/boot/ -type f -print0 | grep -v '\.svn' | xargs -0 rm[/INDENT]
x Rsync new machine on top of old machine [i]
x Fix some files
[INDENT]	cd /mnt/myth/boot/grub
	cp -av /mnt/myth/boot.old/grub/menu.lst
	cd /mnt/myth/etc.old
	cp -av fstab passwd group shadow /mnt/myth/etc
	cd /mnt/myth/etc/X11
	mv xorg.conf xorg.conf.NEW.vmware_busted
	cp /mnt/myth/etc.old/X11/xorg.conf .[/INDENT]
x Reboot into new machine
x Reinstall stuff:
sudo aptitude install tftpd unzip zip build-essential postfix mailx logcheck logcheck-database subversion localepurge libcrypt-ssleay-perl mythtv-themes deborphan
x Reconcile SVN status
x Import a DB backup
x Reboot and test = FAILED!

[i] rsync --archive --numeric-ids --verbose \
  --exclude '/cdrom' \
  --exclude '/dev' \
  --exclude '/lost+found' \
  --exclude '/media' \
  --exclude '/mnt' \
  --exclude '/opt' \
  --exclude '/proc' \
  --exclude '/sys' \
  --exclude '/tmp' \
  root@192.168.99.177:/ /mnt/myth

---

### Post by jpv on 2008-01-07
EDITED: this was self-inflicted and NOT a MythTV, Mythbuntu or update problem!!!

The problem turned out to be that--right around the same time I did the update--I also added some monitoring via the excellent Monit package.  But I was too clever for my own good and the Monit packets were killing Myth.  BUT, it would only happen on a Monit polling cycle, so from my perspective it would happen at "random" times!  And of course I forgot all about that minor little tweak, as I was doing a bunch of things at once...  "What else changed in the environment?"  "Why nothing..."  AARRGGHH!!!

---

### Post by superm1 on 2008-01-07
I'm glad that you were finally able to sort this out, but did you see any indications as to why monit was killing if in the first place? You most likely are not the first one to have a desire to use it for stability reasons.

---

### Post by jpv on 2008-01-12
No clue what was happening, but I've opened an upstream bug at [http://cvs.mythtv.org/trac/ticket/4460](http://cvs.mythtv.org/trac/ticket/4460) and referenced that bug in Mythbuntu bug [https://bugs.launchpad.net/mythbuntu/+bug/182212](https://bugs.launchpad.net/mythbuntu/+bug/182212)

---

### Post by DavidWhyte on 2008-01-12
This has been a known issue for a while.  I have marked the upstream bug as a duplicate of the original bug, which has been closed and should make it into 0.21. Can the mythbuntu bug please get updated accordingly?

Cheers,
Whytey

---

### Post by WhyWontThisWork on 2008-01-12
I think they are the same files however there are a few edits to get rid of extra stuff and add the mythtv files, any idea as to when the update will be released?

---

### Post by superm1 on 2008-01-12
Tomorrow should be next weekly build.

---

### Post by WhyWontThisWork on 2008-01-12
ok... so that will be released in the normal updates then or do I have to go to a CVS and get it or anything special?

---

### Post by superm1 on 2008-01-12
> **WhyWontThisWork said:**
> ok... so that will be released in the normal updates then or do I have to go to a CVS and get it or anything special?

As long as you are using the trunk repository, it should pull this stuff in on its own.

---

### Post by WhyWontThisWork on 2008-01-12
whatever the default is.....

---

### Post by superm1 on 2008-01-12
Weekly builds are described here:

[http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

---

