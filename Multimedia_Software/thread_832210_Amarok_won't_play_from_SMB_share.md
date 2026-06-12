---
title: "Amarok won't play from SMB share"
date: 2008-06-17
forum: Multimedia Software
---

### Post by jcr1 on 2008-06-17
Hi all,

Just got a server up and running at home. On it there is some music. 

From another machine, my laptop, I am trying to play some music thru amarokk from this server. 

I get:

Error Loading Media
No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.

This is weird as I can browse thru Nautilus to that folder and if I just double click on the same music file it opens Totem and starts playing no problem.

How do I make Amarok use this file server location?

---

### Post by jcr1 on 2008-06-18
bump

---

### Post by jcr1 on 2008-06-23
bump

---

### Post by veedub on 2008-06-23
make sure that smbfs is installed.  Then you need to mount the volume as a drive in /etc/fstab.  Here is my fstab that works on my "Music" drive 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 /media/vista ntfs ro,uid=1000,auto 0 0
**//192.168.1.150/Music /media/music cifs uid=1000,auto 0 0**

Edit the following items to mach your config:

//192.168.1.150/Music is the location of your SMB share
/media/music is the directory were you want to mount your SMB share on your linux machine.

---

### Post by jcr1 on 2008-06-24
So are you saying I need to have a seperate mount location for amarok? I already have the drive mounted just for simple file access.

BAsically I have the home directory of my server mounted on my laptop, within the home directory on the server is a 'link' folder which is pointing to a second larger hard drive for storage. I put all my music in a folder in that linked big hhd folder.

---

### Post by veedub on 2008-06-24
If the drive is already mounted, simply add the folder to the library under amarok's configuration menu.  (settings->Configure Amarok->Collection)

---

### Post by jcr1 on 2008-06-25
Got it.

Not sure what I was doing wrong before, but I went through my samba share set up again and now its all working sweet!

Think the only complication was that the music is located on a hdd which is mounted onto another on the server, which is then shared to my laptop! 

All working now though, Thanks!

---

