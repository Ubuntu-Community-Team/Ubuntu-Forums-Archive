---
title: "mount -t cifs results gives mount error(13): Permission denied"
date: 2011-10-28
forum: Networking &amp; Wireless
---

### Post by roliver3 on 2011-10-28
I'm trying to mount a rw personal share that is a subdirectory of a ro share windows share on ubuntu 11.10 using the following command:

sudo mount -t cifs //[netbiosname]/users/[usershare] /mnt/[local mount point] --verbose -o username=[username],password=[mypassword],iocharset=utf8,file_mode=0777,dir_mode=0777

The directory structure on the windows share is 
domain/users/[personal_directory]  The "users" directory is read-only while the [personal_directory] is read-write to a specific user.  Below is the error that is displayed in the terminal 

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

in my syslog I see this:
kernel: [13515.946543] CIFS VFS: cifs_read_super: get root inode failed

I have spent days reading forums and bug reports trying to figure out what this might be with no luck.  Here is what is baffling me.

I can mount my user share using the exact mount command above in ubuntu 11.04, and 10.10 (these are the versions I've tried so far)  It also works in CentOS 6.  I can also mount other shares that are read-writable by everyone with the above mount.  example:


sudo mount -t cifs //[netbiosname]/techsupport /mnt/techupport -o  username=[username],password=[mypassword],iocharset=utf8,file_mode=0777,dir_mode=0777

works perfectly.  I've tried using smbfs instead of cifs each time I get the permissions error.  I've been struggling with this for a week now.  Any help would greatly be appreciated

---

### Post by collisionystm on 2011-10-28
> **roliver3 said:**
> I'm trying to mount a rw personal share that is a subdirectory of a ro share windows share on ubuntu 11.10 using the following command:

sudo mount -t cifs //[netbiosname]/users/[usershare] /mnt/[local mount point] --verbose -o username=[username],password=[mypassword],iocharset=utf8,file_mode=0777,dir_mode=0777

The directory structure on the windows share is 
domain/users/[personal_directory]  The "users" directory is read-only while the [personal_directory] is read-write to a specific user.  Below is the error that is displayed in the terminal 

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

in my syslog I see this:
kernel: [13515.946543] CIFS VFS: cifs_read_super: get root inode failed

I have spent days reading forums and bug reports trying to figure out what this might be with no luck.  Here is what is baffling me.

I can mount my user share using the exact mount command above in ubuntu 11.04, and 10.10 (these are the versions I've tried so far)  It also works in CentOS 6.  I can also mount other shares that are read-writable by everyone with the above mount.  example:


sudo mount -t cifs //[netbiosname]/techsupport /mnt/techupport -o  username=[username],password=[mypassword],iocharset=utf8,file_mode=0777,dir_mode=0777

works perfectly.  I've tried using smbfs instead of cifs each time I get the permissions error.  I've been struggling with this for a week now.  Any help would greatly be appreciated


Here is what you do.

```
sudo bash
```

```
nano /root/.servercred
```

Put

```
username=DOMAIN\username
password=password
```

CTRL + X then Y to save

```
nano /etc/fstab
```

paste this

```
//IP*OF*SERVER/SHARE /mount*location cifs sec=ntlmv2,credentials=/root/.servercred,iocharset=utf8,file_mode=0777,dir_mode=0777 0
```

CTRL + X then Y to save

```
mount -a
```

```
df
```

---

### Post by roliver3 on 2011-12-28
thanks so much for responding.  I had almost forgotten about my post.  I did as you instructed still no luck.  Below are the details

error in my syslog:
 kernel: [219032.793945] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
 kernel: [219032.793951] CIFS VFS: Send error in SessSetup = -13
 kernel: [219032.794864] CIFS VFS: cifs_mount failed w/return code = -13

.smbcredentials
username=[DOMAIN]\[username]
password=[password]

fstab entry:
//[IP of share]/users/roliv /home/roliv/network_shares/roliv cifs sec=ntlmv2,credentials=/home/roliv/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

---

### Post by roliver3 on 2011-12-28
if you have any other ideas I would be greatly in your debt

---

### Post by xclusive585 on 2012-03-22
having this same issue with 12.04 (server) daily builds. (I'm experimenting with it for the future upgrade to 12.04 for my main server)

In /etc/fstab I use this method to mount 2 machines (10.04) storage volumes:
```
//192.168.x.x/storage /mount/storage cifs credentials=/home/user/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777
//192.168.x.y/storage2 /mount/storage2 cifs credentials=/home/user/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777
```this mounts both server shares properly using a 10.04 client machine.

however using 12.04 as a client, this method will only mount one of my two [10.04 machine] network shares. there is no difference in samba setup between the two server shares, both have the same open permissions, yet only one will mount for 12.04

If I can't figure this out, I may be waiting a while to put 12.04 on my server

UPDATE:
ok, so the issue in my case was a password conflict. strangely the wide open (not pass protected) samba share didn't like that my password used in samba credentials was the same as the admin password. changing my .smbcredentials file to a different arbitrary worthless password fixed my mounting errors. Strange but hey.

---

### Post by roliver3 on 2012-05-23
Hi,
could you explain your solution a bit more?  I'm still having trouble mounting the windows share.  Are you saying that since your password listed in samba credentials (is this your .smbcredentials or credentials in /etc/samba.conf) that it let you mount?  then how did you mount the other shares using a worthless password

thanks for your help

---

### Post by cousin1avi on 2012-08-28
Delete this

---

### Post by cousinavi on 2012-08-29
Hello all,

I think I had a similar issue. I will restate my problem just in case it was different.

Firstly I am on ubuntu 12.04, and my problem turned out to be specifying the windows domain incorrectly in the credentials file. I am also using the winbind package so as to resolve netbios names rather than using ip addresses, but I don't think that effects this issue.



I could mount my share on file server using the following command,

```

sudo mount -t cifs //netbios-servername/my-share /media/mount-point -o username=my-user@my-domain,password=my-password,iocharset=utf8,file_mode=0777,dir_mode=0777

```

This would work well for manual mount, but I wanted to automatically mount using /etc/fstab. To do this I needed to specify a credential file. However, when I created the file, /root/.smbcredentials and inserted these lines:
username=my-user@my-domain
password=my-password

And ran the following command:
```

sudo mount -t cifs //netbios-servername/my-share /media/mount-point -o credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777

```
I got the error(13) message.

After editing my /root/.smbcredentials to:
username=my-user
password=my-password
domain=my-domain

I successfully mounted my network drive using the credentials file.

Hope this helps anyone with this issue!

**-avi**
PS
Don't forget to change permissions on the credentials file!
```
sudo chmod 400 /root/.smbcredentials
```

---

### Post by gomezra on 2013-01-22
I seem to be having a similar issue.  I am on Ubuntu 12.04 server trying to connect to a share on a Windows 2012 share.  I can connect to my share using smbclient, but any way that I try to connect using mount fails with the "error (13) permission denied".

I have applied chmod 777 to my mount directory.  I have tried both using a credentials file and passing the credentials directly in the mount command.  I have given "Full Control" rights to the windows domain account that I am using to mount the drive, to the share and all its subdirectories.  I have tried both cifs and smbfs (and both are installed and up-to-date).

I do have a "!" in my password, and so I am escaping that in my mount commands, otherwise I get an error, as the shell doesn't parse the command correctly.  But even if I don't put the password in the mount command and let it prompt me, I still get a permission denied error.  I'm stumped.

I found a thread related to this bug, but this shouldn't be my problem, as I do have control on the Windows side and have granted full access to the share user:

[https://bugzilla.samba.org/show_bug.cgi?id=8950](https://bugzilla.samba.org/show_bug.cgi?id=8950)

Regards,

Ricardo

---

### Post by gomezra on 2013-01-22
Okay, found the solution. 

```

sudo mount -t cifs //server-name/sharename /mnt/mntdir -o credentials=.mycredentials,sec=ntlmssp

```

I had to add the option:

sec=ntlmssp

---

### Post by DeusEx on 2013-03-15
Also had the "mount error(13): Permission denied" using CIFS.

Adding the option sec=ntlmv2 solved it!

---

### Post by MechWez on 2013-03-24
Hi guys can someone help me,
After all the parts completed from other posts, I am getting a msg that says 

Option 'file_mode0777' requires a numerical argument

what do I do to resolve this?
 Please advise.

---

### Post by prodigy_ on 2013-03-24
It's file_mode**=**0777.

---

### Post by MrNamjama on 2013-05-29
> **DeusEx said:**
> Also had the "mount error(13): Permission denied" using CIFS.

Adding the option sec=ntlmv2 solved it!

sec=ntlmv2 fixed my issue as well, thank you!

---

### Post by roliver3 on 2013-08-09
Hi all,

It's been a while, but I still am having trouble with this on 12.04.  I've tried all the suggestions but still can not connect to the hidden windows share.  I need to access my personal directory that is underneath a directory that I don't have access to.  The cifs share is 

```
\\my-domain\users\[username]  Where the "users" directory is hidden  and [username] is accessible only by my account
```


Can anyone provide an actual mount command that they used on Ubuntu 12.04 to successfully mount this type of windows share?

Here are the mount commands I've tried with not success:
sudo mount -t cifs //my-domain/users/[personal-share-name] /network_shares/personal -o username=[username],password=[password],iocharset=utf8,file_mode=0777,dir_mode=0777

```
sudo mount -t cifs //my-domain/users/[personal-share-name]  /network_shares/personal -o  username=[username@my-domain],password=[password],sec=ntlmv,iocharset=utf8,file_mode=0777,dir_mode=0777

sudo mount -t cifs //my-domain/users/[personal-share-name]  /network_shares/personal -o  username=[username],password=[password],iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlmv

sudo mount -t cifs //my-domain/users/[personal-share-name]  /network_shares/personal -o  username=[username],password=[password],iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntmssp

sudo mount -t cifs //my-domain/users/[personal-share-name]  /network_shares/personal -o  username=[my-domain\\username],password=[password],iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlmv

sudo mount -t cifs //my-domain/users/[personal-share-name]  /network_shares/personal -o  username=[my-domain\\username],password=[password],iocharset=utf8,file_mode=0777,dir_mode=0777
```

None of these worked

BTW, the error I get when trying to mount is

 ```
[39827.380877] CIFS VFS: Send error in SessSetup = -13
 [39827.380980] CIFS VFS: cifs_mount failed w/return code = -13
 [39900.273069] CIFS VFS: cifs_read_super: get root inode failed

```

---

### Post by bab1 on 2013-08-09
> **roliver3 said:**
> Hi all,

It's been a while, but I still am having trouble with this on 12.04.  I've tried all the suggestions but still can not connect to the hidden windows share.  I need to access my personal directory that is underneath a directory that I don't have access to.  The cifs share is 

```
\\my-domain\users\[username]  Where the "users" directory is hidden  and [username] is accessible only by my account
```
Can anyone provide an actual mount command that they used on Ubuntu 12.04 to successfully mount this type of windows share?

For starters, the format of the share to be mounted is //SERVER/share.  Not //SERVER/path_to_share/share.  Also you shouldn't be able to access a share that you do not have permissions to all the way down the file system hierarchy.  This means a a minimum that the "*others*" group should have eXecutable permissions on all directories in that file system.  Samba provides access to, but not ultimate authorization in the file system. > 

BTW, the error I get when trying to mount is

 ```
[39827.380877] CIFS VFS: Send error in SessSetup = -13
 [39827.380980] CIFS VFS: cifs_mount failed w/return code = -13
 [39900.273069] CIFS VFS: cifs_read_super: get root inode failed
```

I see you have used "*sec = *" on some of the mounts.  Is CIFS-utils installed instead of smbfs?  Is this an old NAS?  I've not looked back at any of the earlier old posts.  Pardon me if you have answered that before.  ;)

---

### Post by larsbo on 2014-05-30
> **cousinavi said:**
> Hello all,

I think I had a similar issue. I will restate my problem just in case it was different.

...

This would work well for manual mount, but I wanted to automatically mount using /etc/fstab. To do this I needed to specify a credential file. However, when I created the file, /root/.smbcredentials and inserted these lines:
username=my-user@my-domain
password=my-password

And ran the following command:
```

sudo mount -t cifs //netbios-servername/my-share /media/mount-point -o credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777

```
I got the error(13) message.

After editing my /root/.smbcredentials to:
username=my-user
password=my-password
domain=my-domain

I successfully mounted my network drive using the credentials file.


Same here, I got the error(13 message too because my .smbcredentials file looked like this:
```

username="domain\user"
password=pass

```

Typing my username like this worked when connecting through smbclient but apparently not using cifs

I changed the .smbcredientials and now everything works perfect:
```

username=user
domain=domain
password=pass

```

---

