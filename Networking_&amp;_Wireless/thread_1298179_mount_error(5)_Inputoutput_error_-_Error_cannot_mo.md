---
title: "mount error(5): Input/output error - Error: cannot mount filesystem: Protocol error"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by iMisspell on 2009-10-22
[edit]
Problem solved by commenting out **force group = *desired_group*** in the samba config file.
[/edit]


Been search google for a day or so and can not find a solution...

Can not mount any server shares (two dirs) via /etc/fstab:
Receive the following error:
```
	mount error(5): Input/output error
	Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
	mount error(5): Input/output error
	Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
	Error: cannot mount filesystem: Protocol error
```

Command being used in 'fstab'

```
//192.168.0.80/www /myMounts/machine_name/www cifs credentials=/myMounts/.pw/file_name,iocharset=utf8,uid=1000,gid=1000,file_mode=0771,dir_mode=0771 0 0

//192.168.0.80/all /myMounts/machine_name/all cifs credentials=/myMounts/.pw/file_name,iocharset=utf8,uid=1000,gid=1000,file_mode=0771,dir_mode=0771 0 0
```

Both of those commands where being used connecting to a 9.04 server i set up about two weeks ago and they worked fine, only difference was for the 9.04 i was not using 'iocharset=utf8' which seamed to make no difference on 8.04.


GUI, if i go to 'smb://workgroup/' > 'machinename' i can see the two folders there but when i double click to enter them 'nautilus' tries to open the folders as if they where files and i receive the following error in 'gedit':
```
	Could not open the file smb://**machine_name**/www/.
	Unexpected error: Invalid argument
```


Heres the full proccess which i have taken...
Did a fresh install of Ubuntu 8.04 server (about three days ago).
During the install the only packages i choose to install was the Samba Server and Openssh.

After the install was done and the server was up and running i did the following through SSH.

```
sudo aptitude update && sudo aptitude full-upgrade
aptitude-cache policy ssh
sudo aptitude install apache2 php5 libapache2-mod-php5
sudo aptitude install apache2-dev
sudo aptitude install openssh-server
sudo aptitude install php5-dev
sudo aptitude install php-pear
  ** tested http server, all is well **
sudo nano /etc/samba/smb.conf ** edits posted below **
sudo  smbpasswd -a *username*
  ** - tried to mount dirs - did not work **
sudo aptitude install samba
sudo aptitude install smbfs
sudo nano /etc/samba/smb.conf ** double check, all is the same
  ** - tried to mount dirs - did not work **
id *username*
sudo chown -hR root:*desired_group* /var/www/
sudo aptitude install keyutils
hostname
hostname -a
  ** both printed correct machine name **
sudo aptitude install samba smbfs smbclient
  ** - tried to mount dirs - did not work **
sudo chmod -R 775 /all/
sudo chmod -R 775 /var/www/
  ** - tried to mount dirs - did not work **
```



smb.conf edits (this was a copy/paste from the 9.04 which was working how i wanted, did a few small changes for testing in 8.04)...
```
[global]
   netbios name = mahine_name # added this...

[www]
comment = ...
path = /var/www/
read only = no
writeable = yes
create mask = 0664
force create mode = 0664
security mask = 0664
force security mode = 0664
directory mask = 0775
force directory mode = 0775
directory security mask = 0775
force directory security mode = 0775
inherit owner = yes
force group = *desired_group*
locking = no
guest ok = yes # in 9.04 this was NO, which is what i want in 8.04, only reason its YES is for testing
browseable = yes # in 9.04 this was NO, which is what i want in 8.04, only reason its YES is for testing
available = yes 
valid users = *user_name*

[all]
comment = ...
path = /all/
read only = no
writeable = yes
create mask = 664
force create mode = 664
security mask = 664
force security mode = 664
directory mask = 2775
force directory mode = 2775
directory security mask = 2775
force directory security mode = 2775
inherit owner = yes
force group = *desired_group*
locking = no
guest ok = yes  # in 9.04 this was NO, which is what i want in 8.04, only reason its YES is for testing
browseable = yes # in 9.04 this was NO, which is what i want in 8.04, only reason its YES is for testing
valid users = *user_name*
```

When changing the '*guest ok =*' to 'no' i receive the same error in 'fstab' as posted above and with 'nautilus' it still tries to open the folder as a file and 'gedit' will error with '*You do not have the permissions necessary to open the file.*' which seams to make sence because the client im tring to view the folder with is not added to the servers 'user-list'.

Added the curent clients to the server, add that same user to 'sudo  smbpasswd -a *new_user*', restarted samba, tried to view folder again with 'nautilus' and received the orginal error as posted above; "Unexpected error: Invalid argument"


Any help with this problem would be great.
Im doing all the server changes via SSH and im new to commandlines so if you could please give detailed replies on commands to try.

Im off to work right now, will check back when i get home tonight.

Thanks for any help.


_

---

### Post by iMisspell on 2009-10-23
While trying to research this problem i was using the error messages which i was receiving from the ubuntu-desktop, just seached out the error message windows was giving *"The group name could not be found"* which brought me to the thread below...
[http://ubuntuforums.org/showpost.php?p=5391130&postcount=2](http://ubuntuforums.org/showpost.php?p=5391130&postcount=2)

commenting out
*_force group = *desired_group*_*
in the samba config file solved the problem.

hope this helps someone else.
_

---

