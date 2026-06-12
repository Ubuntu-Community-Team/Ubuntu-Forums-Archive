---
title: "Permission for Samba using VPN?"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by ml_nelson on 2009-11-10
I have a Samba server set up in a small office building serving a bunch of Windows boxes. I use the simplest of all security schemes for Windows to logon where the Guest account has read & write permissions.
 
I find that I have a problem if I remotely connect via VPN from home into one of the Windows machines & then try to use the NET commad to map a drive on the home windows machine. Connecting this way, the remote user has only read privileges.
 
So, I got the bright idea that I need to use the logon/password for a user that has full privileges. In fact the user is an administrtor. So the Net command is like so... 
 
net use z: [\\192.168.0.120\public]("file://\\192.168.0.120\public") /user:myuser mypassword.
 
Still only have read-only access for the VPN connected Windows user.
 
What am I missing? My older Samba server doesn't have this issue.
 
Mike

---

### Post by dvlchd3 on 2009-11-10
This is kind of a guess from my limited knowledge of Samba shares, however, I was always under the impression you had to define the rights in the samba config file.  Just because the user you are using to connect has the rights on the machine, does not necessarily mean the user will have the same rights through the Samba share.

With that being said, are the rights defined correctly in the Samba config file? (/etc/samba/smb.conf)  Or by some other means?  I know there are ways to accomplish this graphically.

---

### Post by dmizer on 2009-11-10
Please post your /etc/samba/smb.conf file.

---

### Post by ml_nelson on 2009-11-11
> **dmizer said:**
> Please post your /etc/samba/smb.conf file. The file is actually unmodified from Ubuntu's default with the exception that I changed the name of the workgroup to match that which is in use in the office.

---

### Post by dmizer on 2009-11-11
Ok, take a look at the smb.conf edits I suggest in the 6th link in my sig. Specifically, both fixes outlined in "Problem 2" and "Problem 3 - Jaunty/Karmic"

Also, make sure that IPtables is empty. If you are unsure, please post the output of:
```
sudo iptables -L
```

---

### Post by ml_nelson on 2009-11-11
More info...
 
Here is what I'm seeing; 
 
As the VPN user; I have read-write access to the /public folder, but not to folders in that folder (example, for /public/temp I have read-only access)
 
Now if I go to the Ubuntu box; & log in as the default user, I actually have exacly the same permissions as the VPN user.
 
The solution would seem simple from here, just adjust the permission for the default user at the Ubuntu box & the VPN user will probably be the same. 
 
So, I just need to adjust the permissions so that they apply to all the nested folders. Problem is I can't figure out how to do that. If I look at the permissions of /public. I can see & edit them. But, when I go one deeper (example; /public/temp) the Permissions tab says I'm not the owner & can't modify permissions.
 
Confused!

---

### Post by ml_nelson on 2009-11-11
I got it.... The VPN user needs to logon the same way as the user that created the files & structure. A user who logs-on as..... 
 
**net use z: **[[COLOR=#444444]**\\192.168.0.120\public**[/COLOR]]("file://\\192.168.0.120\public")** /user:myuser mypassword**
 
Can't modify files of a user who logs-on as...
 
**net use z: **[**[COLOR=black]\\192.168.0.120\public[/COLOR]**]("file://\\192.168.0.120\public") (taking advantage of guest access)

---

