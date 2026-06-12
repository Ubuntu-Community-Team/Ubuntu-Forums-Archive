---
title: "FTP backup to NAS"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by acrocephalus on 2012-05-02
Hello!
I have recently bought a NAS (Conceptronic CH3HNAS) and I would like to set up an FTP backup system. On one hand, I would like to backup certain directories. On the other hand, I would like to create an image of my HDD in case I need to restore it. Can anyone point me to the right direction?
Cheers!

Dani

---

### Post by Lars Noodén on 2012-05-02
Well, the right direction would be to steer you away from FTP and towards SFTP.  The NAS does support SSH/SFTP doesn't it?  I can find the Conceptronic CH3HNAS for sale online but not able to find the specs.  But if it runs Linux, like most of these devices, it should have SFTP or be able to easily add it.

Also another step in the right direction would be to use [rsync](https://help.ubuntu.com/community/rsync), which supports [incremental backups](http://www.mikerubel.org/computers/rsync_snapshots/#Incremental).  Better, it only transfers any changes and thus saves bandwidth and time.

---

### Post by acrocephalus on 2012-05-02
> **Lars Noodén said:**
> Well, the right direction would be to steer you away from FTP and towards SFTP.  The NAS does support SSH/SFTP doesn't it?  I can find the Conceptronic CH3HNAS for sale online but not able to find the specs.  But if it runs Linux, like most of these devices, it should have SFTP or be able to easily add it.

Also another step in the right direction would be to use [rsync](https://help.ubuntu.com/community/rsync), which supports [incremental backups](http://www.mikerubel.org/computers/rsync_snapshots/#Incremental).  Better, it only transfers any changes and thus saves bandwidth and time.
Thanks Lars. I'm afraid the Conceptronic CH3HNAS does not have SSH/SFTP, but it seems it is possible to install it. Does anyone know how to do it? I've never done such a thing. I'll check the rsync.

Dani

---

### Post by Lars Noodén on 2012-05-02
I found a manual of sorts but it has little information about customization:

[http://www.conceptronic.net/download_list.php?stype=3&productid=224](http://www.conceptronic.net/download_list.php?stype=3&productid=224)

I think you'd have to look to a user forum for that.  

If nothing else, you can mount the device as a directory using Samba or something like that and then use rsync to transfer between the directories.

---

### Post by acrocephalus on 2012-05-03
Hello,
I'm having some problems with the SFTP solution. My NAS has a SAMBA server, do you think it would be possible to backup over SAMBA and Rsync?

Dani

---

### Post by Lars Noodén on 2012-05-03
Yes, that works, too.  When the NAS is mounted via Samba, it would be like using rsync to transfer between two folders.

---

### Post by acrocephalus on 2012-05-03
Thanks Lars. I'll try this way, I think it's easier than trying to set an SFTP. Do you know how to mount samba on start up? Do you also know a way to create an image of my HDD in case I have to restore the full system?
Cheers!

Dani

---

### Post by Lars Noodén on 2012-05-03
I would start with Ubuntu's [Samba Client Guide](https://help.ubuntu.com/community/Samba/SambaClientGuide).  It covers editing /etc/fstab.  Just be sure to back up /etc/fstab before changing it.  Searching the net for [samba and fstab](https://encrypted.google.com/search?q=fstab+samba) will also bring up lots of examples and HowTos.  If you get a specific problem, post a new thread and the many Samba users here will pounce on it.

About the backup, myself, I usually back up just the data and maybe just a list of packages and configuration files.  I always keep a separate /home or data directory to help with that.  But both a whole system backup or just a data back up can be done with rsync.  It works for both.

---

### Post by acrocephalus on 2012-05-03
Thank you so much Lars. I'll work on that.
Cheers!

Dani

---

