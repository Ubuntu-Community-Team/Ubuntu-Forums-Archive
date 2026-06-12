---
title: "can see workgroup in thunar but can't connect to it"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by N00b-un-2 on 2011-12-03
I've just installed samba, gvfs-backends and fusesmb, and did a dpkg-reconfigure thunar and rebooted.  Now, I have a network icon in thunar and I can open it which shows me "Windows Network".  I click on that and after about a minute, I can see my workgroup.  But if I click on that, it takes several minutes and then times out.  However, if I manually type smb://x.x.x.x (the local ip address of the computer) with the share's I'm trying to access, I can see them immediately.
On a completely separate note, when i use gigolo to connect via SSH, it opens  a secure ftp browser.  WTF is going on with networking on Xubuntu?  I mean, samba has always been a pain in the *** for as long as I can remember (hence my use of NFS for home server purposes).

---

### Post by bab1 on 2011-12-03
> **N00b-un-2 said:**
> I've just installed samba, gvfs-backends and fusesmb, and did a dpkg-reconfigure thunar and rebooted.  Now, I have a network icon in thunar and I can open it which shows me "Windows Network".  I click on that and after about a minute, I can see my workgroup.  But if I click on that, it takes several minutes and then times out.  However, if I manually type smb://x.x.x.x (the local ip address of the computer) with the share's I'm trying to access, I can see them immediately.
On a completely separate note, when i use gigolo to connect via SSH, it opens  a secure ftp browser.  WTF is going on with networking on Xubuntu?  I mean, samba has always been a pain in the *** for as long as I can remember (hence my use of NFS for home server purposes).

This is appears to be a problem with the NMBD daemon.  Is NMBD even running?  you can check using *pgrep * like this```
pgrep -l mbd
```

---

### Post by Morbius1 on 2011-12-03
Give this a shot:

Edit smb.conf as root:
```
gksu leafpad /etc/samba/smb.conf
```Add the following line to the [global] section:
```
name resolve order = bcast host lmhosts wins
```Then save smb.conf and run the following command to restart samba:
```
sudo service smbd restart
```Wait a few minutes - seriously - minutes and then try to access the remote share again.

---

### Post by N00b-un-2 on 2011-12-04
The line was already in global section of smb.conf.  I've been using the same smb.conf file without issues on Ubuntu/kubuntu for well over a year without issues.  In the past I'd tried Xubuntu but the lack of networking was a complete deal breaker (and pyNeighborhood is basically a hack/workaround, as is gigolo).  The backend is there, I can use thunar to connect to my shares fine, but dynamically accessing SMB gets hung up on the workgroup for some reason.  I do however utilize NFS and SFTP which work fine (as does smb when used in the same manner).

---

### Post by N00b-un-2 on 2011-12-04
as for pgrep -l mbd, the output lists two instances of smbd.  wtf?  is that normal?

---

### Post by Morbius1 on 2011-12-04
```
The line was already in global section of smb.conf.
```* Make sure it doesn't have a ";" in front of that line.
* make sure bcast is first.

>          as for pgrep -l mbd, the output lists two instances of smbd.  wtf?  is that normal?     To find out of nmbd is running:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```

---

### Post by bab1 on 2011-12-04
> **N00b-un-2 said:**
> as for pgrep -l mbd, the output lists two instances of smbd.  wtf?  is that normal?

You should have 2 instances of **smbd** and 1 of **nmbd**.  It should like something like this```
939 smbd
986 smbd
1014 nmbd

```

The nmbd daemon handles name resolution for Samba.

---

### Post by N00b-un-2 on 2011-12-04
okay, we are all on the same page.  Yes, I have two instances of smbd, one of nmbd.  the line in smb.conf was not commented with a semicolon and is in the proper order.   The issue persists even after a reboot.

---

### Post by N00b-un-2 on 2011-12-05
strangely enough, I did a fresh install of xubuntu 11.10 on my netbook, followed the exact same steps and samba works flawlessly.

---

