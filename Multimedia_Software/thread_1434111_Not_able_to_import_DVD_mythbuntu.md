---
title: "Not able to import DVD mythbuntu"
date: 2010-03-19
forum: Multimedia Software
---

### Post by wembleyboy on 2010-03-19
My first post here on Ubuntu to be gentle....;)

I have been using Ubuntu for the last month and everyone in my uses it loves it !!!!!!

In fact not turned on my Windoze machine for over month....!!!!

My question is in fact about Mythbuntu which I am slowly getting up and running. 

I have been trying to rip the dvd office space without much scucess. 

I am able to play dvds.....:o

I have all the codes installed libdvdcss2 and ffmpeg. 

I was having an issues with getting a split screen ....that was when playing the movie. 

that was resolved by changing the setting  current Video playback to > High Quality. (If you want to change it is hidden away in utilities/setup > setup > tv settings > playback > select next twice and the setting is the first option on the page.)

When i try to import a DVD i get the following error message. 

ISO Copy of unknown

No job and nothing else to do . You could rip a DVD. 

Waiting for access to DVD 

Please see attached screen shot is attached. 

I have run the command 

ls -l /dev/dvd* 
lrwxrwxrwx 1 root root 3 2010-03-19 21:38 /dev/dvd -> sr0
lrwxrwxrwx 1 root root 3 2010-03-19 21:38 /dev/dvdrw -> sr0

And then have tried both dvdrw and dvd in the Location of DVD Device, that still did not help. 

I have also run the mount command but not able to make much sense of it 

chan@chan-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755

I have ran mtd -n which i have listed below 

chan@chan-desktop:~$ mtd -n
2010-03-20 01:40:33.448 Using runtime prefix = /usr
2010-03-20 01:40:33.448 Using configuration directory = /home/chan/.mythtv
2010-03-20 01:40:33.448 Empty LocalHostName.
2010-03-20 01:40:33.449 Using localhost value of chan-desktop
2010-03-20 01:40:33.456 New DB connection, total: 1
2010-03-20 01:40:33.460 Connected to database 'mythconverg' at host: localhost
2010-03-20 01:40:33.460 Closing DB connection named 'DBManager0'
2010-03-20 01:40:33.461 Connected to database 'mythconverg' at host: localhost
2010-03-20 01:40:33.465 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1028
2010-03-20 01:40:33.470 MTD, Error: Can't bind to server port 2442
            There is probably copy of mtd already running.
            You can verify this by running 'ps ax | grep mtd'.
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.

On the advise of the output above  I ran the following 

chan@chan-desktop:~$ ps ax | grep mtd
 1967 ?        SNsl   0:04 /usr/bin/mtd -d
 5036 pts/0    S+     0:00 grep --color=auto mtd

I have checked the MTD settings are they are 2442

Hope you can help !!!!!

Thanks

---

