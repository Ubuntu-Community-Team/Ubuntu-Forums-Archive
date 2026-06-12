---
title: "Cron Issue When Trying to Sync with a Network Drive?"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by csharpplus on 2010-10-25
Cron refuses to work when trying to sync with a network drive. Any chance you guys can help a newbie?

I am trying to setup a cron job to backup a folder in my home directory  ('/home/scratch') to a folder ('home/internet_backup') that is mounted  (using nfs) to a network folder.

the folder ('home/internet_backup') is mounted correctly to the network folder upon system startup, so this part works.

I created a simple bash file (rsync-shell.1.sh) that looks like this:

     Code:
     # backup the contents of 'scratch' (of 'internet' machine) into '/home/aa/internet_backup/'
# the latter folder ('/home/aa/internet_backup/') is mounted to 'developer' machine
rsync -av --exclude=".*" /home/aa/scratch /home/aa/internet_backup/
# 
when manually running this bash file from my home directory  (./rsync-shell.1.sh) everything works, and the contents are written to  the destination folder.

Yet, instead of running this manually, I wanted this to be executed by  Cron every 30 min. so I first chmod +x this file, and then copied it  (using sudo) to /root.

I then created the following using 'sudo crontab -e':

     Code:
     # m h  dom mon dow   command
10       *       *       *       *       /root/rsync-shell.1.sh 
 This is the same bash file illustrated above, yet, it doesn't work (files are not being written to the destination folder).

What am I missing here?  thanks in advance for any help.

---

### Post by drdos2006 on 2010-10-26
Server software on one machine, client software on the other.
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

Addendum:	On the Server machine
Needed to add Group of users on the machine designated as the server. Added the group via Webmin. If Webmin not an option then use terminal on the Server machine: 
sudo addgroup MyGroupName	
Added /media/sharedfiles on server with :	
sudo mkdir  /media/sdb1/sdb1-shared
Needed to change group permissions for /media/sdb1/sdb1-shared:	
sudo chgrp MyGroupName  /media/sdb1/sdb1-shared
//**
On the Client machine: Created a directory of /media/sharedfiles with : sudo mkdir /media/sharedfiles, mounted /media/sharedfiles from terminal as /media/sharedfiles with : 
sudo mount  <serverIPaddress>:/media/sdb1/sdb1-shared   /media/sharedfiles 
Can also be added to /etc/fstab for automatic mounting.
Copied files as test and it worked.

You might find something in the HOWTO: to help you.

regards

---

### Post by csharpplus on 2010-10-26
Thanks you for your help.

---

