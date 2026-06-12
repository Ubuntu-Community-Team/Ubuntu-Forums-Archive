---
title: "Setting up multiple shared folders on samba"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by Ravanos on 2010-12-21
I'm new at setting  up servers, and i'm trying to set up samba on to have a folder for each person in my office and have them password protected so that only that user will be able to access them. When i set the folder up for my user account it works fine but when i set it up for another user the folder does not ask for a user name or password and says there is no permission to do this. The folder works fine if i make a user and password for a system user but when i add a samba user name and password the folder no longer has permission to add or remove from it along with not asking for the user name and password.

I set the folder to be owned by the user i want to have access to the folder and modified the samba config file to have this at the end

```
[user's name]
path = user's file
available = yes
valid users = user's name
browsable = yes
public = yes
writable = yes
```Any help on what i'm doing wrong would be very appreciated

---

### Post by SeijiSensei on 2010-12-21
Usually, by default, Samba shares all the users' home directories via the [homes] share.  Try simply creating a user in Linux with "sudo adduser username" then creating a parallel Samba user with "sudo smbpasswd -a username".  The advantage of this approach is that users automatically get directories with correct permissions, i.e., owned by the user with 0700 permissions.

---

### Post by Ravanos on 2010-12-22
Thank you [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") very much for your help on this! I got this set up and now everyone will have a folder to back up there information on.

---

