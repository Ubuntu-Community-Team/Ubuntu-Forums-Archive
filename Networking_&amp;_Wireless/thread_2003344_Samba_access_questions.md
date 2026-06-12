---
title: "Samba access questions"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by bavman on 2012-06-13
I set up a home server running ubuntu samba file server. If i set the access to everyone I can access my files just fine and everything works. But if I try to restrict it to certain users I cant log in with my window 7 computers. 

I can't find a good resource that explains everything I need to do to set permissions etc. 
Basically what I'd like to set up is 1 admin account and a couple normal accounts. The admin account I could login from my desktop on the LAN and I would be able to access everything. The normal users would be restricted to their own files and folders and wouldn't be able to access other users files/folder on the drive or certain restricted files that only admin has access to. 

All my computers are running windows 7 and my server is running ubuntu 12.04 LTS.

---

### Post by bab1 on 2012-06-14
> **bavman said:**
> I set up a home server running ubuntu samba file server. If i set the access to everyone I can access my files just fine and everything works. But if I try to restrict it to certain users I cant log in with my window 7 computers. 

I can't find a good resource that explains everything I need to do to set permissions etc. 
Basically what I'd like to set up is 1 admin account and a couple normal accounts. The admin account I could login from my desktop on the LAN and I would be able to access everything. The normal users would be restricted to their own files and folders and wouldn't be able to access other users files/folder on the drive or certain restricted files that only admin has access to. 

All my computers are running windows 7 and my server is running ubuntu 12.04 LTS.

Start with [**_[COLOR="Darkblue"]this[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=1168") howto.  Then edit this line in the /etc/samba/smb.conf file
```

;   name resolve order = lmhosts host wins bcast
```

Edit it to look like this
```

 name resolve order =  bcast

```

You will have to restart the *smbd* daemon (Samba) like this ```
sudo service smbd restart
```

...or you can reboot the system.

---

### Post by bavman on 2012-06-14
Ok so i've set up a couple users. Now how to I do some permission? Right now I have it so I'm sharing a folder and only the 3 users I've create has access to this folder
For example, for now as a test im sharing /srv/samba/share. 

How would I give user1 full read/write access, but user2 and user3 would only have read access? (if thats possible) 

Also how would I make it so only user1 would have access to lets say a folder named "secrete" located inside the share folder. ie user1 would be the only one who could opening it, if user2/3 tried to open it they would get a access denied error?

---

### Post by bab1 on 2012-06-14
> **bavman said:**
> Ok so i've set up a couple users. Now how to I do some permission? Right now I have it so I'm sharing a folder and only the 3 users I've create has access to this folder
For example, for now as a test im sharing /srv/samba/share. 

How would I give user1 full read/write access, but user2 and user3 would only have read access? (if thats possible) 

Also how would I make it so only user1 would have access to lets say a folder named "secrete" located inside the share folder. ie user1 would be the only one who could opening it, if user2/3 tried to open it they would get a access denied error?

There are a couple of things you can do.  You can control user rw access by groups and allow all others to have read only access.  It's going to become cumbersome and complex if you have permissions NOT inherited from above subdirectories, but if you insist you can use Linux ACL's.

I would use the first method and add differing branches to the file system /srv/samba such as /srv/samba/backup or /srv/samba/sales or /srv/samba/accounting.  Then I have groups backup, sales and accounting.  FYI: you don't need to add the directory samba.  The SMB resource is //NETBIOS_NAME/SHARE for the users.  The users don't see the file structure.  Personally I use /smb as it is away from everything else in the Linux file structure.

---

### Post by bavman on 2012-06-14
So what your saying is that I can give user1,2,3 all RW access to the folder (in samba). But then I can set the file permission for the folder as user1 has RW access and user2,3 only have read access (through the os)...and since linux's rules come before samba's rules user2,3 would be denied their access even though its set that was by samba.

i'm really new to linux in general but am trying to learn. If what I said is correct how do I change the ownership to user1 and give that user all the access but restrict user2 and 3?

---

### Post by bab1 on 2012-06-14
> **bavman said:**
> So what your saying is that I can give user1,2,3 all RW access to the folder (in samba). But then I can set the file permission for the folder as user1 has RW access and user2,3 only have read access...and since linux's rules come before samba's rules user2,3 would be denied their access even though its set that was by samba

Not really.  Since Linux EXT4 has [COLOR="Red"]user[/COLOR] - [COLOR="Green"]group[/COLOR] - [COLOR="Blue"]others[/COLOR] as far as access controls for both the directory (folder) and the files, you can use these 3 to control the type of user access.  Consider the following:
The folder has this as permissions```
drwsrwsr-t 8 bab smbusers 4096 2012-04-14 16:15 backup
```

This says the directory backup has rwx for the user and rwx for the group smbusers and r-x for all others.  Linux directories use the eXecute bit to allow directory access and the ability to descend into subdirectories.

For this directory everyone can enter and read (r).  Only the user bab and the group smbusers can read and write (rw).

The files inside (some many subdirectories deep) look like this```

-rw-rw-r--  1 louis smbusers 201K 2010-09-11 16:37 panel2_LBCS2010.jpg
-rw-rw-r--  1 jane smbusers 177K 2010-09-11 16:35 panel_LBCS2010.jpg
```

These are owned by different users but the group is still *smbusers *and so any user that is a member of that group has rw permissions and all have r permissions.  You really don't care who the user is as the group has the same permissions.  Each branch of the file system can have a different group if you want.  You can also use Samba to set a kind of share umask so you could give others no r perms (---) on the files.

Samba can't add permissions it allows or restricts access to the share though.

---

### Post by bavman on 2012-06-14
Thats for pointing me in the right direction. The way linux works is very interested, but a little complicated. I downloaded a program called Kuser that can run with sudo permissions and create/mod groups and users so I can give files and folders different access and permissions.
I find that working through terminal is a little hard and confusing sometimes especially if your syntax in lacking.

---

### Post by bab1 on 2012-06-14
> **bavman said:**
> Thats for pointing me in the right direction. The way linux works is very interested, but a little complicated. I downloaded a program called Kuser that can run with sudo permissions and create/mod groups and users so I can give files and folders different access and permissions.
I find that working through terminal is a little hard and confusing sometimes especially if your syntax in lacking.

Kuser is a KDE user and group manager.  You need to configure the file system to use groups as I described.  All Debian style distros have User Private Groups (UPG).  You need to alter that in the section of the file system you intend to use.  In essence you need to use the sgid bit with chmod at the root directory of the file system we have been talking about (chmod 2775 <directory>) then set the group you want to use (chgrp <group> <dir>).  At this point you have UNIX style (BSD) file and directory permissions.  Until you do this the users and groups will not function correctly.

See [**_[COLOR="RoyalBlue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for sgid information.

I'm going offline (sleep).  If you have more questions or want me to walk through this with you, post it here and I will respond.  Think about how you can use the groups to segregate the data in a hierarchical way.

Also remember that Samba shares create a root to the share that the user (group) can't go above.  So if you had a share at /smb/backup/machine1/europe/sales, The the user would see //SERVER/SALES and would not be able to up to the directory *europe *or *backup*.

Good luck!

---

### Post by zeljkojagust on 2012-06-14
Didn't read all the posts, but from the initial one... best thing to do would be the same username : password on both Linux and Windows machine. Also it's not enough to allow access to share only in samba config file, you also have to properly configure access on the shared folder itself (user:group).

---

### Post by Morbius1 on 2012-06-14
> **bavman said:**
> The normal users would be restricted to their own files and folders and wouldn't be able to access other users files/folder on the drive or certain restricted files that only admin has access to. 

All my computers are running windows 7 and my server is running ubuntu 12.04 LTS.
What you are describing is a classic [homes] share in samba. The standard [homes] share looks like this:
```
[homes]
comment = Home Directories 
valid users = %S 
create mask = 0700 
directory mask = 0700 
browseable = No
```It creates a share of the remote user's home directory automatically when the remote user asks for it which Windows does by default. It is not a browseable share as you can see in the share definition so other users won't even know that a share is available for someone else on the LAN.

All that's required is for you to create a user on the Ubuntu box that matches the Windows user's login user name and then create a samba password that matches the Windows user's local login user's password. The rest is done automatically. The reason it works automatically with Windows ( you can also make it work with a Linux client ) is because of the way Windows browses the network:

If I log into my Windows box with user = morbius : password = morbiuspw and then browse to the Linux server the morbius / morbiuspw combination is automatically sent to the server without being prompted for it. If there is a "morbius" user on the Linux server and the samba password is set to "morbiuspw" then I can access my home directory automatically.

In the enterprise space this works as designed but in a home LAN there are 2 issues which complicates things because all the usernames and passwords match:

* The administrator of the server now knows the Windows user's login name and password to their box.
* The user now has a home directory and login capability to the physical server itself. So unless you have this in a locked room this could be an issue.

You can work around this problem and still use a [homes] share but it does get a little more involved:

[] You can just create a samba password for the Windows user that does  not match the Windows user's login password and then he will be  prompted for a password when he browses the server. 

[] Or you can do something different, conceptually:

** Create a user account that does not create a home directory and has no local login capability to the server itself.
** Give a path in the [homes] share and point it to something other than a /home directory. 
** Create sub-directories in that path with names that match the Windows user's login name and change ownership to that name.
** Create a samba password that matches the windows's user's login password if you want automatic login or different if you do not.

---

### Post by bab1 on 2012-06-14
Thanks @Morbius1 for pointing out the uses of [homes] share.  If home directories is what the OP wants this is definitely the way to create them.  But in post #3 I believe the OP was talking about shared data so we went down that road.  Either way both ideas can be used together.

---

### Post by Morbius1 on 2012-06-14
@bab1, I missed post 3 when I went through this. You are quite correct - sorry for the interruption.

---

### Post by bab1 on 2012-06-14
> **Morbius1 said:**
> @bab1, I missed post 3 when I went through this. You are quite correct - sorry for the interruption.

I think the info you supplied is great.  Not an interruption at all.

---

### Post by bavman on 2012-06-15
Thanks for all the help bab! I got my raid array set up in my server and have been reading on how ownership and permissions work in ext4 so I was able to get everything up and running with correct access for me and the couple people who access my folders. 

My next step was to enable my server to be accessed online so I would be able to grab files where ever i am. Could anyone point me in the right direction? It seems that there is a lot of options open to me and I'm not sure what to choose, FTP/VPN/SSH ...etc. If at all possible I'd like something that will let me stream some movies/shows over the internet. I was looking at a VPN first but most of the articles I read about it said something about having a static IP address and domain, and that seems really complicated to set up (or costly if I get that stuff through a company.

---

### Post by reptilezone2002 on 2012-06-16
> **bavman said:**
> Thanks for all the help bab! I got my raid array set up in my server and have been reading on how ownership and permissions work in ext4 so I was able to get everything up and running with correct access for me and the couple people who access my folders. 

My next step was to enable my server to be accessed online so I would be able to grab files where ever i am. Could anyone point me in the right direction? It seems that there is a lot of options open to me and I'm not sure what to choose, FTP/VPN/SSH ...etc. If at all possible I'd like something that will let me stream some movies/shows over the internet. I was looking at a VPN first but most of the articles I read about it said something about having a static IP address and domain, and that seems really complicated to set up (or costly if I get that stuff through a company.


well theres a tool called Gadminsamba its available in software center .. it works grait with the desktop version of ubuntu.. im using it ..

---

### Post by bab1 on 2012-06-16
> **bavman said:**
> Thanks for all the help bab! I got my raid array set up in my server and have been reading on how ownership and permissions work in ext4 so I was able to get everything up and running with correct access for me and the couple people who access my folders.

Glad to hear that you have Samba setup correctly.>  

My next step was to enable my server to be accessed online so I would be able to grab files where ever i am. 
If you intend to access your Samba shares over the internet, you will need to create a VPN.  Samba (Windows style sharing) is for LAN's only.  The value of a VPN is that your remote hosts can access the LAN as if it was on the local subnet.> 

Could anyone point me in the right direction? It seems that there is a lot of options open to me and I'm not sure what to choose, FTP/VPN/SSH ...etc. If at all possible I'd like something that will let me stream some movies/shows over the internet. I was looking at a VPN first but most of the articles I read about it said something about having a static IP address and domain, and that seems really complicated to set up (or costly if I get that stuff through a company.
I think you should decide what exactly you want to accomplish (a goal) and then ask; how can I do this.  The protocols you have mentioned have varied uses.  Some are compatible with streaming movies and others are not. For instance, FTP is an insecure way of transferring files from one hosts to another.  SSH is used to create an encrypted tunnel between a remote host and a host in you LAN.  SFTP is a subset of OpenSSH and it functions as an FTP like application inside of an encrypted tunnel.

None of these address how you would stream a movie.  My advice is to ***start a new thread*** as is of topic to this thread and in the wrong forum.  I would open the new thread in [**_[COLOR="Blue"]Multimedia & Video[/COLOR]_**]("http://ubuntuforums.org/forumdisplay.php?f=334")

---

### Post by cybercity@localhost on 2012-06-17
in /etc/smb.conf you have to edit few lines. we assume that you have three folders shared on network

share1
share2
share3

suppose you want share1 to be access able by everyone so under [share1] add 2 strings 
valid users 
possible users

e.g
```

[share1]
valid users = user1 user2 user3
possible users = user1 user2 user3

```so user1 user2 and user3 are allowed to access share1

but if you want share2 to be access able by one particular user just add that user in valid and possible users string.

---

### Post by Morbius1 on 2012-06-17
> **cybercity@localhost said:**
> in /etc/smb.conf you have to edit few lines. we assume that you have three folders shared on network

share1
share2
share3

suppose you want share1 to be access able by everyone so under [share1] add 2 strings 
valid users 
possible users

e.g
```

[share1]
valid users = user1 user2 user3
possible users = user1 user2 user3

```so user1 user2 and user3 are allowed to access share1

but if you want share2 to be access able by one particular user just add that user in valid and possible users string.
I have never seen the parameter "possible users" before. I'm not even sure conceptually what that means. Can't find it in "man smb.conf" either. But just in case I added it to my own smb.conf and ran "testparm -s" and got the following error:
> Unknown parameter encountered: "possible users"
Ignoring unknown parameter "possible users"You can add it if you want but samba will ignore it. Is this some Samba4 thing that I don't know about? If it is can you tell me what exactly is a "possible user"?

---

