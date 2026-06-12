---
title: "Network shares"
date: 2008-02-09
forum: Mythbuntu
---

### Post by JMuffin on 2008-02-09
I'm trying to set up mythbuntu to use solely to stream videos from my desktop to my tv. I have it up and running but have absolutely no idea how to actually mount my shared folder on my desktop and make the myth box see it. I've tried searching the forums but haven't been able to find anything that worked. Please help!

---

### Post by JMuffin on 2008-02-09
Has nobody else had to mount a shared folder on their myth box? I've tried editing my fstab file about 17 different ways using various instructions from a number of forums and nothing seems to work. All i want to do is mount a folder from another computer into the /var/lib/mythtv/videos folder, Is that even the right thing to do? Can anybody help?

---

### Post by newlinux on 2008-02-10
It would help if you showed us what you did and what went wrong. Sounds like you are trying to right thing. What kind of share is it (Samba, NFS)? Coming from what OS? Are you sure the share is setup properly? Many here have mounted shared folders, but more info would help us a lot to help you.

---

### Post by JMuffin on 2008-02-10
My other computer is running ubuntu, I'm sharing the folder with Samba. If I right click on the folder and choose "share folder", it says it's being shared through "Windows Network (SMB)". On the mythbuntu box, the line I added to fstab currently looks like this:

```
//jmuff-desktop/stuff    /var/lib/mythtv/videos smbfs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

I have also tried replacing the credentials part with guest, and with a user name and password right in the line. I have tried using cifs instead of smbfs. After editing the file, I exit out and do sudo mount -a, if I use smbfs, I get an error that reads

```
<number>: session setup failed: ERRDOS - ERRnoaccess(Access denied.)
SMB connection failed
```

If I use cifs and then mount, I get a mount error 13 = Permission denied message.

Any idea why I'm being denied? The username and password I'm using are for the only account on the ubuntu box. It seems like that acount should have access to the folder.

---

### Post by newlinux on 2008-02-10
You should stick with cifs since smbfs is being replaced by it. Using file_mode and dir_mode are options meant for cifs anyway. smbfs uses a slightly different syntax.

First you should verify the share is setup correctly. I don't have any experience setting up a SAMBA share via gnome - I've done it with /etc/samba/smb.conf file, similar to how it is explained here: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Servers](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Servers). Can you browse to it without mounting it from another computer? You can also try browsing to it using your filemanager of preference with the URL: smb://jmuff-desktop/stuff 

Also, is /var/lib/mythv/videos an empty directory? If this share is only going to be used for Linux machines you might want to use NFS instead of SAMBA. [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server)

---

