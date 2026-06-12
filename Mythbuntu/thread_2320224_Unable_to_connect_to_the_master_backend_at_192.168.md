---
title: "Unable to connect to the master backend at 192.168.1.100:6543 (16.04 &amp; 0.28)"
date: 2016-04-11
forum: Mythbuntu
---

### Post by yonkiman on 2016-04-11
(This is a new thread for an issue I initially reported [here]("http://ubuntuforums.org/showthread.php?t=2319897&page=2&p=13468536#post13468536").)

I installed 16.04 beta 2 and Mythbuntu 0.28 and for the most part it's solid - can record and watch shows, etc.  But mythweb and mythtv-status are not working 100%.  I'll describe my mythtv-status problem, since I suspect that if I can fix that my mythweb connection issue will be fixed as well.

When I run mythtv-status, I get this:
> $ mythtv-status

MythTV status for localhost
===========================
Status...........: 2016-04-10 18:07:31
Total Disk Space.: Total space is 5.4 TB, with 4.6 TB used (85.2%)
Next Recording In: 35 Minutes

Scheduled Recordings:
2016-04-10 18:43:00 - Fear the Walking Dead (AMC HD (Pacific))
2016-04-10 20:00:00 - Madam Secretary (KIONDT (KION-DT))

Schedule Conflicts:
Unable to access MythTV Perl API. Try with --verbose to find out why.
When I try --verbose, I see what appears to be the same issue I have with mythweb:
> Failed to load Perl API
Couldn't communicate with 192.168.1.100 on port 6543: IO::Socket::INET::MythTV: connect: Connection refused
Any ideas why/how mythtv-status seems to be able to connect to the database for scheduled recordings but not for conflicts?  Not sure where to look next...

---

### Post by yonkiman on 2016-04-19
Fixed Mythweb after a long discussion [here]("http://www.gossamer-threads.com/lists/mythtv/users/598807#598807") (thanks Bill!).  Basically the network stack hadn't finished initializing before mythbackend started trying to get the machine's external IP address, so mythbackend never made the 6543 port available at 192.168.1.100 (my machine's external IP address).  Solution is to delay mythbackend starting until networking is initialized.  This is probably only a problem for faster SSD-based systems.

Short version of solution that worked for me:
[LIST][*]copy **/lib/systemd/system/mythtv-backend.service** to **/etc/systemd/system/**
[*]edit **/etc/systemd/system/mythtv-backend.service** and insert the line **ExecStartPre=/usr/bin/nm-online --quiet --timeout=5** above the existing **ExecStartPre=...** line.
[*]reboot[/LIST]
YMMV:  Read the last entry of [this thread]("http://www.gossamer-threads.com/lists/mythtv/users/598807#598807") for a much more detailed explanation.

Apparently mythtv-status has a bug (also seen in 15.10 I believe) breaking some functionality, but with mythweb working it's not a big deal.

---

### Post by carrucha2 on 2016-09-21
Thanks [**[COLOR=#000000]yonkiman[/COLOR]**]("https://ubuntuforums.org/member.php?u=482397"), exactly what I needed to fix my issue.

---

### Post by Frederico_Zenozzog on 2017-04-24
> **yonkiman said:**
> 
Short version of solution that worked for me:

... and for me. Thanks heaps; I had been struggling with a bunch of issues ever since moving to 16.04LTS and  mythtv 0.28, mostly to do with network and mysql not being accessible across the network. I'm using a slave backend as well. Here's a couple of other things I had to do to get it working:

**Fix mysql so it can be accessed from other clients:**
sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
# remark out the 
#bind-address = 127.0.0.1

and restart mysql

**...and I had to do this as well when one of the remote frontends had a hissy fit:**
[https://lists.gt.net/mythtv/users/598807#598807](https://lists.gt.net/mythtv/users/598807#598807)

add the following line to the end of /etc/mysql/mysql.conf.d/mysqld.cnf
sql_mode=NO_ENGINE_SUBSTITUTION


Cheers

---

### Post by johnfm3 on 2017-07-29
I have this same problem on a new install, and looking for a method to completely restart mythtv and sql install as if it was a new install.  I killed this install pretty bad.  I can not reinstall the OS as the system has a functioning PLEX media server running on it as well.

---

### Post by Frederico_Zenozzog on 2017-07-29
> **johnfm3 said:**
> a method to completely restart mythtv and sql install as if it was a new install. 

Here's what I did:
[LIST=1]
[*]Take a full backup - just in case. 
[*]sudo apt-get purge myth* - note that in my case purge did not delete associated files so I had to 
[*]Delete /home/mythtv/.mythtv (sudo rm -R /home/mythtv) 
[*]Delete /home/<you>/.mythtv 
[*]Delete /home/etc/mythtv 
[*]Delete /var/lib/mythtv (maybe first  back it up separately, especially if it contains media files you want to keep) 
[*]You could delete /var/log/mythtv as well, but probably not necessary 
[*]Run your mysql client,  BACKUP and then DROP the mythconverg database 
[/LIST]

Now re-install mythtv - 

I also had to do a bit of tweaking, some of it due to booting from an SSD (Seems self defeating to write scripts to slow the boot sequence down, doesn't it?); see my post here on April 25th 2017

---

