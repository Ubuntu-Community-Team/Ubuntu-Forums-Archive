---
title: "mythtv network access"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by crazedgremlin on 2006-12-22
Hi!  I just installed mythtv on one of my computers (this computer is downstairs).  I want to access files from the mythtv computer on my other computer which is upstairs.  Does anyone an easy way to do this?

--dan

---

### Post by Yako on 2006-12-22
Mount the share.
Be sure to have installed smbclient. Then make a folder in your home directory or in mythtv's media folder, for example mkdir /home/user/remote, then edit /etc/fstab to contain something like the following:

//server_name_or_ipadress/share   /home/user/remote      smbfs     guest    0    0 

Be sure to replace server_name_or_ipaddress with the correct address, and share with the correct folder. Save and exit, then execute

sudo mount /home/user/remote

The remote files should now display in the /home/user/remote. MythTV should now be able to access them.

Warning: The share name can only be a share name on the server, so things like //server or //server/share/subfolder won't work. Only the shares themselves can be mounted, not the server or subdirectories.

---

### Post by josesanders on 2006-12-22
Mythtv is supposedly designed for that.  Assuming that you have the backend installed on one computer, all you need to install is the frontend on the second computer.  I am working on doing just that right now.  I found this page helpful:

[http://wilsonet.com/mythtv/tips.php](http://wilsonet.com/mythtv/tips.php)

Unfortunately, I don't yet have it working.  Here is a link to the thread that I started about it:

[http://www.ubuntuforums.org/showthread.php?t=322630](http://www.ubuntuforums.org/showthread.php?t=322630)

---

### Post by superm1 on 2006-12-22
> **crazedgremlin said:**
> Hi!  I just installed mythtv on one of my computers (this computer is downstairs).  I want to access files from the mythtv computer on my other computer which is upstairs.  Does anyone an easy way to do this?

--dan

What OS is the computer upstairs using?

---

### Post by crazedgremlin on 2006-12-22
> What OS is the computer upstairs using?

Sorry about that.  It's running Ubuntu Edgy :)

---

### Post by crazedgremlin on 2006-12-22
> **josesanders said:**
> Mythtv is supposedly designed for that.  Assuming that you have the backend installed on one computer, all you need to install is the frontend on the second computer.  I am working on doing just that right now.  I found this page helpful:

[http://wilsonet.com/mythtv/tips.php](http://wilsonet.com/mythtv/tips.php)

Unfortunately, I don't yet have it working.  Here is a link to the thread that I started about it:

[http://www.ubuntuforums.org/showthread.php?t=322630](http://www.ubuntuforums.org/showthread.php?t=322630)

I actually have already tried that.  I was having a hard time getting the frontend working, so I decided to try to just get access to the files.
I just realized it was kindof a silly post; I can just run an ftp server and get the files through there.

Thanks for the replies, guys.

---

### Post by superm1 on 2006-12-27
> **crazedgremlin said:**
> I actually have already tried that.  I was having a hard time getting the frontend working, so I decided to try to just get access to the files.
I just realized it was kindof a silly post; I can just run an ftp server and get the files through there.

Thanks for the replies, guys.
Well if your looking for some help getting the frontend working, I can try to lend a hand.  

A couple of important areas to start:
Make sure in the backend's /etc/mysql/my.cnf doesn't bind directly to 127.0.0.1.  

Make sure the backend had mythtv-setup not binding the master database or the location of the master server to 127.0.0.1.

Make sure that the frontend's ~/.mythtv/mysql.txt is accurate, and if the user is in the mythtv group that /etc/mythtv/mysql.txt is accurate.

---

