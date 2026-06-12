---
title: "failed to mount windows share"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by brighty22 on 2011-07-04
Hi,
I have samba running on ubuntu server edition with 3 shares. This is smb.conf on the server:

```

[global]
workgroup = WORKGROUP
server string = File Server
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000

security = user
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes

unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

map to guest = bad user


#guest account = smbguest

[private]
path = /home/george/private
browsable = yes
guest ok = no
read only = no
valid users = george
create mask = 0770
directory mask = 0770

[Media]
path = /share/media
guest ok = yes
read only = no
#write list = george
create mask = 0770
directory mask = 0770

[Backup]
path = /share/backup
guest ok = yes
read only = no
#write list = george
create mask = 0770
directory mask = 0770

```

When accessing 'Media' and 'Backup' from ubuntu 10.10 desktop, I get the message 'Unable to mount location. Failed to mount Windows share'... despite the server being ubuntu. Ironically I can access all shares perfectly with windows 7.

Any ideas why this is happening? Thanks

---

### Post by Morbius1 on 2011-07-04
Here's my guess:
> When accessing 'Media' and 'Backup' from ubuntu 10.10 desktop, I get the  message 'Unable to mount location. Failed to mount Windows share'A failed to mount is usually not a Samba issue but a Linux permissions issue. I notice a couple of things in the share definition:

Your create / directory masks are set to 770. If the permissions on the path are also set to 770 then there is no way a remote guest will ever get access to the share. The permissions need to be set to 777 on /share/media and /share/backup.

> Ironically I can access all shares perfectly with windows 7I'm betting that you have the exact same username on Win7 that you have on Ubuntu. Windows passes the users actual login user name and password when it browses a network. If that name matches a user name and samba password on the Linux server then the Windows user is authenticated without you knowing it even for a guest share.

So if "george" has access to /share/media and /share/backup locally on the Linux Server and the Windows user also has the name "george" then he has access.

---

### Post by brighty22 on 2011-07-04
One chmod later and it all works. Thanks for the explanations :) Before the command, all folders had these permissions (good call - I did have the same username and password on windows):

drwxrwx---  2 george george 4096 2011-07-03 23:48 backup
drwxrwx---  2 george george 4096 2011-07-04 02:13 media
drwxrwx---  3 george george 4096 2011-07-04 14:11 private

The idea was backup and media were read only by anyone on the network, but when I accessed them (via windows or ubuntu) with my username, I could write. By chmodding them to 777 it kind of takes this bonus functionality out :) I tried changing them to 774 but that produced the same cannot mount error as before. Is there a way of editing smb.conf to map all guests to a certain username? I could then change the owner of backup and media to guestuser:george and the permissions to 470 - so the group had more access than the owner.. or is this not possible?

---

### Post by Morbius1 on 2011-07-04
> I tried changing them to 774 but that produced the same cannot mount error as before.
You always have to have the execute bit ( octal 1 ) set on a folder or else you won't be able to open it. So the octal always has to be an odd number. For this example try the following instead: 775.

A "5" for other will allow the remote guest to open the folder ( 1 ) and read its contents ( 4 - resulting in a 4+1=5 octal ).

---

### Post by brighty22 on 2011-07-04
Didn't know that - thanks :)

Is there a way of getting ubuntu to send login details, like windows does? It all looks perfect from the windows end - I can write to all the shares. However from ubuntu, I have to login to see private (and then I have full access), and have read only to media and backup :/ Not a major issue as I can always use SSH, but simply for convenience :)

---

### Post by Morbius1 on 2011-07-04
> Is there a way of getting ubuntu to send login details, like windows does?I'm not sure what login details windows sends.
> However from ubuntu, I have to login to see private (and then I have  full access), and have read only to media and backup There's probably an elegant way to do this within one share definition but I am not an elegant person so....

You can always make another share with the exact same path but a different name and permissions. For example:
```
[MediaAdmin]
path = /share/media
guest ok = no
read only = no
valid users = george
```No guests allowed with acess including write access only to george. When george saves a file it will save as owner= george with permissions of 644. All of the guest users on the other share [Media] will be able to read the file but not edit the file.

[COLOR=Blue]EDIT:[/COLOR] If you go this route you can streamline your original [Media] share to be a classic guest / read only share definition:
```
[Media]
path = /share/media
guest ok = yes
read only = yes
```

---

### Post by brighty22 on 2011-07-04
Hmmm. Will have an experiment and post back if I find anything. Thanks for all your help :D

---

