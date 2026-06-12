---
title: "Samba share"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by kpgalligan on 2009-05-06
I know this is a simple problem, but its getting pretty frustrating and I'm hoping somebody can point me in the right direction.  I have a network shared drive (thecus 2100).  It has a windows share.  I can connect to that in Gnome from Nautilus.  No problem.  When I try mount a directory, however, problems.  I need to mount it directly because my apps can't use the connection set up in Nautilus (which, by the way, I think should be changed).  However, when I mount the directory, I can browse it and see the files, but can't access them in any way.

I tried the steps here...

[https://help.ubuntu.com/community/SettingUpSamba#Samba%20Client%20Manual%20Configuration](https://help.ubuntu.com/community/SettingUpSamba#Samba%20Client%20Manual%20Configuration)

Look under "CIFS".  The 'sudo mount' part worked fine.  I can access the drive and see files, but again, I tried to copy and paste a file into a local drive, and it failed.

Thoughts?

---

### Post by tricolorpoa on 2009-05-06
May be you do not have permission to write in those share...

---

### Post by kpgalligan on 2009-05-06
> **tricolorpoa said:**
> May be you do not have permission to write in those share...

Just trying to read from.  Write local (in my home drive).

---

### Post by albinootje on 2009-05-06
> **kpgalligan said:**
> I can access the drive and see files, but again, I tried to copy and paste a file into a local drive, and it failed.
Can you post the output of :
```

dmesg | tail -n10
tail -f /var/log/syslog
ls -latr /var/log/samba/|tail -n10

```

---

### Post by kpgalligan on 2009-05-06
```

kevin@kevin-ubuntu-hp:~$ dmesg | tail -n 10
[23364.886510] Status code returned 0xc0000022 NT_STATUS_ACCESS_DENIED
[23364.886518]  CIFS VFS: Send error in read = -13
[23364.894052] Status code returned 0xc0000022 NT_STATUS_ACCESS_DENIED
[23364.894064]  CIFS VFS: Send error in read = -13
[23364.894510] Status code returned 0xc0000022 NT_STATUS_ACCESS_DENIED
[23364.894519]  CIFS VFS: Send error in read = -13
[23376.016317] Status code returned 0xc0000022 NT_STATUS_ACCESS_DENIED
[23376.016328]  CIFS VFS: Send error in read = -13
[23376.017018] Status code returned 0xc0000022 NT_STATUS_ACCESS_DENIED
[23376.017026]  CIFS VFS: Send error in read = -13
kevin@kevin-ubuntu-hp:~$ tail -n 10 /var/log/syslog
May  6 18:20:01 kevin-ubuntu-hp /USR/SBIN/CRON[5701]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
May  6 18:25:01 kevin-ubuntu-hp /USR/SBIN/CRON[5891]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
May  6 18:30:01 kevin-ubuntu-hp /USR/SBIN/CRON[5984]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  6 18:30:01 kevin-ubuntu-hp /USR/SBIN/CRON[5985]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
May  6 18:35:01 kevin-ubuntu-hp /USR/SBIN/CRON[6214]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
May  6 18:40:01 kevin-ubuntu-hp /USR/SBIN/CRON[6323]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
May  6 18:40:01 kevin-ubuntu-hp /USR/SBIN/CRON[6324]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  6 18:45:01 kevin-ubuntu-hp /USR/SBIN/CRON[6528]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
May  6 18:50:02 kevin-ubuntu-hp /USR/SBIN/CRON[6693]: (root) CMD (if [ -x /usr/bin/vnstat ] && [ `ls /var/lib/vnstat/ | wc -l` -ge 1 ]; then /usr/bin/vnstat -u; fi)
May  6 18:50:02 kevin-ubuntu-hp /USR/SBIN/CRON[6695]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
kevin@kevin-ubuntu-hp:~$ ls -latr /var/log/samba/ | tail -n 10
-rw-r--r--  1 root root  309 2009-03-21 08:41 log.winbindd.7.gz
-rw-r--r--  1 root root  403 2009-03-29 09:03 log.winbindd.6.gz
-rw-r--r--  1 root root  425 2009-04-05 09:43 log.winbindd.5.gz
-rw-r--r--  1 root root  377 2009-04-12 08:49 log.winbindd.4.gz
-rw-r--r--  1 root root  373 2009-04-18 13:55 log.winbindd.3.gz
-rw-r--r--  1 root root  413 2009-04-26 08:48 log.winbindd.2.gz
-rw-r--r--  1 root root  429 2009-05-03 02:27 log.winbindd.1.gz
drwxr-x---  3 root adm  4096 2009-05-03 03:06 .
-rw-r--r--  1 root root 2826 2009-05-06 08:12 log.winbindd
drwxr-xr-x 15 root root 4096 2009-05-06 08:13 ..
kevin@kevin-ubuntu-hp:~$ 


```

---

### Post by albinootje on 2009-05-06
> **kpgalligan said:**
> ```

kevin@kevin-ubuntu-hp:~$ dmesg | tail -n 10
[23364.886510] Status code returned 0xc0000022 NT_STATUS_ACCESS_DENIED
[23364.886518]  CIFS VFS: Send error in read = -13

```


Thanks. See here :
[http://ubuntuforums.org/showthread.php?t=1048482](http://ubuntuforums.org/showthread.php?t=1048482)
which points to here :
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
which mentions this :
> 
******HARDY USERS******
Mount error 13. If you are seeing "mount error 13 = Permission denied" error ("CIFS VFS: cifs_mount failed w/return code = -13" in dmesg) when entering the "sudo mount -a" command, add the nounix option like so:
```

//netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```
thanks to TonyS for posting this solution here: [http://ubuntuforums.org/showthread.php?t=800313](http://ubuntuforums.org/showthread.php?t=800313)

This might help. Can you test that ?

---

