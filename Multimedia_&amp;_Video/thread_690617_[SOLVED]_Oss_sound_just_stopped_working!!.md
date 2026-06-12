---
title: "[SOLVED] Oss sound just stopped working!!"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by bcn17 on 2008-02-07
My sound had been working fine, I was playing a couple songs in Amarok and then brought my  computer to my gf house. We started a movie and no sound. So I clicked my link that directs to ossxmix and nothing. ossxmix in terminal did nothing either. So i went to [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60]("http://ubuntuforums.org/showpost.php?p=3768914&postcount=60") which is Temüjin's HOW TO for oss. Here is what i did and got.
  
```
bar@barubuntu:~$ sudo aptitude purge remove oss-linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "remove".  However, the following
packages contain "remove" in their name:
  libfile-remove-perl claws-mail-attach-remover libapache2-mod-removeip 
  sylpheed-claws-gtk2-attach-remover 
The following packages will be REMOVED:
  oss-linux{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 7885kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 131027 files and directories currently installed.)
Removing oss-linux ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux (--purge):
 subprocess pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree        
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done      
```

```
 sudo apt-get install gcc gcc-4.1 gcc-4.1-base make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8
```

```
sudo dpkg -i oss-linux_v4.0-1013_amd64.deb
Selecting previously deselected package oss-linux.
(Reading database ... 131028 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1011 (using oss-linux_v4.0-1013_amd64.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1013_amd64.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux_v4.0-1013_amd64.deb
```
This is where I'm stuck, I tried it in normal gnome and failsafe terminal 
any help would be appreciated.

EDIT: I used [these]("http://www.4front-tech.com/forum/viewtopic.php?t=2054") directions to remove oss- I then followed the above directions exactly to reinstall oss. I am running 64 bit however and flash still didn't work after following addendum 2. So i found this page an rand the recommended link. It worked!

---

