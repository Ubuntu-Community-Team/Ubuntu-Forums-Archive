---
title: "Mount CIFS"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by ruzlebiff on 2011-01-10
Hello,
 
I'm running the latest stable FreeNAS with CIFS/SMB enabled.
When i browse info the share everything works fine (no user/pass auth), but if i try to permanently mount the share using fstab and the guide here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) i get permission-problems.
No difference if i use no user/pass, gues- or admin-login.. Still get a padlock on every folder/file i copy/create on the share.
 
Anyone got a working, permanently mouting-guide for me?
 
BR
Sindre

---

### Post by Morbius1 on 2011-01-10
Why not post the line in fstab that you are using to mount the remote share.

---

### Post by ruzlebiff on 2011-01-10
//netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0 
//netbiosname/sharename    /media/sharename        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Have tried both of these, with the same result: padlock on every file i copy, and on every folder i create.

---

### Post by Morbius1 on 2011-01-10
Add nounix to this:
> //netbiosname/sharename    /media/sharename        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0So that it looks like this:
> //netbiosname/sharename    /media/sharename        cifs     guest,rw,iocharset=utf8,[COLOR=Blue]nounix[/COLOR],file_mode=0777,dir_mode=0777 0 0

---

### Post by ruzlebiff on 2011-01-10
Works like a charm! Thanks a million! 
Solves a lot of my problems :)

---

### Post by carcare999 on 2011-02-10
Simplifies equipment rooms, but has disk, has memory..
but  very little room for I/O (liek a blade) so gigabit ethernet or simple  serial/Scsi IO.. but completelky standalone for small applications eg  DNS servers, Data in/data out with no big need for databases or temprary  diskspace.
=============
[education blog](http://www.canshine.com/)
[Music](http://www.rockstopscene.co.uk)

---

