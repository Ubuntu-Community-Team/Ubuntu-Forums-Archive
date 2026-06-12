---
title: "Can't write to network share"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by Sauro on 2010-04-22
Hi can anyone give me some advice or point me in the right direction ?

I have managed to auto mount 6 windows network shares, I can access them and have read access but I'm unable to write to the shares. I have checked all the settings on the networked device and can access via a windows machine and write to the shares. 

I have used the following lines in my fstab config 

//192.168.1.1/share /home/user/pics cifs username=user,password=password 0 0

As far as I can tell that should work, I have noticed that when they are not mounted the mount points have the user as the owner and group with permissions set to 755, but when it is mounted they change to root for both owner and group.

i'm new to Linux and assume that it has something to do with me creating the mount points in the home folder ?

*EDIT* I've just tried making a mount point in /media and have the same problem when mounting to that, when i use the command line and cd to the share I can write to the share using sudo, is there a way I can enable my user account to have permission to write using the GUI ?

---

### Post by Sauro on 2010-04-22
fixed :D

fstab entry should have included uid=user,gid=users


//192.168.1.1/share /home/user/share cifs username=user,password=password,uid=user,gid=
users 0 0

---

