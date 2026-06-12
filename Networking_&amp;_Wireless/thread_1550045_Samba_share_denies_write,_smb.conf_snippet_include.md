---
title: "Samba share denies write, smb.conf snippet included"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by locoHost on 2010-08-10
Thanks for reading :)

I'm a very -slightly- advanced Samba user. I believe I know the basics of editing the smb.conf and I know to use smbpasswd to update the Samba users database.

I have a group of identical shares. They are readOnly for the group @movies-play and they are (supposed to be) writeable by specific users. The readOnly group works great, no prob there, but I cannot get write access for the specified users. They are in the Samba user database using smbpasswd -a mark and neelix.

Here is the share section in my smb.conf...

```
[movies-usb3]
   path = /media/usb3/movies
   guest ok = no
   browseable = yes
   read only = no
   read list = @movies-play
   write list = mark, neelix
```

I have the workgroup and netbios info set. I have security=user set. The folder 'movies' in the path above is owned by 'mark' so it seems I should be able to write in it but I can't. 

I'm connecting to the share (it's on a server running Lucid) from my laptop (running Lucid). I added this mount info to fstab...

```
//spock/movies-usb3  /media/spockmovies3  cifs  credentials=/home/mark/.smbpasswd  0  0
``` 

Of course spock in the hosts file so it resolves. I can see the share fine, just can't write.

Can you guess what I might be missing?


Thanks in advance for your expert advice. I sure need it :)

Mark

---

### Post by Iowan on 2010-08-10
My (somewhat old) Samba Unleashed book suggests that the "read only = no" *should* make the share writable by everyone ***not*** in the @movies-play group.
Perhaps you've already seen [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To.

---

### Post by locoHost on 2010-08-11
I think this is an unsolvable problem... 

I've been mucking with this for 3 full days and the best I can make happen is ONE of the 4 identical shares is writable and no, I don't know how that happened. Just that ONE! What's different about that one share you ask? Good question, nothing! I've looked at every line in the smb.conf, every line in both fstabs (client and server), the permissions in the mount folders on client, the permissions in the mount folder on server, everything is the same for each of the 4 shares. The owner of everything is 'mark' and 'mark' (me) is the admin on both boxes, and 'mark' is even in the 'sambashare' group on every folder in both machines and the group has write permission... yet... just ONE share allows write!!! The others throw deny error.

Here is the fstab...

```
//192.168.0.4/movies-usb1	/media/movies1	cifs	rw,_netdev,credentials=/home/mark/.smbpasswd	0	0
//192.168.0.4/movies-usb2	/media/movies2	cifs	rw,_netdev,credentials=/home/mark/.smbpasswd	0	0
//192.168.0.4/movies-usb3	/media/movies3	cifs	rw,_netdev,credentials=/home/mark/.smbpasswd	0	0
//192.168.0.4/movies-usb4	/media/movies4	cifs	rw,_netdev,credentials=/home/mark/.smbpasswd	0	0
```


The credentials file contains...

username=mark
password=mypassword

This account exists on both the client and the server. The password is different on each machine. This credentials file is on the client and the password is the password for the server account. The account IS in the samba user database on the server with this password using smbpasswd -a mark


Here is one of the share in smb.conf

```
[movies-usb2]
   path = /media/usb2/media/movies
   guest ok = no
   browseable = yes
   read only = no
   write list = mark, neelix
```

This the the one share that is writeable, however the other four shares have the same settings in the smb.conf. Of course the usb? is different.


I think I'll go throw myself down the stairs now... 

:(

---

### Post by Iowan on 2010-08-11
Hmmm... that brings back (some) memories from long ago. I remember another thread that had multiple shares - only one of which (the first one?) worked properly. Now if I can find it...

---

### Post by capscrew on 2010-08-12
> **locoHost said:**
> I think this is an unsolvable problem... 
Maybe, but I would not give up just yet.  :D> 

I've been mucking with this for 3 full days and the best I can make happen is ONE of the 4 identical shares is writable and no, I don't know how that happened. Just that ONE! What's different about that one share you ask? Good question, nothing! I've looked at every line in the smb.conf, every line in both fstabs (client and server), the permissions in the mount folders on client, the permissions in the mount folder on server, everything is the same for each of the 4 shares. The owner of everything is 'mark' and 'mark' (me) is the admin on both boxes, and 'mark' is even in the 'sambashare' group on every folder in both machines and the group has write permission... yet... just ONE share allows write!!! The others throw deny error.

Here is the fstab...

```
//192.168.0.4/movies-usb1	/media/movies1	cifs	rw,_netdev,credentials=/home/mark/.smbpasswd	0	0
//192.168.0.4/movies-usb2	/media/movies2	cifs	rw,_netdev,credentials=/home/mark/.smbpasswd	0	0
//192.168.0.4/movies-usb3	/media/movies3	cifs	rw,_netdev,credentials=/home/mark/.smbpasswd	0	0
//192.168.0.4/movies-usb4	/media/movies4	cifs	rw,_netdev,credentials=/home/mark/.smbpasswd	0	0
```
I'm assuming this is an external drive; yes?  Is the file system ext3 or 4?> 
The credentials file contains...

username=mark
password=mypassword

This account exists on both the client and the server. The password is different on each machine. This credentials file is on the client and the password is the password for the server account. The account IS in the samba user database on the server with this password using smbpasswd -a mark
The user in the mount.cifs (mount -t cifs) command is for the underlying OS and should be the user on the host that partition is mounted on (the local host).> 


Here is one of the share in smb.conf

```
[movies-usb2]
   path = /media/usb2/media/movies
   guest ok = no
   browseable = yes
   read only = no
   write list = mark, neelix
```

This the the one share that is writeable, however the other four shares have the same settings in the smb.conf. Of course the usb? is different.

What security setting do you have in the global section of the smb.conf file?> 


I think I'll go throw myself down the stairs now... 

:(

For now what we need to know is:
[LIST]
[*]What type of security are you using in the [GLOBAL] section of the smb.conf file
[*]What is the filesystem type on the mounted partition?
[*]Post the output of "ls -l on each share
[*]List the file system hierarchy of the shares 

[/LIST]

---

### Post by locoHost on 2010-08-12
> **capscrew said:**
> For now what we need to know is:
[LIST]
[*]What type of security are you using in the [GLOBAL] section of the smb.conf file
[*]What is the filesystem type on the mounted partition?
[*]Post the output of "ls -l on each share
[*]List the file system hierarchy of the shares 

[/LIST]

For right now...

1. security = user
2. I'll have to double check but I think usb1 and usb2 (2 is writeable) are both ext3, and usb3 and usb4 are both ext4. They're all plugged into the same usb hub on the server.
3. and 4. I'll try to get these posted around luch time

Thank you, Thank you, Thank you, Thank you! :)

---

### Post by locoHost on 2010-08-12
[COLOR="Blue"]The user in the mount.cifs (mount -t cifs) command is for the underlying OS and should be the user on the host that partition is mounted on (the local host).[/COLOR]

Wait, perhaps this is the problem! The credentials file has username=mark and password=theServerPassword, not the local 'mark' password. 'mark' is a user on both machines but diff passwords.

I'll try this too! :)

---

### Post by locoHost on 2010-08-12
All of the drives are Ext4 (version 1.0)


I changed the .smbpasswd file to...

```
username=DEIBERTS/mark
password=clientMarkPassword-notServerMark

```

I then umounted the 4 and did mount -a ...

```
root@E1705-laptop:/home/mark# mount -a
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```


I change the password back to the 'mark' password on the server and they all mount, however still with just usb2 being writable.

---

### Post by locoHost on 2010-08-12
Here are the ls from 2 of the server shared drives...

```
mark@spock:/media/usb2/media$ ls -l
total 56
drwxrwxr-x  70 mark sambashare 20480 2010-08-12 08:26 movies
drwxrwxr-x 418 mark sambashare 20480 2009-11-21 20:33 music
drwxrwxr-x   2 mark sambashare  4096 2009-12-09 19:43 pictures
drwxrwxr-x   3 mark sambashare  4096 2010-06-09 10:29 share
drwxrwxr-x  10 mark sambashare  4096 2010-07-30 15:43 tvshows


mark@spock:/media/usb4$ ls -l
total 36
drwxrwxr-x  2 mark sambashare 16384 2010-06-02 16:07 lost+found
drwxrwxr-x 68 mark sambashare  4096 2010-08-05 17:19 movies
drwxrwxr-x  2 mark sambashare  4096 2010-06-02 16:58 music
drwxrwxr-x  2 mark sambashare  4096 2010-06-02 16:58 pictures
drwxrwxr-x  4 mark sambashare  4096 2010-07-31 15:25 share
drwxrwxr-x  2 mark sambashare  4096 2010-06-02 16:58 tvshows

```

You can see that usb2 has a 'media' folder as the parent of the individual media type folders. usb3 and usb4 do not have this. That parent media folder has same user and group and permissions so I don't think that is an issue. Plus usb1 has this same extra parent, but it's still not writeable like usb2 is.

The 'movies' folder is specified in the share sections in the smb.conf. I guess you can see that in the post above :)

Here are all 4 share sections from smb.conf on server...

```
[movies-usb1]
   path = /media/usb1/media/movies
   guest ok = no
   browseable = yes
   read only = no
   write list = mark, neelix

[movies-usb2]
   path = /media/usb2/media/movies
   guest ok = no
   browseable = yes
   read only = no
   write list = mark, neelix

[movies-usb3]
   path = /media/usb3/movies
   guest ok = no
   browseable = yes
   read only = no
   write list = mark, neelix

[movies-usb4]
   path = /media/usb4/movies
   guest ok = no
   browseable = yes
   read only = no
   write list = mark, neelix

```

---

### Post by capscrew on 2010-08-12
> **locoHost said:**
> All of the drives are Ext4 (version 1.0)


I changed the .smbpasswd file to...

```
username=DEIBERTS/mark
password=clientMarkPassword-notServerMark

```

I then umounted the 4 and did mount -a ...

```
root@E1705-laptop:/home/mark# mount -a
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```


I change the password back to the 'mark' password on the server and they all mount, however still with just usb2 being writable.

Could we define the hosts and the mortal users little better?  I'm not sure what you mean by server a or client.  Hosts are hosts and they have hostnames.  What is the hostname of the host that is *providing *the SMB resources (the shares)? What is the hostname of the host that is *requesting  * the share?

At this point I am **have no answers**.  I'm just gathering information.

---

### Post by locoHost on 2010-08-12
> **capscrew said:**
> At this point I am **have no answers**.  I'm just gathering information.

I fully understand and I GREATLY appreciate!!

The physical setup is this client laptop (for now, just this one laptop) and a server in the basement. The server in the basement is 'SPOCK'. Spock is it's netbios name. Is that what you mean by hostname? This laptop is netbios name 'E1705-LAPTOP'. These names are also mapped to the fixed IPs in the hosts files on each machine. Spock has a usb hub with 4 drives plugged in. All machines are running Ubuntu 10.04. Samba is installed on all machines.

There is a user account called 'mark' on each machine. Not sure what the UIDs are or if they match. Not sure if that matters. The passwords differ on each machine. There is also a gr-oup (the word 'gr-oup' is getting star'd out by this forum software!?!? Weird.) on each machine called 'sambashare'. My goal is that 'mark' and/or a user in 'sambashare' will be able to write to the drives on Spock. Follow? Of course I could make everything global write but that kinda defeats the purpose of the file system security right? :) I don't want 'other' to be able to write and mess up the media.

Did I answer your question? Close? ;)

---

### Post by capscrew on 2010-08-12
You have made this needlessly confusing.  See my comments below.


> **locoHost said:**
> Here are the ls from 2 of the server shared drives...


```
mark@spock:/media/usb2/media$ ls -l
total 56
drwxrwxr-x  70 mark sambashare 20480 2010-08-12 08:26 movies
drwxrwxr-x 418 mark sambashare 20480 2009-11-21 20:33 music
drwxrwxr-x   2 mark sambashare  4096 2009-12-09 19:43 pictures
drwxrwxr-x   3 mark sambashare  4096 2010-06-09 10:29 share
drwxrwxr-x  10 mark sambashare  4096 2010-07-30 15:43 tvshows


mark@spock:/media/usb4$ ls -l
total 36
drwxrwxr-x  2 mark sambashare 16384 2010-06-02 16:07 [COLOR="Red"]**lost+found**[/COLOR]
drwxrwxr-x 68 mark sambashare  4096 2010-08-05 17:19 movies
drwxrwxr-x  2 mark sambashare  4096 2010-06-02 16:58 music
drwxrwxr-x  2 mark sambashare  4096 2010-06-02 16:58 pictures
drwxrwxr-x  4 mark sambashare  4096 2010-07-31 15:25 share
drwxrwxr-x  2 mark sambashare  4096 2010-06-02 16:58 tvshows

```

The lost+found (shown in red above) should be owned by root.  How and why is this owned by the mortal user mark?  This also is the root (beginning) of the partition.  The other is not the root of a partition.> 

You can see that usb2 has a 'media' folder as the parent of the individual media type folders. usb3 and usb4 do not have this. That parent media folder has same user and ***** and permissions so I don't think that is an issue. Plus usb1 has this same extra parent, but it's still not writeable like usb2 is.

Who knows whether it matters.  It may not, but then again it may.  I have a very simple file structure so I can easily correct just these kind of problems. > 

The 'movies' folder is specified in the share sections in the smb.conf. I guess you can see that in the post above :)

Here are all 4 share sections from smb.conf on server...

```
[movies-usb1]
   path = /media/usb1/media/movies
   guest ok = no
   browseable = yes
   read only = no
   write list = mark, neelix

[movies-usb2]
   path = /media/usb2/media/movies
   guest ok = no
   browseable = yes
   read only = no
   write list = mark, neelix

[movies-usb3]
   path = /media/usb3/movies
   guest ok = no
   browseable = yes
   read only = no
   write list = mark, neelix

[movies-usb4]
   path = /media/usb4/movies
   guest ok = no
   browseable = yes
   read only = no
   write list = mark, neelix

```

The drive I use for Samba shares has 2 partitions.  The first partition is not for sharing at all.  I mention it so you understand the you do not mount drives, *you mount partitions*.  The second partition is for Samba and it is mounted at **/smb**.  I do not use /media for mounting partitions unless it is removable (i.e transient). It appears that you are using similar (and confusing) names for mount points.  I can't tell, but I believe that you are also createing shares inside other shares 

In my partition mounted at /smb, I have /smb/backup and /smb capscrew and /pictures and /smb/videos directories.  These are what are shared.

---

### Post by capscrew on 2010-08-12
> **locoHost said:**
> I fully understand and I GREATLY appreciate!!

The physical setup is this client laptop (for now, just this one laptop) and a server in the basement.
Are both Ubuntu?> 
The server in the basement is 'SPOCK'. Spock is it's netbios name. Is that what you mean by hostname? 
The hostname is not the netbios name.  The can be the same human name, but netbios naming is not hosts naming.> 

This laptop is netbios name 'E1705-LAPTOP'. These names are also mapped to the fixed IPs in the hosts files on each machine. 
You do not map netbios names in /etc/hosts> 
Spock has a usb hub with 4 drives plugged in. All machines are running Ubuntu 10.04. Samba is installed on all machines.
Answered my first question.  :D> 

There is a user account called 'mark' on each machine. Not sure what the UIDs are or if they match. Not sure if that matters. The passwords differ on each machine. 
They are not domin wide accounts.  They are local host only.  If you were careful and had the same UID and password, they would appear as the same account.> 
There is also a gr-oup (the word 'gr-oup' is getting star'd out by this forum software!?!? Weird.) on each machine called 'sambashare'. My goal is that 'mark' and/or a user in 'sambashare' will be able to write to the drives on Spock. Follow? Of course I could make everything global write but that kinda defeats the purpose of the file system security right? :) I don't want 'other' to be able to write and mess up the media.


Did I answer your question? Close? ;)

As long as the user exists on the local host where the shares reside then you should be able to control permission.

---

### Post by CharlesA on 2010-08-12
My bet is that you don't have the proper permissions set at a *file level* on the host system.

I ran into the same problem (kinda) until I changed the file permissions of the folders.

I needed to create a user (not smbuser) on the host system to set the permissions correctly.

You should be able to add neelix and whoever else to the "sambashare" g r o u p if you haven't already. Otherwise the permissions look fine.

I did it differently, but it still works for me.

Sidenote: I wonder why it is censoring "g r o u p"

---

### Post by locoHost on 2010-08-12
> **capscrew said:**
> You have made this needlessly confusing.  See my comments below.

That's very probable :)

> **capscrew said:**
> The lost+found (shown in red above) should be owned by root.  How and why is this owned by the mortal user mark?

I must have: chown at some point.


> **capscrew said:**
> This also is the root (beginning) of the partition.  The other is not the root of a partition.Who knows whether it matters.  It may not, but then again it may.

I'll try matching the media parent folder on usb4 and see what happens. 

> **capscrew said:**
>   I have a very simple file structure so I can easily correct just these kind of problems. The drive I use for Samba shares has 2 partitions.  The first partition is not for sharing at all.  I mention it so you understand the you do not mount drives, *you mount partitions*.

Yep I know. I have most of these drives setup with 2 partitions. The first is for data, the second is much smaller, only 2 to 3 hundred GB and they're for backups. I backup movies/music/pics from one data partion on a drive to the backup partition on another drive. Clearly not full backups, just some of the good stuff :)

> **capscrew said:**
> The second partition is for Samba and it is mounted at **/smb**.  I do not use /media for mounting partitions unless it is removable (i.e transient). It appears that you are using similar (and confusing) names for mount points.  I can't tell, but I believe that you are also createing shares inside other shares

Mmm no I don't believe so, but I will certainly investigate this possibility. 

> **capscrew said:**
> In my partition mounted at /smb, I have /smb/backup and /smb capscrew and /pictures and /smb/videos directories.  These are what are shared.


My thought/plan was that the media partitions could not only be read by any machine on the network, but written to by certain other users or groups. Is my plan flawed? Well, flawed beyond this write issue I mean ;)

---

### Post by locoHost on 2010-08-12
> **CharlesA said:**
> My bet is that you don't have the proper permissions set at a *file level* on the host system.

I ran into the same problem (kinda) until I changed the file permissions of the folders.

I needed to create a user (not smbuser) on the host system to set the permissions correctly.

You should be able to add neelix and whoever else to the "sambashare" g r o u p if you haven't already. Otherwise the permissions look fine.

I did it differently, but it still works for me.

Sidenote: I wonder why it is censoring "g r o u p"

Yeah why is g r o u p getting filtered?!?! 

Anyway, not sure what you mean by *don't have proper file level permissions*. The only permissions I currently know of are read, write, execute for user, groop and other. Do you mean something else? You can see the folder permissions in one of the posts above. Do they look wrong?

Thanks for replying! :)

---

### Post by capscrew on 2010-08-12
> **locoHost said:**
> ...

My thought/plan was that the media partitions could not only be read by any machine on the network, but written to by certain other users or groups. Is my plan flawed? Well, flawed beyond this write issue I mean ;)

No, not at all.  The user must have an account on the host providing the share (SMB resource) and the correct directory and file permissions set.  These permissions are set at OS level not just at Samba level.

---

### Post by CharlesA on 2010-08-12
> **locoHost said:**
> Yeah why is g r o u p getting filtered?!?! 

Anyway, not sure what you mean by *don't have proper file level permissions*. The only permissions I currently know of are read, write, execute for user, groop and other. Do you mean something else? You can see the folder permissions in one of the posts above. Do they look wrong?

Thanks for replying! :)

They look correct, but you need to have a user account on the host machine.

Can you post the output of this please:

```
cat /etc/group | grep sambashare
```

That'll make sure that you added the users to that *****.

Both the ***** are the g-word. This definitely makes it hard to understand. >.<

---

### Post by locoHost on 2010-08-12
> **CharlesA said:**
> They look correct, but you need to have a user account on the host machine.

Can you post the output of this please:

```
cat /etc/group | grep sambashare
```

That'll make sure that you added the users to that group.

Both the group are the g-word. This definitely makes it hard to understand. >.<

Ok I'll do this in a few mins. The user 'mark' is on both machines and is an administrator (the account used during install) on both machines. You (well, I) would think that would let that account write where ever it wants. Sorta. You follow?

The account 'mark' is named the same on both machines, but the password is different. Would I gain anything by making the passwords identical?

I'm gonna type groop until someone explains why g r o u p is a bad word... ;)

---

### Post by CharlesA on 2010-08-12
Double post to make it easier to understand.

I installed Samba, used the default smb.conf file settings and just added the shares.

I created two users:

```
sudo useradd write -G sambashare
sudo useradd read
```

write, who was made part of the group "sambashares"
read, who isn't a part of the group "sambashares"

Set their passwords using **sudo smbpasswd -a write** and **sudo smbpasswd -a read**.

```
sambashare:x:110:charles,write
```

The folder I wanted to share was created at /share with these permissions:

```
drwxrwxr-x 4 charles sambashare 4096 2010-08-12 11:22 /share

```

I created two folders inside /share, named read and write. Notice they have the same file permissions:

```
drwxrwxr-x 2 charles sambashare 4096 2010-08-12 11:22 read
drwxrwxr-x 3 charles sambashare 4096 2010-08-12 11:34 write

```

Anyway, here's what the share definitions look like:

```
[write]
   browseable = yes
   path = /share/write
   write list = write,charles
   read list = @read
   create mode = 664
   directory mode = 775

[read]
   browsable = yes
   path = /share/read
   write list = charles
   read list = @read
   create mode = 660
   directory mode = 770

```

The user read can only read from both "read" and "write."
The user write can only read from "read" and can write to "write"
The user charles can write to both read and write.

As for having a different password, I'm not sure, but it would screw up authentication, which would not allow you to access that share.

---

### Post by locoHost on 2010-08-12
What is the @ preceeding the user names? I thought that indicated a groop?

Or does this prove I'm missing pieces :)

---

### Post by CharlesA on 2010-08-12
Yes, the @ means it's a group. I added the "write" user to the "read" group.

I think there's something missing from the way you set it up.

BTW: group is group again.

---

### Post by bapoumba on 2010-08-12
> **locoHost said:**
> Yeah why is g r o u p getting filtered?!?! 


.o/
My fault :(

When some spammers come around to post links and stuff, it is our habit to censor some words that make the links dead with the * signs. I was not cautious enough and "group" was in one of the url..

bodhi fixed it (thanks) and I'll manually fix this thread as the censored words are set up to be kept in the posts db. Well, sorry :KS

---

### Post by locoHost on 2010-08-12
> **CharlesA said:**
> Yes, the @ means it's a group. I added the "write" user to the "read" group.

I think there's something missing from the way you set it up.

BTW: group is group again.

I apologize for being dense: I don't see where you're creating a group called 'read'. I see the user 'read' at the beginning. So the @read in the smb.conf is throwing me :confused:

---

### Post by locoHost on 2010-08-12
Here is the output you asked for in an earlier post...

```
root@spock:/media/usb4# cat /etc/group | grep sambashare
[COLOR="Red"]sambashare[/COLOR]:x:122:mark,neelix

```

The group name 'sambashare' is colored red. Is that significant?

---

### Post by locoHost on 2010-08-12
Hey does this mean anything to you guys...

```
root@E1705-laptop:/home/mark# smbpasswd mark
New SMB password:
Retype new SMB password:
root@E1705-laptop:/home/mark# restart smbd
smbd start/running, process 2152
root@E1705-laptop:/home/mark# cd /media
root@E1705-laptop:/media# ls -l
total 0
drwxrwxr-x 131 mark sambashare 0 2010-07-18 07:24 movies1
drwxrwxr-x  70 mark sambashare 0 2010-08-12 16:14 movies2
drwxrwxr-x  88 mark sambashare 0 2010-06-09 17:13 movies3
drwxrwxr-x  68 mark sambashare 0 2010-08-05 17:19 movies4
root@E1705-laptop:/media# chown root *
chown: changing ownership of `movies1': Input/output error
chown: changing ownership of `movies2': Permission denied
chown: changing ownership of `movies3': Input/output error
chown: changing ownership of `movies4': Input/output error
root@E1705-laptop:/media# 

```

Look at the end where I did chown. movies2 is the mounted share that I *can* write to. The others I cannot write to. What does that mean?

I know you have to umount to make changes but it's odd that the error is different on the share that I can write to?!?!?! :confused:

---

### Post by locoHost on 2010-08-12
Something is definitely wrong. I made the host folders a+rwx. I umounted the shares locally and then made the local (this laptop) folders a+rwx and remounted. So now everything is globally writable from this laptop thru to the host machine. Guess what? Still permission denied. That 'Input/output error' in the post above must be significant. Does anyone know what that means?

---

### Post by capscrew on 2010-08-12
> **locoHost said:**
> Something is definitely wrong. I made the host folders a+rwx. I umounted the shares locally and then made the local (this laptop) folders a+rwx and remounted. So now everything is globally writable from this laptop thru to the host machine. Guess what? Still permission denied. 


That 'Input/output error' in the post above must be significant. Does anyone know what that means?

It means you can't change the owner to root.  Only root can do that.

---

### Post by locoHost on 2010-08-12
> **capscrew said:**
> It means you can't change the owner to root.  Only root can do that.

Right, but I think the *significant* part is that the error is different for the share that is working correctly (movies2/usb2, that allows write as it should). 

I think this a clue that needs interpreted ;)

---

### Post by capscrew on 2010-08-12
> **locoHost said:**
> Right, but I think the *significant* part is that the error is different for the share that is working correctly (movies2/usb2, that allows write as it should). 

I think this a clue that needs interpreted ;)

Use strace before the command.

---

### Post by locoHost on 2010-08-12
Ok, well here's the output. Perhaps someone who speaks 'strace' can see something strange that indicates why movies2/usb2 allows write and the other 3 do not...

```
root@E1705-laptop:/media# strace chown root mov*
execve("/bin/chown", ["chown", "root", "movies1", "movies2", "movies3", "movies4"], [/* 24 vars */]) = 0
brk(0)                                  = 0x850d000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77cb000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=61062, ...}) = 0
mmap2(NULL, 61062, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77bc000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000m\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1405508, ...}) = 0
mmap2(NULL, 1415592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xcb8000
mprotect(0xe0b000, 4096, PROT_NONE)     = 0
mmap2(0xe0c000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x153) = 0xe0c000
mmap2(0xe0f000, 10664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xe0f000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77bb000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb77bb8d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xe0c000, 8192, PROT_READ)     = 0
mprotect(0x8055000, 4096, PROT_READ)    = 0
mprotect(0x551000, 4096, PROT_READ)     = 0
munmap(0xb77bc000, 61062)               = 0
brk(0)                                  = 0x850d000
brk(0x852e000)                          = 0x852e000
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77ca000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb77ca000, 4096)                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_IDENTIFICATION", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_IDENTIFICATION", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=373, ...}) = 0
mmap2(NULL, 373, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77ca000
close(3)                                = 0
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=26048, ...}) = 0
mmap2(NULL, 26048, PROT_READ, MAP_SHARED, 3, 0) = 0xb77c3000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MEASUREMENT", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MEASUREMENT", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap2(NULL, 23, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77c2000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TELEPHONE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TELEPHONE", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=59, ...}) = 0
mmap2(NULL, 59, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77c1000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_ADDRESS", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_ADDRESS", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=155, ...}) = 0
mmap2(NULL, 155, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77c0000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NAME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NAME", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=77, ...}) = 0
mmap2(NULL, 77, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77bf000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_PAPER", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
mmap2(NULL, 34, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77be000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MESSAGES", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
close(3)                                = 0
open("/usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=57, ...}) = 0
mmap2(NULL, 57, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77bd000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_MONETARY", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_MONETARY", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=286, ...}) = 0
mmap2(NULL, 286, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77bc000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=1170770, ...}) = 0
mmap2(NULL, 1170770, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb769d000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2454, ...}) = 0
mmap2(NULL, 2454, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb769c000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap2(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb769b000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=256324, ...}) = 0
mmap2(NULL, 256324, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb765c000
close(3)                                = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
open("/etc/nsswitch.conf", O_RDONLY)    = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=513, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb765b000
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 513
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb765b000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=61062, ...}) = 0
mmap2(NULL, 61062, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb764d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_compat.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\16\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=30496, ...}) = 0
mmap2(NULL, 29268, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xebd000
mmap2(0xec3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0xec3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnsl.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\2201\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=79676, ...}) = 0
mmap2(NULL, 92136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xa6c000
mmap2(0xa7f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12) = 0xa7f000
mmap2(0xa81000, 6120, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xa81000
close(3)                                = 0
mprotect(0xa7f000, 4096, PROT_READ)     = 0
mprotect(0xec3000, 4096, PROT_READ)     = 0
munmap(0xb764d000, 61062)               = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=61062, ...}) = 0
mmap2(NULL, 61062, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb764d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_nis.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\31\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=34408, ...}) = 0
mmap2(NULL, 37432, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x958000
mmap2(0x960000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7) = 0x960000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_files.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \32\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=42572, ...}) = 0
mmap2(NULL, 45772, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x159000
mmap2(0x163000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9) = 0x163000
close(3)                                = 0
mprotect(0x163000, 4096, PROT_READ)     = 0
mprotect(0x960000, 4096, PROT_READ)     = 0
munmap(0xb764d000, 61062)               = 0
open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 3
fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
_llseek(3, 0, [0], SEEK_CUR)            = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=1677, ...}) = 0
mmap2(NULL, 1677, PROT_READ, MAP_SHARED, 3, 0) = 0xb765b000
_llseek(3, 1677, [1677], SEEK_SET)      = 0
munmap(0xb765b000, 1677)                = 0
close(3)                                = 0
fstatat64(AT_FDCWD, "movies1", {st_mode=S_IFDIR|0775, st_size=0, ...}, AT_SYMLINK_NOFOLLOW) = 0
fchownat(AT_FDCWD, "movies1", 0, -1, 0) = -1 EIO (Input/output error)
open("/usr/share/locale/en_US.UTF-8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US.utf8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.utf8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/coreutils.mo", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=613, ...}) = 0
mmap2(NULL, 613, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb765b000
close(3)                                = 0
write(2, "chown: ", 7chown: )                  = 7
write(2, "changing ownership of `movies1'", 31changing ownership of `movies1') = 31
open("/usr/share/locale/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, ": Input/output error", 20: Input/output error)    = 20
write(2, "\n", 1
)                       = 1
fstatat64(AT_FDCWD, "movies2", {st_mode=S_IFDIR|0775, st_size=0, ...}, AT_SYMLINK_NOFOLLOW) = 0
fchownat(AT_FDCWD, "movies2", 0, -1, 0) = -1 EACCES (Permission denied)
write(2, "chown: ", 7chown: )                  = 7
write(2, "changing ownership of `movies2'", 31changing ownership of `movies2') = 31
write(2, ": Permission denied", 19: Permission denied)     = 19
write(2, "\n", 1
)                       = 1
fstatat64(AT_FDCWD, "movies3", {st_mode=S_IFDIR|0775, st_size=0, ...}, AT_SYMLINK_NOFOLLOW) = 0
fchownat(AT_FDCWD, "movies3", 0, -1, 0) = -1 EIO (Input/output error)
write(2, "chown: ", 7chown: )                  = 7
write(2, "changing ownership of `movies3'", 31changing ownership of `movies3') = 31
write(2, ": Input/output error", 20: Input/output error)    = 20
write(2, "\n", 1
)                       = 1
fstatat64(AT_FDCWD, "movies4", {st_mode=S_IFDIR|0777, st_size=0, ...}, AT_SYMLINK_NOFOLLOW) = 0
fchownat(AT_FDCWD, "movies4", 0, -1, 0) = -1 EIO (Input/output error)
write(2, "chown: ", 7chown: )                  = 7
write(2, "changing ownership of `movies4'", 31changing ownership of `movies4') = 31
write(2, ": Input/output error", 20: Input/output error)    = 20
write(2, "\n", 1
)                       = 1
close(1)                                = 0
close(2)                                = 0
exit_group(1)                           = ?
root@E1705-laptop:/media# 

```

---

### Post by capscrew on 2010-08-12
> **locoHost said:**
> Ok, well here's the output. Perhaps someone who speaks 'strace' can see something strange that indicates why movies2/usb2 allows write and the other 3 do not...

```


...

fstatat64(AT_FDCWD, "movies4", {st_mode=S_IFDIR|0777, st_size=0, ...}, AT_SYMLINK_NOFOLLOW) = 0
fchownat(AT_FDCWD, "movies4", 0, -1, 0) = -1 [COLOR="Red"][B]EIO (Input/output error)
[/B][/COLOR]write(2, "chown: ", 7chown: )                  = 7
write(2, "changing ownership of `movies4'", 31changing ownership of `movies4') = 31
write(2, ": Input/output error", 20: Input/output error)    = 20
write(2, "\n", 1
)                       = 1
close(1)                                = 0
close(2)                                = 0
exit_group(1)                           = ?
root@E1705-laptop:/media# 

```

The partitions in question have a EIO error (red).  Although this is a general error, it really means there is something wrong with the partition (install or physical).  As in```
[EIO]
Input/output error.

A physical I/O error occurred.

A referenced object may be damaged.
```

See [**_here _**]("http://publib.boulder.ibm.com/infocenter/iseries/v5r3/index.jsp?topic=/apis/chown.htm").  

If it was me I would reformat the partitions and remake the shares.  I would also store backups for this data offline (tape or CD/DVD) for awhile, just in case the drive itself proves to be bad.

---

### Post by locoHost on 2010-08-13
> **capscrew said:**
> The partitions in question have a EIO error (red).  Although this is a general error, it really means there is something wrong with the partition (install or physical).  As in```
[EIO]
Input/output error.

A physical I/O error occurred.

A referenced object may be damaged.
```

See [**_here _**]("http://publib.boulder.ibm.com/infocenter/iseries/v5r3/index.jsp?topic=/apis/chown.htm").  

If it was me I would reformat the partitions and remake the shares.  I would also store backups for this data offline (tape or CD/DVD) for awhile, just in case the drive itself proves to be bad.

I ran the disk utility filesystem check on usb3 and it's fine. All green lights, disk is healthy. I'll do the same on the other drives before jumping into something this drastic :)

---

