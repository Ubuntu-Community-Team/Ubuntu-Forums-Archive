---
title: "Need help setting up Samba for Windows 7 WITH user-login."
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by xdominex on 2010-10-25
I am currently attempting to setup Samba 3 (installed) for a basic home-network file-sharing server via Ubuntu 10.04. It seems like (based on my extensive googling and research) nobody wants or has a configuration like I do, but surely SOMEBODY knows how to do this. 


The following is my goal for a basic setup.

Folder 1 (share is called "Read-Write"):
-Users from Windows 7 can see, read, write, execute, create, or delete any files and folders in Folder 1 as they so desire.
-Users can accomplish all of this from as "guest."

Folder 2 (share is called "Read-Only"):
-I can log in as my user to see, read, write, execute, create, or delete any files and folders in Folder 2 as I so desire.
-People other than me can log in as "guest."
-"Guest" users from Windows 7 can see, read, and execute programs as desired.


Things I have accomplished:
-Directories exist
-Directories are browseable via Windows 7
-My user has a password for Samba (assigned via "sudo smbpasswd -a matthew)

Things I have not yet been able to accomplish:
-Configure Folder 2 so that Samba asks for login credentials when someone tries to access it SO THAT I an use my Samba user to log in.
-Configure Folder 2 so that, when I log in as my Samba user, I can see, read, write, execute, create, or delete any files and folders in Folder 1 as I so desire.
-Configure Folder 2 so that Windows 7 users can easily access it as guest to browse, read, and execute files and folders in it.

-Configure Folder 1 so that any Windows 7 user can easily access it as guest to see, read, write, execute, create, or delete any files and folders in Folder 1 as they so desire.

Thank you so much for your help!

---

### Post by Morbius1 on 2010-10-25
Most of what you want to do isn't being impeded by Samba but by Linux file permissions. 

First off though:
> Folder 1 (share is called "Read-Write")
Folder 2 (share is called "Read-Write")Can't have two shares with the same name so one of them will have to change.

_* Let's start with Folder1:*_

First you are going to have to change permissions of the target folder in order to accommodate a guest remote user:
```
sudo chmod 0777 /path-to-Folder1
```Then a very basic share would look like this:
```
[Read-Write1]
path = /path-to-Folder1
read only = no
guest ok = yes
force user = nobody
```Any remote user that adds or edits a file in that share will have the following ownership/permissions:
nobody / 0755 which will allow him and other remote users to have full access.

_* For Folder2:*_

Only because this is beginning to give me a headache ( I'm not used to thinking this much all at once :) ) I would suggest something slightly unconventional:

Share the same target folder twice with different share names and with different authentications.

Once again change permissions on the target:
```
sudo chmod 0777 /path-to-Folder2
```Create a guest share just like above but with a different path and with write turned off:
```
[Read-Write2]
path = /path-to-Folder2
read only = yes
guest ok = yes
force user = nobody
```Then create a different share pointing to the same path but with an "R" at the end of the share name to indicate that it is "Restricted", with write turned on, and with guest access denied:
```
[Read-Write2R]
path = /path-to-Folder2
read only = no
guest ok = no
force user = nobody
```In Read-Write2 you can only read. In Read-Write2R only an authenticated user can write and guest will have no access although guest will have read only access to the same contents at Read-Write2.

I'm used to doing this sort of thing iteratively so I create a share - it doesn't work as I expected - and eventually I can get it to work. I may have made a typo or more embarrassingly a logic mistake somewhere in here but give it a shot and see if it does what you want.

---

### Post by xdominex on 2010-10-26
I got it! I can't believe this took me like 5-6hrs per day for about 4 days to figure this out, but here's my entire setup:

"matthew" as a Samba user with password.

sudo chmod 0777 /svr/Samba/R-W  (this is Folder 1)
sudo chmod 0755 /svr/Samba/R-O  (this is Folder 2)

I then opened "Run Application," typed in "gksudo" and then "nautilus." Now in the file browser I made myself the owner of both folders.

Here are my relevant Samba parameters:

```

[Global]
   workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   map to guest = bad user
   usershare allow guests = yes

[Filebase 1]
	path = /srv/Samba/R-W
	read only = no
	guest ok = yes
	force user = nobody

[Filebase 2]
	path = /srv/Samba/R-O
	read only = yes
	guest ok = yes
	write list = matthew
```

Thank you so much for your help and recommendations! The directions you gave me helped get me extremely close, then I figured out that I had to use 0755 for the one guests can access but not read/write in. I also had to go in and change the ownership settings on the folders. Both of those things were very easy and quick, though. Thanks a ton! This is my first time ever playing with a network setup like this, and I get extremely excited about this kind of thing. I'm a 19-year-old messing around with his home network (supports about 5 computers right now including the one used as a server) because I freakin love networking and computer stuff and am determined to get good at both Samba and Ubuntu in general.

---

### Post by Morbius1 on 2010-10-26
First off it's a miracle you got any assistance from my ramblings. :)

Second, and this is only is you have the time, would you mind confirming or rejecting a possible problem I see with this share:
> [Filebase 2]
    path = /srv/Samba/R-O
    read only = yes
    guest ok = yes
    write list = matthewHere's my theory: That will only work if the client to this server is Windows and only if the Windows client is logged in as matthew. It will not work if the client is another Linux box.

"guest ok = yes" takes priority over "write list" so when a linux machine seeks to access the share ( regardless of who is logged into the linux box ) the remote user is never prompted for authentication. Since the share is declared "read only" he will not be able to write to that share.

If however the remote user is running windows and his local Windows login username is "matthew" then Windows will pass his username at the moment he attempts to access the share ( it's a Windows thing ) so his identity is already acknowledged by Samba and is allowed to write.

I don't know if any of your other machines are running linux but can you confirm that the remote user is never prompted for authentication. So if the remote user happens to be "matthew" on a linux box he will never be granted write access to the share. Actually, ... um ... It should happen for another Windows user as well I think. Nobody is being prompted for authentication unless perhaps the local Windows login username matches a samba user name but the passwords are different.

---

