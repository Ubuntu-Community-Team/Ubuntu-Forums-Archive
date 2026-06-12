---
title: "Unable to connect to network share from 13.04, but works fine from 12.04"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by UltraAnders on 2013-06-15
I have an external HDD attached to my Raspberry Pi running Raspbmc. I can connect to it from my 12.04 desktop (after help from 2F4U [here]("http://ubuntuforums.org/showthread.php?t=2150506")).

I've tried the same process to connect to the share from my laptop running 13.04, so from /etc/fstab:
```
//raspbmc/seagate /media/rpSeagate cifs credentials=/home/ah/.smbcredentials,uid=ah,gid=users,iocharset=utf8,sec=ntlm 0 0
```
Username and password are in the file /home/ah/.smbcredentials. When I try to mount, I get the following error:
```
ah@ah-ThinkPad-X121e:~$ sudo mount -a
mount error(112): Host is down
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```I can ping the host (raspbmc) fine from the lappy. When I try access the share through nautilus, I get:
```
Unable to access location
Failed to mount Windows share: Connection timed out
```

I've tried:
[LIST]
[*]Installing winbind, cifs-utils, samba, samba-common, python-glade2, system-config-samba
[*]Editing /etc/nsswitch.conf with --> [FONT=Courier New]hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4[/FONT]
[*]Editing /etc/samba/smb.conf with --> [FONT=Courier New]name resolve order = wins bcast lmhosts host[/FONT] and also tried them in this order:[FONT=Courier New] lmhosts host wins bcast[/FONT]
[*]Using the ip address instead of the raspbmc, i.e. ```
//192.168.1.64/seagate /media/rpSeagate cifs credentials=/home/ah/.smbcredentials,uid=ah,gid=users,iocharset=utf8,sec=ntlm 0 0
```
[/LIST]
I'm stuck!

---

### Post by UltraAnders on 2013-06-16
Okay, so I switched on the lappy this morning and it's working! Go figure. I reset the lappy numerous times yesterday. :rolleyes: :-k

---

