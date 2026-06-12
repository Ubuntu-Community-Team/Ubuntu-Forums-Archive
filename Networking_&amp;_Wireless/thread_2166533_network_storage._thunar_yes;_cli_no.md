---
title: "network storage. thunar: yes; cli: no"
date: 2013-08-09
forum: Networking &amp; Wireless
---

### Post by JohnnyC35 on 2013-08-09
I am trying to access files on my one computer (MEDIA01) from my main computer (HOME). Both have Xubuntu. I can access the files from Thunar (smb://media01/storage/) but I am trying to run a bash script from it and I can't seem to to get executable files to run. I thought maybe if I can get it to mount via the command line I could do it that way. Also going through this I noticed I cannot mount MEDIA01 via fstab.

the errors I get with mount and fstab are:
$sudo mount -t cifs //192.168.1.129/storage /media/share01 -o user=john,password=password,rw,sec=ntlm --verbose

**Unable to find suitable address.**

MEDIA01 is 192.168.1.129, I double checked and made it static.

From what I have found some people have found sec=ntlm gets things to work somehow. With or without it does nothing for me.

running: 'pgrep -l mbd' lists
[B]7574 smbd
7609 smbd
7610 nmbd[/B]

typing: sudo restart nmbd  sudo restart smbd gives me
[B]snmbd start/running, process 8544
smbd start/running, process 8554[/B]

I have tried reinstalling samba and cifs but there is no change.

the log.nmbd is as follows:
```

[2013/08/04 16:41:59.164045,  0] nmbd/nmbd.c:66(terminate)
  Got SIGTERM: going down...
[2013/08/09 13:13:19,  0] nmbd/nmbd.c:861(main)
  nmbd version 3.6.9 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2013/08/09 13:13:43,  0] nmbd/nmbd_become_lmb.c:397(become_local_master_stage2)
  *****
  
  Samba name server HOME is now a local master browser for workgroup MEDIASHARE on subnet 192.168.1.139
  
  *****
[2013/08/09 20:54:35,  0] nmbd/nmbd.c:66(terminate)
  Got SIGTERM: going down...
[2013/08/09 20:54:50,  0] nmbd/nmbd.c:861(main)
  nmbd version 3.6.9 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2013/08/09 21:15:40,  0] nmbd/nmbd.c:66(terminate)
  Got SIGTERM: going down...
[2013/08/09 21:15:40,  0] nmbd/nmbd.c:861(main)
  nmbd version 3.6.9 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011
[2013/08/09 21:16:53,  0] nmbd/nmbd.c:66(terminate)
  Got SIGTERM: going down...
[2013/08/09 21:16:53,  0] nmbd/nmbd.c:861(main)
  nmbd version 3.6.9 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2011

```

Any thoughts as to where to go from here? Thanks :)

---

