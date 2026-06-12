---
title: "Help with Samba share please"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by Schmidty1913 on 2009-02-02
I was wondering if my smb.conf file was configured correctly for what i want it to do

i wanted the home directories to only be accessable to their owners
i wanted website to be only seen by mike and accessable by mike
i wanted sharedfiles to be accessable by anyone with write permissions only (no delete permissions) with or with out a username on my server and the user mike to have write and delete access to it



[homes]
comment = home directories
valid users = %S
read only = no
browseable = no

[Website]
comment = Website
path = /var/www/
valid users = mike
write list = mike
browseable = no

[SharedFiles]
comment = sharedfiles
read only = yes
guest only = yes
guest ok = yes
path = /home/samba/

---

### Post by lykwydchykyn on 2009-02-02
> **Schmidty1913 said:**
> I was wondering if my smb.conf file was configured correctly for what i want it to do

i wanted the home directories to only be accessable to their owners

You should have that.
> 
i wanted website to be only seen by mike and accessable by mike

It should be accessible by mike; however, nobody can see it because it cannot be browsed.  mike would have to connect to it directly.  
> 
i wanted sharedfiles to be accessable by anyone with write permissions only (no delete permissions) with or with out a username on my server and the user mike to have write and delete access to it

This one's a bit tricky, and your config doesn't do that.  Actually, it takes more than just the config file to accomplish this.  Here's what you do:
 - Change "read only" to "no"
 - Change the permissions on the directory /home/samba "wide open" (777), allowing anyone to read/write.
 - Set the "sticky bit" on the directory (chmod +t /home/samba).  This allows people to write to any file, but only delete files they own.
 - Set "force user: mike" on the share.  This will make all uploaded files owned by mike.

The net result is, any file uploaded is owned by mike, and only mike (or root) can delete the files.  But anyone can write to any file or create any file in the directory.

---

### Post by Schmidty1913 on 2009-02-02
Should i keep guest ok = yes and guest only = yes?

---

### Post by lykwydchykyn on 2009-02-02
> **Schmidty1913 said:**
> Should i keep guest ok = yes and guest only = yes?

You should keep "guest ok=yes".  But if you want to connect to the share as mike (and thus be able to delete files), you want to remove "guest only".  Because if that's "yes", then you cannot connect to the share as mike and you won't be able to delete files.  You'd have to log in to the server locally (through ssh or at the console) to delete anything.

---

### Post by Schmidty1913 on 2009-02-02
windows xp users connecting are being asked for a username and password still when trying to connect to it throught the ip address (ex. \\192.168.1.1\) do they have to type \\192.168.1.1\SharedFiles ????

---

### Post by lykwydchykyn on 2009-02-02
Controlling how Windows XP responds to various samba security settings has always been a mystery to me.  Are the XP clients configured for "simple file sharing"?

---

### Post by capscrew on 2009-02-02
> **Schmidty1913 said:**
> windows xp users connecting are being asked for a username and password still when trying to connect to it throught the ip address (ex. \\192.168.1.1\) do they have to type \\192.168.1.1\SharedFiles ????

When you use **\\server_ip** you are asking to be authenticated to the server only.  If you use **[COLOR="Green"]\\server_ip\samba_share[/COLOR]** you are authenticating using the share directives. You are using security=user; correct?.  If you have the security set to security=share then you are only using the file permissions (OS) of the share.

---

### Post by Schmidty1913 on 2009-02-02
> 
[global]
    netbios name = MediaCenter
    server string = "MediaCenter"
    workgroup = WORKGROUP
    username map = /etc/samba/smbusers
    security = user
[homes]
	comment = Home Directories
	valid users = %S
	read only = No
	browseable = No

[Website]
	comment = Website
	path = /var/www/
	valid users= mike
	write list = mike
	browseable = yes

[SharedFiles]
	comment = SharedFiles
	browseable = yes	
	read only = no
	force user: mike
	guest ok = yes
	path = /home/samba/


Im still having the same problem where it is asking xp users to type a user name and password... any ideas?

---

### Post by dmizer on 2009-02-02
You need to give the XP users accounts on the Ubuntu server:
```
sudo useradd -s /bin/true mike
sudo smbpasswd -L -a mike
sudo smbpasswd -L -e mike
```

Make sure the password is exactly the same as what they use to log in.

---

### Post by Schmidty1913 on 2009-02-02
thats not what i want, i want an open share where anyone can log into it without entering a password...

---

### Post by capscrew on 2009-02-02
> **Schmidty1913 said:**
> thats not what i want, i want an open share where anyone can log into it without entering a password...


You have misunderstood what dmizer has suggesting.  Adding a user to the smbpasswd database is what you need to do to have Samba work the way you want it to.

When a user attempts to access a share the Samba daemon checks to see if the user has a Linux login and is in the smbpasswd database.  If the user is in that database (or mapped to a user in the database via the smbusers file) then access is granted without any further authorization.



Follow the advice of dmizer and see what happens.

Edit: When you say :> ...anyone can log into it... You are implying that one has to login.  This means there has to be an account to log into.  If you want guest access then you need to define the guest in the global section of the smb.conf file and allow guests in the share section.

---

