---
title: "guide freezes - unable to save icons"
date: 2009-11-07
forum: Mythbuntu
---

### Post by linuxgrrl on 2009-11-07
hello,
Last night I did a clean install of 9.10 RC1.  It seems to be running mostly fine, however, when I enter the guide from Schedule Recordings, my hard disk starts churning and I get error messages in mythfrontend.log such as:
```
2009-11-07 14:11:17.238 Failed to save to /home/mary/.mythtv/channels/universal_sports.jpg
2009-11-07 14:11:17.921 Failed to save to /home/mary/.mythtv/channels/whut_washington.jpg
2009-11-07 14:11:18.604 Failed to save to /home/mary/.mythtv/channels/wrc_washington.jpg
2009-11-07 14:11:19.304 Failed to save to /home/mary/.mythtv/channels/wrc_washington.jpg
```

Yet I've tried to fix the permissions, they now look like this:
```
mary@mythbox:~$ ls -la /home/mary/.mythtv/
total 64
drwxrwxrwx  6 mary mythtv  4096 2009-11-06 22:03 .
drwxr-xr-x 26 mary mary    4096 2009-11-07 14:06 ..
drwxrwxrwx  2 mary mythtv  4096 2009-11-06 22:03 channels
-rw-rwxrwx  1 mary mythtv   422 2009-11-07 14:06 config.xml
lrwxrwxrwx  1 root root      15 2009-11-06 21:08 lircrc -> ../.lirc/mythtv
lrwxrwxrwx  1 root root      21 2009-11-06 21:08 mysql.txt -> /etc/mythtv/mysql.txt
drwxrwxrwx 10 mary mythtv  4096 2009-11-06 22:00 MythWeather
drwxrwxrwx  2 mary mythtv 36864 2009-11-07 14:11 osdcache
drwxrwxrwx  3 mary mythtv  4096 2009-11-07 14:11 themecache

```
What am I doing wrong?  I think it must still be the permissions somehow.  To get to the above result I did "chgrp mythtv /home/mary/.mythtv/*" and "chmod ugo=rwx /home/mary/.mythtv/channels".

thanks
Mary

---

