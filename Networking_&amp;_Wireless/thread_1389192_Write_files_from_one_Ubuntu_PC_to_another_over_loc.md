---
title: "Write files from one Ubuntu PC to another over local network"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by toogooda on 2010-01-24
Help Please,

What I am trying to do is reasonably simple, I have 1 Ubuntu Desktop PC and 2 Ubuntu Laptops that are all connected via wireless network (remote desktop works perfect so no network issues)
All I want to do is utilise the huge drive space on the desktop machine as a kind of fileshare for the two laptops so backups and music/photo sync can be done.
I have managed to do this using Samba in that from the laptops I can write files in Nautilus to the fileshare **BUT** the files have no owner, no group, and no permissions, this is the if I view from the client or server side.

IE I can navigate on the laptop to the shared are by the smb://servername/filesharename/ in Nautilus right click and add a blank document and call it say "test"
If I now have a look at the permissions it says "The permissions of test could not be determined"
On the server side the new file has a padlock icon and permissions tab says:
Owner nobody
          Read and write
Group nobody
          Read only
others blank
          Read only
or ls -l 
-rwxr--r-- 1 nobody nogroup    0 2010-01-24 21:46 test

I can fix this by do sudo chmod 777 * in dir but that would be an inconvenient hack

I am guessing lots of people do this and I am just being thick about it, can anyone please help me with how to configure samba properly or use it properly to set-up this simple file share?

Details:

All machines using up to date 9.10 desktop

Desktop PC 
logging in as normal user with near root privileges (andrew)
Sharing folder /home/andrew/Public just right clicked in Nautilus and setup share
ls -l
drwxrwxrwx 5 andrew andrew 4096 2010-01-24 21:46 Public
No other setup done

Laptop PC
no setup, just smb://servername/filesharename/ in nautilus

Please help I must be missing something obvious.:(

---

### Post by toogooda on 2010-01-25
Solved it myself today.
Samba was fine the issue was with the way I mounted it on the client, instead of using the obsolete sbmount I used cifs with username password and with 777 mode.

It looked like this:

sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8,file_mode=0777,dir_mode=0777

Once the drive was mounted properly it all worked as expected.

The article that helped me was:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

It also exlains how to have the samba drive mount automatic at start-up.

:D

---

### Post by duanedesign on 2010-01-25
thanks for sharing how you solved this. Definetly some information that will be helpful to others.

Now what else can you figure out for us ;)

---

### Post by Morbius1 on 2010-01-25
Rather that have the client use a mount command to access a shared folder there is an alternate way. On the machine that has the shared folder:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = your_local_user_name
```For example if morbius1 has a folder he wants to share add** force user = morbius1** to smb.conf.

Save the file, exit gedit, and back in the terminal type: **sudo service samba restart**

Now your clients can go back to browsing to the shared folder and when they write to it the force user will act as a mask to force the ownership to be morbius1:morbius1 instead of "nobody".

---

### Post by toogooda on 2010-01-25
> **Morbius1 said:**
> Rather that have the client use a mount command to access a shared folder there is an alternate way. On the machine that has the shared folder:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = your_local_user_name
```For example if morbius1 has a folder he wants to share add** force user = morbius1** to smb.conf.

Save the file, exit gedit, and back in the terminal type: **sudo service samba restart**

Now your clients can go back to browsing to the shared folder and when they write to it the force user will act as a mask to force the ownership to be morbius1:morbius1 instead of "nobody".

Hey that sounds great, and wasn't given in the articles I read. Can you tell me if this method also retains the file permitions? IE 777.

I will give it a go! but still need to mount becuase the rsync tool doesn't support smb:// paths.

Thanks for your help

---

### Post by Morbius1 on 2010-01-25
> Can you tell me if this method also retains the file permitions? IE 777.It's quite likely and highly probable that I don't understand the nature of the problem because you should no longer need 777.

> On the server side the new file has a padlock icon and permissions tab says:
Owner nobody
          Read and write
Group nobody
          Read only
others blank
          Read only
or ls -l 
-rwxr--r-- 1 nobody nogroup    0 2010-01-24 21:46 test

I can fix this by do sudo chmod 777 * in dir but that would be an inconvenient hackI thought the problem was that when a client sent a folder or directory to the server it ended up with nobody:nogroup 744.
The server user couldn't write to that folder or file. The force user fixes that by making the owner the server user.

The force user also works in reverse. If the server user has read / write access to a file in the shared directory so will the client assuming the share definition allows it. For example if the share is set up to allow read/write then the client will have read/write assuming the server user himself has that permission. If the share is set up as read only then even though the remote client is seen as the server user by the server, and even though the server user has local read /write access, samba will not allow a write.

How far away am I from understanding the problem :confused:

---

### Post by toogooda on 2010-01-26
> **Morbius1 said:**
> Rather that have the client use a mount command to access a shared folder there is an alternate way. On the machine that has the shared folder:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = your_local_user_name
```For example if morbius1 has a folder he wants to share add** force user = morbius1** to smb.conf.

Save the file, exit gedit, and back in the terminal type: **sudo service samba restart**

Now your clients can go back to browsing to the shared folder and when they write to it the force user will act as a mask to force the ownership to be morbius1:morbius1 instead of "nobody".

> **Morbius1 said:**
> It's quite likely and highly probable that I don't understand the nature of the problem because you should no longer need 777.

I thought the problem was that when a client sent a folder or directory to the server it ended up with nobody:nogroup 744.
The server user couldn't write to that folder or file. The force user fixes that by making the owner the server user.

The force user also works in reverse. If the server user has read / write access to a file in the shared directory so will the client assuming the share definition allows it. For example if the share is set up to allow read/write then the client will have read/write assuming the server user himself has that permission. If the share is set up as read only then even though the remote client is seen as the server user by the server, and even though the server user has local read /write access, samba will not allow a write.

How far away am I from understanding the problem :confused:

100% yes that is the issue now that you have explained it I agree it is irrelevant thanks for your help

---

### Post by toogooda on 2010-02-04
Have tested the suggestion above:

force user = your_local_user_name

And found it works perfect, much better than my first resolution, I recommend this to anyone with the same issue.

---

