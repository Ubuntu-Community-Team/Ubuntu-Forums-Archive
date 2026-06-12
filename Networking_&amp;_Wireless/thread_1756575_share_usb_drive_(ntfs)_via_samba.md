---
title: "share usb drive (ntfs) via samba"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by Maistro_44 on 2011-05-12
Hi guys. I finally have my ubuntu up and running. 

I have a USB-drive which is often connected to my ubuntu-machine. I want to share this via Samba but I can't set the user-rights. If I try to acces the file (via windows machine) I can see the directory but if I open it it gives me: \\Computer\media\directory is not accesible. You might not have permission to use this network resource. 

I tried setting the rights but it just 'changes back immediately'. I found some posts about not being able to set rights via ubuntu on a ntfs disk. 

If I mount it via fstab it will give an error when the USB-drive is not connected. So that's no option. 

Is there a way to share this drive via my Samba server? 
Oh, by the way. I did get acces to a partition on my linux-machine, to I assume my samba-settings are correct. 
Please help this ubuntu-newbie.

---

### Post by Morbius1 on 2011-05-12
The external ntfs drive will mount with you as owner and with permissions for only you to access it. To fix that make the remote user look like you:

Add the following line to your smb.conf file:
```
force user = your-user-name
```Where you put that line depends on what method of samba sharing you used. If you used usershare ( from Nautilus ) then put it in the [global] section. If you used the classical method then add it to the share definition itself within smb.conf.

---

### Post by Maistro_44 on 2011-05-12
Morbius1 your great. That did it!
I've been trying and trying for days. 
Thanks a lot.

---

### Post by lux201 on 2012-01-18
> **Morbius1 said:**
> The external ntfs drive will mount with you as owner and with permissions for only you to access it. To fix that make the remote user look like you:

Add the following line to your smb.conf file:
```
force user = your-user-name
```Where you put that line depends on what method of samba sharing you used. If you used usershare ( from Nautilus ) then put it in the [global] section. If you used the classical method then add it to the share definition itself within smb.conf.

Thankyou! :)
after many hours trying to resolve this, finally!! this worked.

I found this is only necessary when sharing content on ntfs volumes (ie. windows drives)

---

### Post by pkerr on 2012-04-08
So fact that the NTFS file system is on a USB device makes a difference.  I have been puzzled about this for a day.

Thank you

---

### Post by apochry on 2012-04-13
> **Morbius1 said:**
> The external ntfs drive will mount with you as owner and with permissions for only you to access it. To fix that make the remote user look like you:

Add the following line to your smb.conf file:
```
force user = your-user-name
```Where you put that line depends on what method of samba sharing you used. If you used usershare ( from Nautilus ) then put it in the [global] section. If you used the classical method then add it to the share definition itself within smb.conf.

Thanks, you are the MAN!

---

### Post by hum4nb31ng on 2012-05-13
Thank you :)

---

### Post by learning99 on 2012-06-06
Thanks!

Worked perfectly.  I also struggled for two days....but learned a lot.

---

### Post by bioShark on 2012-10-14
> **Morbius1 said:**
> The external ntfs drive will mount with you as owner and with permissions for only you to access it. To fix that make the remote user look like you:

Add the following line to your smb.conf file:
```
force user = your-user-name
```Where you put that line depends on what method of samba sharing you used. If you used usershare ( from Nautilus ) then put it in the [global] section. If you used the classical method then add it to the share definition itself within smb.conf.

Thanks. I think you already know that you helped a lot of users out there, but I am sure you still like to hear from them...so, again:

Thanks a lot!

---

### Post by CannibalCat on 2012-10-26
Forgive me for being a complete moron when it comes to ubuntu, but I can't seem to edit the smb.conf file by opening it via the file menu.

Can anyone offer me step by step instructions on how to do allow other computers on my network to share my USB NTFS drives? I'm using Ubuntu 11.04 (classic desktop).

---

### Post by ahallubuntu on 2012-10-26
smb.conf is a protected file that can be edited only by an admin user.  In Ubuntu, it may be easiest to open a terminal window and type

```
sudo gedit /etc/samba/smb.conf
```

(then enter your password)

Now you'll be able to edit the file.

However, for simple sharing of files, you can simply right-click on any folder in Nautilus (the file manager) and choose the sharing option.  The very first time you do this, you'll be asked to install some stuff to make sharing work; after that, it's quick.  This is probably a lot easier for most users than trying to edit the smb.conf file.  I have seen cases where the knowledge of sharing a folder is lost on a USB hard drive, however (unless it is always plugged in).  In that case, using the smb.conf router running a Samba server directly probably is your best bet.

---

### Post by Morbius1 on 2012-10-27
I realize nobody wants to follow the rules anymore but it's not sudo gedit ... it's:
```
gksu gedit /etc/samba/smb.conf
```You can just open up nautilus and right click the folder that's the mount point for the external USB drive and share it from there but you are still going to have to edit smb.conf manualy to add the:
```
force user = your-user-name
```Add it directly under the workgroup line in smb.conf then restart samba:
```
sudo service smbd restart
```External ntfs formatted usb drives will mount with you as owner and permissions of 700. The easiest way for the remote user to gain access is for him to appear to be you which is what force user does.

---

### Post by CannibalCat on 2012-10-28
I tried as you instructed, Morbius, and I can access the internal Ubuntu HDD, and can see the NTFS USB drives but have no access to them. :/

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = workgroup
	force user = Alan

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = yes
;   browseable = yes
;   create mask = 0600
;   directory mask = 0700

[printers]
	comment = All Printers
;	browseable = yes
	path = /var/spool/samba
	printable = yes
;	guest ok = yes
;	read only = no
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers

[TV Shows]
	path = /media/TV2/TV Shows
	writeable = yes
;	browseable = yes
	guest ok = yes

[Movies]
	path = /media/Movies/Movies
	writeable = yes
;	browseable = yes
	guest ok = yes


Any advice?

---

