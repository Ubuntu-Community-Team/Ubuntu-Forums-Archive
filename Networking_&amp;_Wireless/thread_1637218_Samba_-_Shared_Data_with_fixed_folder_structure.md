---
title: "Samba - Shared Data with fixed folder structure"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by yameen101 on 2010-12-04
We want to fix our data folders structre in Samba, for example our folders would be like as Data/Group A/2010 /A
 
We want all our users can work only in folder A and no one can create any files in data, GroupA, 2010 folders. Similarly no one can delete these basic folders. However users can create further folders in A as required.
 
Is this possible in samba?

---

### Post by Morbius1 on 2010-12-04
> We want to fix our data folders structre in Samba, for example our folders would be like as Data/Group A/2010 /A
 
We want all our users can work only in folder A and no one can create  any files in data, GroupA, 2010 folders. Similarly no one can delete  these basic folders. However users can create further folders in A as  required.
 

Sorry, your requirements are not clear.

Is /A a subdirectory of /Data/Group A/2010 ?
Or is /A a stand alone directory under / ?

Do you want to grant any or possibly read only access to /Data/Group A/2010 ?

Do you want /A to allow add/delete access ?

And what users? All users - as in guest access. Or only a subset of users? Do you want the remote user to authenticate or not?

Your post needs more clarification.

---

### Post by yameen101 on 2010-12-04
Dear Morbius1
Many thanks for your reply
 
Yes A is the sub-directory of /Data/GroupA/2010.
 
We want to restrict Users to delete these 4 folders i.e. Data/GroupA/2010/A. However can create, modify or delete any document/folder in A. Folder A is the only workable folders for users.
 
Our network in LAN based and no remote/guest users. Users are authenticated through IP addresses.
 
 
Thanks again.

---

### Post by Morbius1 on 2010-12-04
I still do not think I understand fully what you want but it sounds like you want to create a simple guest share at "A":

If you are running Gnome you can user Samba Usershares through Nautilus or you can create a Classic Samba share. For a classic samba share you would add the following share definition at the end of /etc/samba/smb.conf:
> [ShareA]
path = /Data/GroupA/2010/A
read only = No
guest ok = yes
force user = nobodySave smb.conf and in a terminal restart samba:
```
sudo service smbd restart
```Now you will have to modify the permissions on the target directory to allow remote guests to have permissions to read and write to that directory:
```
sudo chmod 0777 /Data/GroupA/2010/A
```Now you need to restart samba:
```
sudo service smbd restart
```The remote guest user will be able to add to, delete from, or modify anything in that share. "force user = nobody" will ensure that every file will be owned by "nobody" so that all remote users will appear to own everyting in that share.

---

