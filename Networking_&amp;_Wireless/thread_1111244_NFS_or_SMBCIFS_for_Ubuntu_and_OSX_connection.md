---
title: "NFS or SMB/CIFS for Ubuntu and OSX connection?"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by Chris Weaver on 2009-03-30
Dear All,

For about two months ago I finished switching our community radio station (Resonance104.4FM) over to Ubuntu 8.10. Having little experience it was in parts both harrowing and educational! The only computer that didn't get switched over was an PPC Apple laptop running Tiger. This serves as our playout machine and I managed to share its music directories by simply mounting them via the following fstab entry:

```
//xxx.xxx.xxx.xxx/chrisweaver/Audio/Prerecords  /mnt/Laptop/Prerecords  cifs        username=myusername,password=mypassword,uid=1000 0  0
``` 


This works fine or so it seemed. Every now and then files transfered onto the OSX machine would be corrupted in some small way (mp3 files cutting out halfway through for instance) and now today another issue (which has prompted me to write this post) has arisen after an update of Tiger. The mount points are taking about 10 minutes to work (i.e the /mnt/ directories are empty until you refresh them 10 minutes after boot up)

So I have two questions:

1) Is SMB/CIFS a good method for transferring files between OSX and Ubuntu. Would FTP or NFS be more reliable? 

2) Has anyone else had this "hanging mount issue" or perhaps suggest how I could test if it was related to the OSX update?

many thanks in advance.

---

### Post by inobe on 2009-03-30
vlc can stream and it's multi platform.

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

i think the directions located in the vlc docs is a more sufficient way to streaming media over a lan..

but if you wish to use smb [https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

or at best' a free multi platform music server :lol:

[http://sockso.pu-gh.com/](http://sockso.pu-gh.com/)

---

### Post by Chris Weaver on 2009-03-31
I don't understand your reply? The network links are fine 90% of the time. It's just that 1% when a programme transfer will die on air.

---

### Post by ddnev45 on 2009-03-31
A friend of mine uses Ubuntu as an ftp server to network mac and windows laptops without any problems.

[http://ubuntuforums.org/showthread.php?t=218630&highlight=ftp+server]("http://ubuntuforums.org/showthread.php?t=218630&highlight=ftp+server")

[http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server]("http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server")

I've never set up an ftp server myself, so I don't know any details.

---

### Post by Chris Weaver on 2009-04-01
I did think along that but here things have to be kept simple. So the situation is that the audio editing is done on the Ubuntu machines and then the files are dropped on OSX machine for playback.

Strangely, I turned on an old Ubuntu 8.10 machine and it connected to the shares immediately!

---

