---
title: "Help setting up Samba shares"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by tsunamikitsune on 2010-10-11
I currently have a Ubuntu server all set up with some raided hard drives and I'm ready to do some filesharing with Samba. I've managed to get everything up and running, even find the server on my Windows 7 computer, but I'm not quite sure how to configure it the way I'd like. A little help would be greatly appreciated.

First off, I'd like to have a login and home folder for each member of the household. So, when I login, I see all the folders that everyone can access, plus my home folder, which is specific to me. For example:

Ryan logs in and sees two folders: Ryan (/mnt/raid/home/ryan) and Public (/mnt/raid/public). Chelsea logs in and sees two folders: Chelsea (/mnt/raid/home/chelsea) and Public (/mnt/raid/public).

Is this a possibility? I'm not too sure how to set it up if it is.

Next, I could use some instruction on permissions. If I wanted one folder to be visible and writable to all, one folder to be visible to all and only writable to some, and one folder only visible to some, how would I go about setting these up?

Lastly, I have a question that's not so much Samba-related (at least I don't think it is), but I'm some clarification would be nice. While I was testing my ability to read and write to the server, I noticed the speed of writing to the server was about 11 MB/s. Is this normal for a wired transfer over LAN? If not, is there any way to speed things up a bit?

Sorry for all the questions, hopefully the answers aren't too hard to come by. Thanks in advance to anyone who's willing to help me out! :D

---

### Post by RichardUK on 2010-10-11
The smb.conf file starts out with what you need for user folders to be shared based on who is logged in, but it is just commented out.

Copied from mine but never tried it but it should work, why else would it be in there. ;)

```
#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

```

---

### Post by tsunamikitsune on 2010-10-11
Alright, I uncommented those lines and now I can see my home folder when I open the server folder on my Windows 7 computer.

The first time I did so, I was asked for a login, which I entered and it now automatically shows my home folder, which leads me to believe it's working. Is there a way to clear my login in Windows 7 and use a different one to test all the accounts, though? I want to make sure everything checks out before I let everyone on.

**EDIT:** I managed to work around this by creating new shares (which had not yet saved my username and password), but now I'm having issues. The "valid users = %S" line doesn't seem to work, forcing me to add my username if I want to access the share. If I change the valid users line to another user and try to login with their name and password, I get a message about it being unaccessible and my not having permission to access it. 

Help? Please?

---

