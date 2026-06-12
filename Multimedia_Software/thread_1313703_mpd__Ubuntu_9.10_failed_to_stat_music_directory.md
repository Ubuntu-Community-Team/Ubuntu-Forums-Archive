---
title: "mpd / Ubuntu 9.10 failed to stat music directory"
date: 2009-11-03
forum: Multimedia Software
---

### Post by dmclennan on 2009-11-03
Just upgraded to Ubuntu 9.10, Karmic and I'm finding problems with mpd version 0.15.4.  My music library is on a Windows 2008 Server with Ubuntu CIFS mount setup in fstab.  I am able to access the network including the music folders.  It is important to note that this configuration worked great with Ubuntu 9.04. 

When I start mpd, mpd returns failed to stat music directory.  Depending on how I set the music_directory, I get 

failed to stat music directory "/var/lib/mpd/music": Value too large for defined data type where music -> /mnt/winserver/My Music/iTunes/iTunes Music/ 

or

failed to stat music directory "/mtn/winserver/My Music/iTunes/iTunes Music": No such file or directory.

I very much would like mpd to work in Karmic across CIFS network share.  Any help or suggestions are very much appreciated.

---

### Post by verdun423 on 2009-12-30
[SIZE=3][FONT=Calibri]I have exact the same problem only my music library is on a LaCie nas[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]What have found that this reported as a bug "https://bugs.launchpad.net/ubuntu/+source/linux/+bug/486667" [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Have you found already a solution or work around for this issue. I'm working with kernel 2.6.31-16[/FONT][/SIZE]

---

### Post by dmclennan on 2009-12-30
Sorry, I gave up and expermineted with reinstalling PulseAudio, ALSA, ... and eventually just reinstalled 9.04.  This causes me concern over the benefits of distribution upgrades.  Good luck.

---

### Post by andreaslink on 2010-01-16
Hey,

I think here is your problem solved:
[http://musicpd.org/mantis/view.php?id=2665]("http://musicpd.org/mantis/view.php?id=2665")

As correctly detected, it's a problem because of inodes and cif and so on of a samba share, but using the samba-mount-option "-o noserverino", the proble is solved.

I use:
```
mount -t smbfs -o noserverino,ro,username=andreas //networkstorage/music /var/lib/mpd/music
```

This works fine for me!!

Sincerly, Andreas

---

### Post by verdun423 on 2010-01-17
Hi Andreas
 
Thanks for your reply. Now I'm trying to play audio via Rhythmbox. 
When i can't get Rhythmbox working I'm going back to MPD with your found solution.
 
Thx,Regards
Leo

---

