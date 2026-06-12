---
title: "Setting up proper security privileges for xbmc user"
date: 2013-04-30
forum: Multimedia Software
---

### Post by PeterTaps on 2013-04-30
Folks,

Background: I am running xbmc media center app on a Ubuntu 13.04 based system.

In order for user  "xbmc" to properly run "xbmc" application, the wiki says that the following must be done:

sudo polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.suspend 
sudo polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.hibernate
sudo polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.reboot
sudo polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.shutdown
sudo polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.reboot-multiple-sessions
sudo polkit-auth --user xbmc --grant org.freedesktop.hal.power-management.shutdown-multiple-sessions

However, polkit-auth is no longer available on Ubuntu. 

There are instructions to download polkit related deb packages and force-install them. But I do not wish to use any core package that is not part of the standard repository. 

I am looking for ways to add proper privileges to xbmc user without downloading polkit-auth.

A website suggested to do the following:

1. Create a security group called "xbmcg" and visudo to add permissions to run some applications without password.

$xbmcg ALL=NOPASSWD: /usr/bin/xbmc, /bin/mount, /bin/umount, /sbin/reboot, /sbiin/shutdown

2. Next, add user "xmbc" to a bunch of groups:

adduser xbmc xbmcg
adduser xbmc adm 
adduser xbmc dialout 
adduser xbmc cdrom 
adduser xbmc floppy 
adduser xbmc audio 
adduser xbmc dip 
adduser xbmc video 
adduser xbmc plugdev 
adduser xbmc fuse
adduser xbmc sudo


I am wondering if this strategy would work of if there is a better strategy.

How about I just add xmbc to admin group and just run "sudo xmbc?"

Thank you in advance for your help.

Regards,
Peter

---

