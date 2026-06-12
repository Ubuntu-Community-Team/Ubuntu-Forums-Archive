---
title: "Streaming MP3's from Windows"
date: 2008-05-07
forum: Multimedia Software
---

### Post by RAMDrive on 2008-05-07
Search has failed, so here is the question...

I have all my MP3's on a windows server. To play then on other MS boxes I have foobar running and configured to stream from the MS server.  Is there a way to do something like that in 8.04?  I don't have the HD space to copy the files to this machine.

Thanks.

---

### Post by wolfen69 on 2008-05-07
try vlc player. it can do almost anything.

---

### Post by maphilli14 on 2008-05-07
I have Tectia's SSH daemon running on my Win2k3 server.  Then I mount the drive with the mp3s via sshfs.  Works like a champ in Amarok (other too I'm sure!)

HTH,

Mike

---

### Post by RAMDrive on 2008-05-08
thanks for the help i got it working using an smbfs mount in fstab and playing with amarok.

//ipaddress/sharename   /home/ramdrive/files smbfs credentials=/root/.smbcredentials   0   0

---

