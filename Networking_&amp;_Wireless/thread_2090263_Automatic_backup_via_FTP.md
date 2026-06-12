---
title: "Automatic backup via FTP"
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by lseg on 2012-12-01
Hi guys,

I would like to make an automatic backup of a website via FTP.

I am not sure which tool I should use to do this.
It should be able to copy a full directory (with subdirectories), not copying the files which did not change since last download.

somehow I should add it to crontab, to get it automized.

Any help is welcome,

Kind regards,

Luc

---

### Post by ahallubuntu on 2012-12-01
rsync is what you want.

See my response in #6 in this thread:

[http://ubuntuforums.org/showthread.php?t=2089313](http://ubuntuforums.org/showthread.php?t=2089313)

---

### Post by boogerama on 2012-12-01
LuckyBackup has a nice front end for RSYNC.  Give it a shot.

---

### Post by lseg on 2012-12-02
Hi,

I don't have the option to do rsync, the only option I have is FTP, I am not in control of this web hosting server (it is from one.com).

I want to do a backup of a website, and the only option I have is FTP.
There is no doubt rsync would be a better option, but I simply dont have another option.

Kind regards,

Luc

---

### Post by lseg on 2012-12-03
Hi,

I actually found this trick:
[http://vaunaspada.babel.it/blog/?p=572](http://vaunaspada.babel.it/blog/?p=572)

using curlftpfs to mount the FTP as a normal drive, and then perform rsync locally.

I need the opposite of what is described in this link, instead of making a backup of a local folder to a remote ftp, I would have to make a backup of directories on the FTP site to the local directory.

I am wondering how rsync will deal with this: the FTP drive will  be mounted just before I want to do the backup.
How will rsync detect which files to sync ? I have no idea how rsync keeps track of changes/differences.

Kind regards,

Luc

---

### Post by Lars Noodén on 2012-12-03
> **lseg said:**
> 
How will rsync detect which files to sync ? I have no idea how rsync keeps track of changes/differences.


It uses checksums to find the part of the file that changed.  There is a good interview out there explaining it, but I can't find it.  But here is something:

[http://rsync.samba.org/how-rsync-works.html](http://rsync.samba.org/how-rsync-works.html)

If you can avoid FTP and use SFTP, that would be a good idea.  There is SSHFS which will work over SFTP.  If your hosting service cannot provide SFTP and really does only provide [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp), then it is time to switch to a provider that can actually provide some data security.  It is time to stop using FTP.

---

### Post by Groodles on 2012-12-03
> **lseg said:**
> Hi guys,

I would like to make an automatic backup of a website via FTP.

I am not sure which tool I should use to do this.
It should be able to copy a full directory (with subdirectories), not copying the files which did not change since last download.

somehow I should add it to crontab, to get it automized.

Any help is welcome,

Kind regards,

Luc

The ncftp suite of programs work very well as part of a scripted "FTP" backup.  it supports recursive directory transfers and will skip files which have not changed.

[http://www.ncftp.com/](http://www.ncftp.com/)

It's in the repos too.

---

