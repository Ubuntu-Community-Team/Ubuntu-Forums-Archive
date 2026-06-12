---
title: "Different users overwrite file permissions in network"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by AfrikaDietmar on 2010-06-28
Hi,

i've setup a network with samba, all machines run ubuntu.
Network connection works fine. Everbody can login as assigned.
There are different linux/samba users. 
There is also a group.

Some folders and files i have assigned them to groups and some to unique users, this works out fine to when it comes to accessing the folder.

There is a folder where every samba user has access to. These users login with their user name and password, the problem is that when they open a file and save it, the permissions of the file get overwritten and they take over the complete ownership of that file making it inaccessible to others. 

What would be some solutions to prevent the ownership overwriting or taking over the ownership of a file ? (Even if ownership gets overwritten, its most importantly the group ownership that should remain, this gets overwritten to, and others as well.)

---

### Post by AfrikaDietmar on 2010-06-28
Well, after some digging I found I need to edit **/etc/pam.d/common-session**  and add the line 
[COLOR=Red]session    optional     pam_umask.so umask=002[/COLOR] where umask=002  is an available option.

In /etc/profile i commented out umask 022

I made the following change to my /etc/samba/smb.conf

[global]
#(I added the following to global)
obey pam restrictions = Yes
pam password change = Yes

[server]
path = /home/server/shared
public = no
browsable = yes
writeable = yes
create mask = 0774
directory mask = 0775
valid users = user1, user2, user3
write list = user1, user2, user3
#inherit permissions = yes

I commented out inherit permissions.

Even though i have applied the changes above, when i login samba user1 and open a file on server and save it, its user1 who gains complete ownership, he also overwrites group and others ownership.

Any idea how to solve his ?

---

### Post by pricetech on 2010-06-28
You said you put the users in a group.  Change the Primary Group of those users and see if that helps.  Maybe that will solve part of your dilemma anyway.

---

### Post by AfrikaDietmar on 2010-06-28
I guess my attempt above was useless concerning the masking ?

I'm kind of getting there with "force user = user1" and "force group = group1" (where user1, user2 and user3 are part of).
When i save a file across the network on that server it forces the set user to take over the permissions, since the user i use is part of the forced group, i and my colleagues can open and save to.

When I right click on the servers file (when i have logged into the server as Admin) that has been newly saved or created by a user, i see that under permissions, under group that it also saves the name of that forced user.

Is it not possible in a way to make it save as owner the forced user but for the group the groups name ?
(Or is it not possible neither necessary?)

Thats how my shared folder in smb.conf looks like:
[server]
path = /home/server/shared
public = no
browsable = yes
writeable = yes
create mask = 0774
directory mask = 0775
valid users = user1, user2, user3
write list = user1, user2, user3
force user = user1
force group = group1

---

### Post by AfrikaDietmar on 2010-06-28
> You said you put the users in a group.  Change the Primary Group of  those users and see if that helps.  Maybe that will solve part of your  dilemma anyway.I have 4 shared folders.
Folder1 is accessible by all 3 users.
Folder2 is accessible by all 3 users.
Folder3 is accessible by user2 only.
Folder4 is accessible by user2 and user3.

user2 is kind of the admin who is allowed access to all folders.

All 3 users are in group1
user2 and user3 also make up group2

I did the following on Folder1 and Folder2
```
sudo chown -R user1:group1 /home/server/Folder1
``````
sudo chown -R user1:group1 /home/im-server/Folder2
```Folder3 is accessible by only user2

Folder4 is accessible by only user2 and user3, who also make up group2
Thus i did this:
```
sudo chown -R user2:group2 /home/server/Folder4
```Likewise in smb.conf I have included in the valid users, write list, force user, and force group same infos of users and group names.

From what I understand what you are saying, i should simply remove the group ?
At the moment, if user1 who is part of group1 is in smb.conf as "force = user1" on Folder1 and all files writes and executes a file or folder, he takes over the permissions of that file - but since the other users are also part of the group he is in, they can still open that file or make changes. IF i remove group, but due to masking functions that i have applied, it would then still work, or work in a more clean way and files would keep their proper owner and group ownership ? Because right now forced user also overwrites group permission on a file or folder.

---

### Post by pricetech on 2010-06-28
> **AfrikaDietmar said:**
> From what I understand what you are saying, i should simply remove the group ?

No.  Go to System - Administration - Users and Groups.  Choose each user in turn and click the Advanced button.  Choose the Advanced tab on the screen that comes up and change, if necessary, the entry for Main group.

---

### Post by AfrikaDietmar on 2010-06-29
ok, i found it concerning the main group, do i need to reset my smb.conf file like it was before on the server, that is, remove force user, force group and leave the masking functions as i have set them ?

---

### Post by AfrikaDietmar on 2010-06-29
> ok, i found it concerning the main group, do i need to reset my smb.conf  file like it was before on the server, that is, remove force user,  force group and leave the masking functions as i have set them ?     I updated the main group as you mentioned and that worked.
I have 3 groups, and files save with correct groups now.

I didn't change my smb.conf file except if i updated the groups and valid users and write list.

I tried once to comment out this
```
 /etc/pam.d/common-session   
(removed #) session    optional     pam_umask.so umask=002  where umask=002  is an available option.

```and to remove the router symbol where commented out this one
```
In /etc/profile i commented out umask 022
```rebooted, this didn't affect the system nor make any changes to saved files across the network. Group associations remained correctly for files saved accross the network.

I believe this is due to the fact that in smb.conf force user and force group is applied as well as create mask = 0774
directory mask = 0775
so that masking function was unnecessary, am i correct ?

---

