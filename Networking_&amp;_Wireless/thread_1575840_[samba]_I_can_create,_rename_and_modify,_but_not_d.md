---
title: "[samba] I can create, rename and modify, but not delete"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by Pri0 on 2010-09-16
Hi all

First of all I'd like to thank all the helpful members of this forum. A week ago I didn't know anything about linux, and I'm pretty sure that through this forum entirely I've gone on to setup an Ubuntu Server with Samba, which I've set up at the office here.

I'm having a strange issue. I've created an Archives folder which I've shared with everyone. The idea is that only I can create or modify any of the contents of this folder, and everyone else can only read and execute. 

At first what I was doing was using:
```
sudo chown -R bob archives
sudo chgrp -R staff archives
sudo chmod -R 750 archives
```

I'm a member of the staff group.

If I'm correct, this should allow only me to be able to modify the contents of any folder within Archives, yet I can't delete any files? I can create, modify and rename files, but not delete them. 

[img]http://img824.imageshack.us/img824/5936/capturemv.jpg[/img]

Here's smb.conf, I've just edited out the company name and such...

```
[global]
	workgroup = COMPANYNAME
	netbios name = STORAGE
	server string = Storage Server
	security = user
	username map = /etc/samba/smbusers
	map to guest = Bad User
	guest account = nobody	

[homes]
	path = /companyname/homes/%S	
	valid users = %S
	read only = No
	browseable = No

[Utilities]
	path = /companyname/utilities
	guest ok = No
	writeable = No
	write list = bob
	create mask = 0770	
	force create mode = 0770
	directory mode = 0770
	force directory mode = 0770
	
[Scratch]
	path = /companyname/scratch
	guest ok = No
	writeable = Yes
	create mask = 0770
	force create mode = 0770
	directory mode = 0770
	force directory mode = 0770

[Common]
	path = /companyname/common
	guest ok = No
	writeable = Yes
	create mask = 0770
	force create mode = 0770
	directory mode = 0770
	force directory mode = 0770	

[Archives]
	path = /companyname/archives
	guest ok = No
	writeable = No
	write list = bob
	create mask = 0770
	force create mode = 0770
	directory mode = 0770
	force directory mode = 0770
``` 

As you'll see in the Archives section, I've had to force a workaround, but surely it should work without having to add myself to a write list? I'm the owner of the folders, I should be able to delete files from them surely?

The only reason I'm here is because I set up the exact same thing on an Ubuntu Desktop install and I didn't need to use any of this write list, create mask, create mode and directory mode stuff to get the behavior I needed. Is Server different/more secure in this respect that I have to explicitly state *everything*?

Another strange thing I noticed, if I didn't use everything after *write list* in the Archives section, was that if I created, say, a text file in the Archives root folder, it would assign the following rights...

```
-rwxrwxr-- 1 bob bob    0 2010-09-16 15:42 test.txt
```

Is there a way to force the group to be staff on created files? Obviously there's *force group* in the smb.conf, but is that the only way? And why can 'other' users write to the folder if I used chmod 750?

Excuse the long message, thorough is my middle name. Like I said, the only reason this is bugging me is because I didn't have these issues with Ubuntu Desktop, despite essentially copying the smb.conf, smbusers and relevant folders to the server. The only difference between that and my current setup is that I'm using the 'staff' group as opposed to adding everyone to 'users', and my unix password changed to something a bit more secure.

Please help me! As it stands my setup works, but I feel that I'm not completely understanding something.

---

### Post by dmizer on 2010-09-16
Windows and Linux do not share the same methods for local file permissions. This means that the samba server essentially translates Windows file permissions into Linux file permissions. 

I am not sure if there is a better way, but the way I have always done it is to use the force group option. If you use the force group option, then you will probably be able to do this
```
[Common]
    path = /companyname/common
    guest ok = No
    writeable = Yes
    force group = +staff
```
However, for the archives, you should change both user and group to bob (above you showed chgrp staff on archives). Once you've changed the permissions on all the files locally, it should work like this as long as you are logging in from Windows as user bob.
```
[Archives]
    path = /companyname/archives
    guest ok = No
    writeable = No
    write list = bob
    force group = +bob
```

Note on the plus sign
```
           In Samba 2.0.5 and above this parameter has extended functionality
           in the following way. If the group name listed here has a ´+´
           character prepended to it then the current user accessing the share
           only has the primary group default assigned to this group if they
           are already assigned as a member of that group. This allows an
           administrator to decide that only users who are already in a
           particular group will create files with group ownership set to that
           group. This gives a finer granularity of ownership assignment. For
           example, the setting force group = +sys means that only users who
           are already in group sys will have their default primary group
           assigned to sys when accessing this Samba share. All other users
           will retain their ordinary primary group.

```
In other words, without the plus sign, any file created by anyone will be given the staff group even if they are not a member of the staff group.

Alternatively, you could do some reading in man smb.conf about the username map option. This could resolve a lot of things for you as well.

---

### Post by Karim_992 on 2012-02-29
guys i need your help and i really appreciate it. 

i am a windows system administrator and lately my manager want me to change the system to Unix.

i still studding and reading, what i really need is exactly this case i need to configure my Samba server permissions to allow read,write but not delete for a group or user. 

[[ i am configuring a file server ]] 
i need this option for groups so users can access the departments files and modify them and get the data they need but not to delete this files 

The scenario i am trying to build is 
client X [read,modify but not delete files or subfolders]
Group X [read,modify but not delete files or sub folder]
root[read,modify and delete] i think this is the normal case for the root

---

### Post by bab1 on 2012-02-29
> **Karim_992 said:**
> guys i need your help and i really appreciate it. 

i am a windows system administrator and lately my manager want me to change the system to Unix.

i still studding and reading, what i really need is exactly this case i need to configure my Samba server permissions to allow read,write but not delete for a group or user. 

[[ i am configuring a file server ]] 
i need this option for groups so users can access the departments files and modify them and get the data they need but not to delete this files 

The scenario i am trying to build is 
client X [read,modify but not delete files or subfolders]
Group X [read,modify but not delete files or sub folder]
root[read,modify and delete] i think this is the normal case for the root

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for setting the linux filesystem extended permissions.

You should start your own thread.  Forum policy is to *not* reply to threads older than 1 year.  This thread is 1.5 years old.

---

### Post by nothingspecial on 2012-02-29
[IMG]http://img696.imageshack.us/img696/7058/necrov.png[/IMG]

---

