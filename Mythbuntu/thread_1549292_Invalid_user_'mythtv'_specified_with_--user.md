---
title: "Invalid user 'mythtv' specified with --user"
date: 2010-08-09
forum: Mythbuntu
---

### Post by slaterson on 2010-08-09
i am working on setting up a mythbuntu box to connect to my tv.  its a bit of a complicated setup, however for good reason. :)  i'll try to explain the setup and the problems i am having...

first, the setup:
server in another room used for authentication and to hold a lot of media (ripped DVDs, cds, etc...)
authentication is done via LDAP and is working properly
server has a RAID 5 array for home directories and data storage
a few other computers on the network, all authenticating against the LDAP server for access to the files on the NFS share so music, videos, etc can be used on any client

as far as simple user login and permissions, things are working great (and have been for a _long_ time) with the exception of my new mythbuntu box.

problem 1:
i have got the mythbuntu box authenticating against my ldap server.  i can login as any user in the ldap directory.  i created a mythtv user & group and added it to my directory then found all files owned by user mythtv and/or group mythtv and changed the uid/gid of each file/directory to that of the uid/gid i created in my ldap directory (i had to do this due to the uid/gid that mythbuntu uses on install being already used on my other systems).

when i restart my mythbuntu box, the mythbackend will not start.  i get the message:

```
Invalid user 'mythtv' specified with --user
```

in the mythbackend.log file.  i have been scratching my head trying to figure out where this user is set.  i can start the backend successfully after logging in, it just won't start automatically.

problem 2:
i have a group named 'media'.  all videos, cds, etc files are set to read for both user and group 'media', no permissions for world.  'mythtv' user is a member of 'media', however, 'mythtv' user cannot see files owned by the group 'media' without the file being world readable.  this is very strange, as other users in the 'media' group can and the 'mythtv' user on other systems can.

any help is appreciated!

---

### Post by wyliecoyoteuk on 2010-08-09
How are the user and password set on the backend database?

---

### Post by slaterson on 2010-08-09
they were set on install, and are still set to the default of what the install chose.  i can find them in /home/mythtv/.mythtv/config.xml and /home/mythtv/.mythtv/mysql.txt.  i have tried from the command line and i can login (mysql -u mythtv -p).

---

### Post by superm1 on 2010-08-09
> **slaterson said:**
> i am working on setting up a mythbuntu box to connect to my tv.  its a bit of a complicated setup, however for good reason. :)  i'll try to explain the setup and the problems i am having...

first, the setup:
server in another room used for authentication and to hold a lot of media (ripped DVDs, cds, etc...)
authentication is done via LDAP and is working properly
server has a RAID 5 array for home directories and data storage
a few other computers on the network, all authenticating against the LDAP server for access to the files on the NFS share so music, videos, etc can be used on any client

as far as simple user login and permissions, things are working great (and have been for a _long_ time) with the exception of my new mythbuntu box.

problem 1:
i have got the mythbuntu box authenticating against my ldap server.  i can login as any user in the ldap directory.  i created a mythtv user & group and added it to my directory then found all files owned by user mythtv and/or group mythtv and changed the uid/gid of each file/directory to that of the uid/gid i created in my ldap directory (i had to do this due to the uid/gid that mythbuntu uses on install being already used on my other systems).

when i restart my mythbuntu box, the mythbackend will not start.  i get the message:

```
Invalid user 'mythtv' specified with --user
```

in the mythbackend.log file.  i have been scratching my head trying to figure out where this user is set.  i can start the backend successfully after logging in, it just won't start automatically.

So this is set in /etc/init/mythtv-backend.conf.  My guess is something with your LDAP setup is not pulling over properly when mythbackend tries to drop permissions to a particular user/group.

Debugging this one is gonna be hard.  Are you handy in C++?  I'm thinking it's going to need a patch to fix mythbackend's permissions drop stuff to work with LDAP.

> 
problem 2:
i have a group named 'media'.  all videos, cds, etc files are set to read for both user and group 'media', no permissions for world.  'mythtv' user is a member of 'media', however, 'mythtv' user cannot see files owned by the group 'media' without the file being world readable.  this is very strange, as other users in the 'media' group can and the 'mythtv' user on other systems can.

any help is appreciated!

Is the mythtv user maybe defined in both /etc/passwd and your ldap stuff by accident?

---

### Post by slaterson on 2010-08-09
> **superm1 said:**
> So this is set in /etc/init/mythtv-backend.conf.  My guess is something with your LDAP setup is not pulling over properly when mythbackend tries to drop permissions to a particular user/group.

i checked here.  you are correct, the user is specified in teh init script, which works if i start it at the command line.  this makes me believe mythbackend is starting before ldap is up.  who do i check this on mythbuntu?

> **superm1 said:**
> Are you handy in C++?

unfortunately, no.

> **superm1 said:**
> I'm thinking it's going to need a patch to fix mythbackend's permissions drop stuff to work with LDAP.

are you sure?  when i start mythbackend at the command line after logging in, it works as expected.

> **superm1 said:**
> Is the mythtv user maybe defined in both /etc/passwd and your ldap stuff by accident?

i removed all traces of 'mythtv' from /etc/passwd, /etc/group and /etc/shadow (including the - files).

i'm really stumped about my problem 2.  it makes absolutely no sense at all, some users work while others don't.

happy to do any testing you would like to help fix/troubleshoot this.  creating local users to fix this issue is kind of a pain, as i would need to partially duplicate my ldap directory on the mythbuntu box.

---

### Post by superm1 on 2010-08-09
> **slaterson said:**
> i checked here.  you are correct, the user is specified in teh init script, which works if i start it at the command line.  this makes me believe mythbackend is starting before ldap is up.  who do i check this on mythbuntu?



unfortunately, no.



are you sure?  when i start mythbackend at the command line after logging in, it works as expected.

Interesting... Is there an ldap init or upstart script that's setup in /etc/init or /etc/init.d?


> 
i removed all traces of 'mythtv' from /etc/passwd, /etc/group and /etc/shadow (including the - files).

i'm really stumped about my problem 2.  it makes absolutely no sense at all, some users work while others don't.

happy to do any testing you would like to help fix/troubleshoot this.  creating local users to fix this issue is kind of a pain, as i would need to partially duplicate my ldap directory on the mythbuntu box.
problem 2 i'm stumped too, hopefully someone else speaks up with some idears.

---

### Post by slaterson on 2010-08-09
> **superm1 said:**
> Interesting... Is there an ldap init or upstart script that's setup in /etc/init or /etc/init.d?

there isn't anything for ldap, but there is for networking...  i checked /etc/init/mythtv-backend.conf and it depends on net-device-up IFACE=lo (loopback).  since i am using ldap and it depends on the real network being up, i changed 'lo' to 'eth0' so it waits for the nic to be up and it has fixed my problem 1!  now, to figure out problem 2...

> **superm1 said:**
> problem 2 i'm stumped too, hopefully someone else speaks up with some idears.

could this be related to nfs mounting somehow?  i have an nfs export that is mounted from the mythbuntu box where all my media is stored.  works great from other systems, just not from the mythbuntu box as the mythtv user (other users work fine on this box).

getent passwd | mythtv lists the user in my ldap directory.

getent group | mythtv lists the group mythtv containing user mythtv (plus one other user) and group media (plus several other users, including, of course, the mythtv user).

---

### Post by slaterson on 2010-08-10
some more tests...

if i login as user mythtv and run the command 'groups', i only get back the group 'mythtv'.  this is odd, as 'getent group' returns five groups (users, audio, video, media and mythtv).

i have also tried running 'deluser mythtv' which tells me that entry 'mythtv' can't be removed from /etc/passwd.  i have already deleted the mythtv user from passwd, passwd-, shadow and shadow-.  is ubuntu authenticating another way?  are there other files or methods i need to look at?

when i run the command 'groups' as another user in my ldap directory, all the groups are listed as expected.

it looks like when i removed the mythtv user, i didn't do it cleanly.  how do i completely remove the mythtv user or clean up the manual removal that i already started?

---

### Post by slaterson on 2010-08-10
i got it working!  it was an error with my ldap configuration on the mythbuntu box.

in my /etc/ldap.conf file i have the entry 'nss_initgroups_ignoreusers' followed by a list of users to ignore.  mythtv was listed.  i haven't checked, but i believe this lists users to ignore so udev can get all its devices started. mythtv was in the list for some reason, i removed it from the list and voila, mythtv user is no behaving as expected.

---

### Post by superm1 on 2010-08-10
Cool, glad you got both issues fixed! :)

---

