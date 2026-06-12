---
title: "Accessing a folder within a windows share"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by The Ratman on 2011-02-15
[SIZE=1]I'm trying to figure out a good way to access a folder within a Windows share from an Ubuntu 10.04 computer. I work at a school which uses a Windows network. Each class has one login and a folder for their work. All the folders are in one Windows share called //fses/class$. Each class does not have access to //fses/class$ (otherwise a student from one class would be able to access another class's folder) - they only have access to their own folder e.g. //fses/class$/3b.

When I try to access a class's folder from an Ubuntu computer I get an error that //fses/class$ cannot be accessed. I've got around it for the moment by using a teacher's credentials, but that's not ideal because then the students have access to other classes' work. I also tried using the 'mount' command e.g.

[/SIZE][SIZE=1]sudo mount -t smbfs -o username=3b,password=**** //fses/class$/3b /media/3b

This did work (although I know it'd be better to use cifs and a credentials file), but only a 'superuser' can do it, and it mounts the folder for all users. I could also give the students superuser permission for the mount command, but this seems like giving them more permission than should really be necessary.

Is there any way for a user who is not a superuser to access the folder? I'd like to use something like this.

nautilus [/SIZE][SIZE=1]username=3b,password=**** smb://fses/class$/3b
[/SIZE]

---

### Post by dmizer on 2011-02-15
Take a look at the second link in my sig :)

---

### Post by The Ratman on 2011-02-16
> **dmizer said:**
> Take a look at the second link in my sig :)

Thanks - actually I already found and read your instructions when I was searching for help in the forums. I might put a mount command in fstab, but I was hoping there might be a way to directly access a folder within a Windows share without using 'mount' so any user can do it and it'll only be available for that user. Do you know of any way to do that?

---

### Post by Morbius1 on 2011-02-16
Here's one way to do this that may satisfy all your requirements - if I read your post correctly:

Create a shortcut to the remote share with this command:
```
nautilus smb://fses/class$/3b
``` It will open Nautilus to that location. 

It will ask you for a username and password if this is required and allow you to select "remember" forever if you want. It will only be accessible to the user who originally requested it.

---

### Post by The Ratman on 2011-02-16
> **Morbius1 said:**
> Here's one way to do this that may satisfy all your requirements - if I read your post correctly:

Create a shortcut to the remote share with this command:
```
nautilus smb://fses/class$/3b
``` It will open Nautilus to that location. 

It will ask you for a username and password if this is required and allow you to select "remember" forever if you want. It will only be accessible to the user who originally requested it.

Well - I tried that already but it doesn't work because user 3b has got access to //fses/class$/3b but has NOT got access to //fses/class$. It seems like the computer first tries to mount //fses/class$ and fails, so it can't get to //fses/class$/3b.

This command does actually work.

sudo mount -t smbfs -o username=3b,password=**** //fses/class$/3b /media/3b

I'm just hoping it's possible to access the folder without using the 'mount' command. It seems to me that some sort of 'mount' happens for users who are not 'superusers' when they plug in a USB flash drive or when they access a network share - I want to use that sort of 'mount' with //fses/class$/3b.[SIZE=1]
[/SIZE]

---

### Post by dmizer on 2011-02-16
> **The Ratman said:**
> I'm just hoping it's possible to access the folder without using the 'mount' command. It seems to me that some sort of 'mount' happens for users who are not 'superusers' when they plug in a USB flash drive or when they access a network share - I want to use that sort of 'mount' with //fses/class$/3b.[SIZE=1]
[/SIZE]

It is possible for a regular user to mount the folder if you put a mount command in /etc/fstab like so:
```
//fses/class$/3b /media/3b [COLOR="Red"]users,[/COLOR]username=3b,password=****,file_mode=0777,dir_mode=0777 0 0
```

The [COLOR="Red"]users[/COLOR] option allows a regular user to mount the share with the following command (no sudo):
```
mount /media/3b
```
Alternatively, you could use autofs to mount the share when the share folder is opened: [http://www.poetsma.com/dokuwiki/doku.php?id=autofs](http://www.poetsma.com/dokuwiki/doku.php?id=autofs)

---

### Post by Morbius1 on 2011-02-17
I get more confused every time I look at this thread.

Let me state what I think are the requirements:

You want //fses/class$/3b to mount at /media/3b for user 3b.
You want this to be accessible by user 3b and no one else.
The next user ( 4b ? ) needs to mount his own share ( //fses/class$/4b ?) such that only he has access to his share.

Am I even close to getting the requirements correct?

If I am then I believe the mount command should be more like this:
```
sudo mount -t cifs -o username=3b,password=xxxxxx,uid=1000,dir_mode=0700,file_mode=0600,nounix //fses/class$/3b /media/3b
```It will mount the share with ownership = 3b ( assumming 3b has a uid=1000) and with permissions allowing him read/write access and no one else. But user "4b" will have to have his own line substituting "username=4b" and "uid=1001"(?)  and the mount point (/media/4b) in the above command.

You can convert these to fstab entries that would eliminate the need to sudo.

The thing that bewilders me is the fully enumerated path to the share:
> //fses/class$/3b"class$" aside from being hidden may or may not be shared but it shouldn't matter. It would matter if it didn't have read access so the remote user couldn't open it to get to 3b. The share is "3b" and I would think that the share should be accessible at //fses/3b. I guess I'm getting confused over what exactly is being shared. Is it class$ or is it 3b.

And I'm still not sure why some derivation of smb:// doesn't work like one of the following:
```
smb://3b:password@fses/class$/3b
smb://3b@fses/class$/3b
Or even :
smb://3b@fses/3b
```

---

### Post by The Ratman on 2011-02-17
Thank you dmizer and Morbius1 for your help - I appreciate your time.

I tried dmizer's suggestion to put a command in fstab but it didn't work because the computer connects wirelessly and the wireless connection is only established AFTER fstab is executed. Anyway, I'd really like a simpler approach because in the long term I'd like to be able to do this for many different users and would rather not have to set up mount points and fstab commands for all the users on all the Ubuntu computers.

I haven't tried dmizer's suggestion to use autofs, but again it looks pretty complicated, and I'd rather not set that up for many users on many computers.

I want to be able to use a command like Morbius1 suggests - some derivation of smb:// - however none of those suggestions worked. I keep getting an error that for user 3b //fses/class$ can't be mounted. //fses/3b is not recognised at all. If I use my teacher's credentials it does work - //fses/class$ is mounted and I can access the 3b folder BUT all the other classes' folders can be accessed too.

When one of our Windows machines logs on the user has access to his or her class's folder without being able to see the other classes' folders - e.g. 3b can access //fses/class$/3b but can't list the contents of //fses/class$.

The best solution I have so far is to use sudoers to give all users permission to use the mount command - that definitely works. Then user 3b can mount //fses/class$/3b at a folder within /home/3b with the right permissions. However I'd still like to try to find the right syntax to simply use smb:// to access the folder without using 'mount'.

---

### Post by The Ratman on 2011-02-23
I'm going to go ahead and mark this thread as 'solved' now as I've found a solution, but I still feel sure there's a better way.

I ran visudo to change /etc/sudoers.
sudo visudo

I added this line to give all users permission to mount and unmount.
ALL ALL=(ALL) NOPASSWD: /bin/mount, /bin/umount

I then logged on as user 3b and created a mount point.
/home/3b/network_folder

Finally I created a launcher on the desktop with this command.
sudo mount -t smbfs -o username=3b,password=**** //fses/class$/3b /home/3b/network_folder

I'd like to improve this by using cifs instead of smbfs and by using a credentials file, but I'm happy I've got it working for the moment.

---

### Post by dmizer on 2011-02-23
> **The Ratman said:**
> I ran visudo to change /etc/sudoers.
sudo visudo

I added this line to give all users permission to mount and unmount.
ALL ALL=(ALL) NOPASSWD: /bin/mount, /bin/umount

I then logged on as user 3b and created a mount point.
/home/3b/network_folder
Yes, this is a bad idea.

> **The Ratman said:**
> Finally I created a launcher on the desktop with this command.
sudo mount -t smbfs -o username=3b,password=**** //fses/class$/3b /home/3b/network_folder

I'd like to improve this by using cifs instead of smbfs and by using a credentials file, but I'm happy I've got it working for the moment.
First of all, even though your command says smbfs, you are actually using cifs since smbfs has depreciated and is no longer a part of Ubuntu. 

If you are going to use a launcher anyway, you should certainly use /etc/fstab. All you have to do is add the "noauto" option to the /etc/fstab line and it will not mount until the mount command is run. If you add the "users" option as described earlier, then a simple command like this will work without editing the sudoers file.
```
mount /home/3b/network_folder
```

---

### Post by The Ratman on 2011-02-24
> **dmizer said:**
> Yes, this is a bad idea.


First of all, even though your command says smbfs, you are actually using cifs since smbfs has depreciated and is no longer a part of Ubuntu. 

If you are going to use a launcher anyway, you should certainly use /etc/fstab. All you have to do is add the "noauto" option to the /etc/fstab line and it will not mount until the mount command is run. If you add the "users" option as described earlier, then a simple command like this will work without editing the sudoers file.
```
mount /home/3b/network_folder
```

Thanks, dmizer - I didn't know you could use 'noauto' - that would be good with our computers because they connect wirelessly. However the reason I want to use sudoers is so I just need to do one thing on every computer, then any user can make and edit their own launchers. If I used fstab I'd have to add many entries on many computers, and update them all if anything changes e.g. usernames or passwords.

Is there any way to put an entry for a user in fstab without the password, then create a launcher to mount the share folder but when the user runs the launcher they're prompted for their password?

---

### Post by dmizer on 2011-02-24
I believe what you really need to think about is implementing network authentication with samba.

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)

The reality is that if you want things to be easy later, you'll have to deal with complicated settings now. If you don't want to deal with complicated settings now, you'll have to simply modify each computer in the network manually. Unless you create an enterprise solution (like domain control) with your samba server, there's only so much you can automate and eventually you'll have to visit each computer. This would be true if your server was Windows or if it was Mac or Linux.

You won't be able to have it both ways. Learning how to do it correctly now will have extreme advantages later.

---

### Post by The Ratman on 2011-02-24
> **dmizer said:**
> I believe what you really need to think about is implementing network authentication with samba.

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)

The reality is that if you want things to be easy later, you'll have to deal with complicated settings now. If you don't want to deal with complicated settings now, you'll have to simply modify each computer in the network manually. Unless you create an enterprise solution (like domain control) with your samba server, there's only so much you can automate and eventually you'll have to visit each computer. This would be true if your server was Windows or if it was Mac or Linux.

You won't be able to have it both ways. Learning how to do it correctly now will have extreme advantages later.

That's very good advice, dmizer. I'm setting up about a dozen Ubuntu computers connected to a Windows network, and I would really love to learn how to set them up really well with their samba servers configured correctly. You're right - it would be much better to put some time into reading that manual instead of looking for quick and easy answers.

---

