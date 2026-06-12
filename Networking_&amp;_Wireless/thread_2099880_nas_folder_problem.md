---
title: "nas folder problem"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by sigurnjak on 2012-12-30
I have a problem with mounting nas folder locally . I  did google the heck out of it  but no solution . 
My nas folder is  at

  smb://192.168.1.120/public/

 but to access it as local drive i mounted it like this in a fstab 

//192.168.1.120/public/ /media/public smbfs uid=guest,gid=users 0 0

It mounts during boot , puts an icon on the desktop , i can see files , but as a user can not  delete or  put files on it . As root it is no problem . So how do i give myself read and wright privileges? 
 Where did i go wrong ?

---

### Post by 2F4U on 2012-12-30
You are using the guest account on the nas to mount the share. What privileges does this account have on the nas?

---

### Post by sigurnjak on 2012-12-31
Guest has all read and wright privileges . It is default user for Patriot gear box NAS . 
When i mount it as plain samba  folder i have all rights but after i mount it locally only root can  delete and put files here, also mount locally  is much faster  data transfer then samba .

---

### Post by bsprakash on 2012-12-31
Hi Friends., 
I am having strange problem in same kind of scenario.

I am having problem with mounting.. I bought iOmega Storage box ix200.
I shared a folder from iOmega box for 10 users.

I mounted this shared drive in all 10 Virtual machines by editing /etc/fstab file. After rebooting the drive got mounted. But when a user accessing it and tries to create a new file it shows lock symbol on it.

But if i try to access this drive from Menu - Location and, from there put File server IP and do then i am able to create a file without lock symbol. It's opening read-only for all the users.

This is happening for all the users except 1 user.
If i assign that user then its working fine. Can someone guide me what may be the issue.

---

### Post by Morbius1 on 2012-12-31
> My nas folder is  at

  smb://192.168.1.120/public/

 but to access it as local drive i mounted it like this in a fstab Just so you know, when you use "smb://..." you are mounting it locally. You just may not like the mount point it automatically created.

You didn't specify what version of Ubuntu you are using:

If it's 12.10 the mount point is at:
> /run/user/your-user-name/gvfsPrior to that it was at:
> /home/your-user-name/.gvfsAnyway:
>  //192.168.1.120/public/ /media/public smbfs uid=guest,gid=users 0 0How about:
>  //192.168.1.120/public/ /media/public smbfs uid=guest,gid=users,dir_mode=0775,file_mode=0664 0 0Assuming of course that you personally are a member of the "users" group.

---

### Post by sigurnjak on 2012-12-31
Sorry for not specifying i , it is Ubuntu 12.04 ,  running gnome shell.
In next few minutes i will be near my pc and try your suggestion .

---

### Post by sigurnjak on 2012-12-31
After following this
 How about:
Quote:
//192.168.1.120/public/ /media/public smbfs uid=guest,gid=users,dir_mode=0775,file_mode=0664 0 0
Assuming of course that you personally are a member of the "users" group.

I rebooted  and my  drive did not mount , I did have to install gnome-system-tools to be able to manage groups  and am now in progress of changing permissions to public mount point  and adding my self to  users group . It may take a while since there is few hundred gigs of stuff there  and i have to go , but i will update you guys as soon as i can . 
Thanks for pointing me to a whole neW direction , 
If i do not make it back  soon , 
HAPPY NEW YEAR !!!!):P):P

---

### Post by sigurnjak on 2012-12-31
Well i did solved it ! Thanks for your help  ! 
I added new Gearbox user named andrey , edited fstab  uid to andrey and gid  same , changed smbfs to cifs ,  remounted everything ,  and i got all the rights to the drive . 

New fstab line 
//192.168.1.120/public/ /media/public cifs uid=andrey,gid=andrey  0 0

Happy new year folks !!!):P):P

---

