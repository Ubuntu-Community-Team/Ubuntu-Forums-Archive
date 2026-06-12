---
title: "SMB share not accessible by creator account"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by morningstar.fallen on 2013-02-26
Hi everyone,

I have been trying to solve this issue on my own for quite while but to  no avail. Basically I have created a samba share following this guide: 

[HTML]http://www.howtoforge.com/ubuntu-12.10-samba-standalone-server-with-tdbsam-backend[/HTML]Everything  works fine except one thing. I have created the share as user "martin",  using "sudo su" (also tried adding "sudo" at the beginning of each line  instead) and when I am logged in locally into the machine as "martin" I  cannot write to the share neither locally or over the network. But when  I created a user called "testuser" I can access the share and write  to it without a problem both locally and over the network.

I believe the problem lies somewhere in this line (which I am not able to decode completely):  

```
chmod -R ug+rwx,o+rx-w /home/shares/allusers/
```I have  experienced this problem on several different machines (including  fedora17, slitaz, and ubuntu 12.04 x64) and it's always the same: the  account that was logged in during the creation of share does not have  the permission to access it.

There were some more and some less obvious solutions that I've tried so far:

```
chgrp -R users /home/shares/allusers/
``````
find /home/shares/allusers/ -type d -exec chmod g+rwx \{} \;
```and 

```
sudo chmod 777 /home/shares/allusers/
```Now one of those above has enabled editing locally but still no joy over  the network. Unfortunately I don't know which one was it (because I am  still a bit of a noob).

Any ideas?

P.S I've attached my smb.conf for reference

---

### Post by Morbius1 on 2013-02-26
Because martin isn't a member of the "users" group?

To find out run:
```
id
```
If he is not a member of the users group add him:
```
sudo gpasswd -a martin users
```
Then logout and login again.

---

### Post by squigish on 2013-02-26
> **morningstar.fallen said:**
> I believe the problem lies somewhere in this line (which I am not able to decode completely):  

```
chmod -R ug+rwx,o+rx-w /home/shares/allusers/
```

chmod changes file permissions.  -R means apply the following changes recursively (i.e. to all subdirectories of the target and files in them)

There are three different sets of permissions stored on a linux filesystem: those for the user who owns the file, those for the group that owns the file, and those for everyone else. 

ug+rwx means "for the user and for the group that own these files, allow read, write and execute permissions"

o+rx-w means "for other users, allow read and execute permissions, and remove write permissions, if they ever existed"

chmod 777 somefile is the same as chmod ugo=rwx somefile.  You can run 
```
man chmod
``` in a terminal to learn more about chmod and permissions. 

Regarding which of those commands did the trick, my money is on the chgrp command, assuming that all of your users are indeed in the 'users' group.

What sort of setup are you hoping for? It sounds like you have a computer with a couple user accounts, on a home network where you are totally unconcerned about security. You want to have a share that anyone can read or write, with or without a password.  Is that right?

Looking at your smb.conf file, on line 102 you should uncomment (remove the leading #) the line 
```
security = user
```

If that doesn't fix the problem, post back here and I or someone else can dig deeper into the smb.conf file.

---

### Post by Morbius1 on 2013-02-26
If you follow the HowTo verbatim it will guarantee that the local server user will be denied access - locally and from the lan. What it said to do is:

Create a folder at /home/shares/allusers
Change ownership to root:users
Change permissions to 775
Create a user named tom, make him a member of the users group, and give him a samba password.
Create the share:
> [allusers]
  comment = All Users
  path = /home/shares/allusers
  valid users = @users
  force group = users
  create mask = 0660
  directory mask = 0771
  writable = yesWorks great ... for tom. Not so good for the server user martin - he can't access the local folder since he isn't a member of the users group and he can't access it as a samba client since he never gave himself a samba password. You "fixed" the local issue by setting permissions to 777 but didn't fix anything on the lan. 

You need to add martin to the samba password database:
```
sudo smbpasswd -a martin
```And you need to add martin to the users group:
```
sudo gpasswd -a martin users
```

---

### Post by morningstar.fallen on 2013-02-27
> **Morbius1 said:**
> Because martin isn't a member of the "users" group?

To find out run:
```
id
```If he is not a member of the users group add him:
```
sudo gpasswd -a martin users
```Then logout and login again.

Yes, that did the trick! The simplest solutions standing right in front of me are usually the most powerful ones and nearly always missed when I look for them... :)

---

### Post by morningstar.fallen on 2013-02-27
> **squigish said:**
> chmod changes file permissions.  -R means apply the following changes recursively (i.e. to all subdirectories of the target and files in them)

There are three different sets of permissions stored on a linux filesystem: those for the user who owns the file, those for the group that owns the file, and those for everyone else. 

ug+rwx means "for the user and for the group that own these files, allow read, write and execute permissions"

o+rx-w means "for other users, allow read and execute permissions, and remove write permissions, if they ever existed"

chmod 777 somefile is the same as chmod ugo=rwx somefile.  You can run 
```
man chmod
``` in a terminal to learn more about chmod and permissions. 

Regarding which of those commands did the trick, my money is on the chgrp command, assuming that all of your users are indeed in the 'users' group.

What sort of setup are you hoping for? It sounds like you have a computer with a couple user accounts, on a home network where you are totally unconcerned about security. You want to have a share that anyone can read or write, with or without a password.  Is that right?

Looking at your smb.conf file, on line 102 you should uncomment (remove the leading #) the line 
```
security = user
```If that doesn't fix the problem, post back here and I or someone else can dig deeper into the smb.conf file.

Thanks for explanation. I agree my smb.file must look rather messy because I was trying really hard to make sure my shares will be accessible whatever the cost. Because it is on a home network I did not care about security at all. But I realize that if that was on a company network I'd get a proper slap or get fired and fined even... :)

So do you think if I stick with the default setting from the guide below and add my own user account to the users group, everything should be fine?

[IMG]http://dl.dropbox.com/u/12299120/Screenshot.png[/IMG]

---

### Post by morningstar.fallen on 2013-02-27
> **Morbius1 said:**
> If you follow the HowTo verbatim it will guarantee that the local server user will be denied access - locally and from the lan. What it said to do is:

Create a folder at /home/shares/allusers
Change ownership to root:users
Change permissions to 775
Create a user named tom, make him a member of the users group, and give him a samba password.
Create the share:
Works great ... for tom. Not so good for the server user martin - he can't access the local folder since he isn't a member of the users group and he can't access it as a samba client since he never gave himself a samba password. You "fixed" the local issue by setting permissions to 777 but didn't fix anything on the lan. 

You need to add martin to the samba password database:
```
sudo smbpasswd -a martin
```And you need to add martin to the users group:
```
sudo gpasswd -a martin users
```

YES! Thanks again! I have managed to get as far as figuring out the first bit and allocating own **smbpasswd** to "martin" but I couldn't figure out that this account was not in the "users" group.

---

### Post by morningstar.fallen on 2013-02-27
Thank you all, it works a charm now! :KS

---

