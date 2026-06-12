---
title: "Share Access"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by wabbit46 on 2009-11-27
I have recently upgraded from Ununtu 8.04 to Ubuntu 9.10. I had a directory under /user/local to back up my Windows (Vista) computer.

This worked well on Ububtu 8.04 but on Ubuntu 9.10 I cannot write to this directory. I have tried changing ownership of the directory and it's location without any results. 

Is there something I need to do to write to a Ubuntu share ?

---

### Post by dmizer on 2009-11-27
Please post the contents of /etc/samba/smb.conf

---

### Post by wabbit46 on 2009-11-27
I cannot save the smb.conf file or post it

---

### Post by dmizer on 2009-11-27
This command should help:
```
cat /etc/samba/smb.conf
```

---

### Post by wabbit46 on 2009-11-27
Thanks for the advice here is the smb.conf file :-

```
# 
# Sample configuration file for the Samba suite for Debian GNU/Linux. 
# 
# 
# This is the main Samba configuration file. You should read the 
# smb.conf(5) manual page in order to understand the options listed 
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example 
# 
# Some options that are often worth tuning have been included as 
# commented-out examples in this file. 
#  - When such options are commented with ";", the proposed setting 
#    differs from the default Samba behaviour 
#  - When commented with "#", the proposed setting is the default 
#    behaviour of Samba but the option is considered important 
#    enough to be mentioned here 
# 
# NOTE: Whenever you modify this file you should run the command 
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file 
# "smb.conf.master" and create the "real" config file with 
# testparm -s smb.conf.master >smb.conf 
# This minimizes the size of the really used smb.conf file 
# which, according to the Samba Team, impacts performance 
# However, use this with caution if your smb.conf file contains nested 
# "include" statements. See Debian bug #483187 for a case 
# where using a master file is not a good idea. 
# 

#======================= Global Settings ======================= 

[global] 

## Browsing/Identification ### 

# Change this to the workgroup/NT-domain name your Samba server will part of 
   workgroup = WORKGROUP 

usershare owneronly = false 

# server string is the equivalent of the NT Description field 
   server string = %h server (Samba, Ubuntu) 

# Windows Internet Name Serving Support Section: 
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server 
#   wins support = no 

# WINS Server - Tells the NMBD components of Samba to be a WINS Client 
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both 
;   wins server = w.x.y.z 

# This will prevent nmbd to search for NetBIOS names through DNS. 
   dns proxy = no 

# What naming service and in what order should we use to resolve host names 
# to IP addresses 
  name resolve order = lmhosts host wins bcast 

#### Networking #### 

# The specific set of interfaces / networks to bind to 
# This can be either the interface name or an IP address/netmask; 
# interface names are normally preferred 
;   interfaces = 127.0.0.0/8 eth0 

# Only bind to the named interfaces and/or networks; you must use the 
# 'interfaces' option above to use this. 
# It is recommended that you enable this feature if your Samba machine is 
# not protected by a firewall or is a firewall itself.  However, this 
# option cannot handle dynamic or non-broadcast interfaces correctly. 
;   bind interfaces only = yes 



#### Debugging/Accounting #### 

# This tells Samba to use a separate log file for each machine 
# that connects 
   log file = /var/log/samba/log.%m 

# Cap the size of the individual log files (in KiB). 
   max log size = 1000 

# If you want Samba to only log through syslog then set the following 
# parameter to 'yes'. 
#   syslog only = no 

# We want Samba to log a minimum amount of information to syslog. Everything 
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log 
# through syslog you should set the following parameter to something higher. 
   syslog = 0 

# Do something sensible when Samba crashes: mail the admin a backtrace 
   panic action = /usr/share/samba/panic-action %d 


####### Authentication ####### 

# "security = user" is always a good idea. This will require a Unix account 
# in this server for every user accessing the server. See 
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html 
# in the samba-doc package for details. 
  security = share 

# You may wish to use password encryption.  See the section on 
# 'encrypt passwords' in the smb.conf(5) manpage before enabling. 
   encrypt passwords = true 

# If you are using encrypted passwords, Samba will need to know what 
# password database type you are using.  
   passdb backend = tdbsam 

   obey pam restrictions = yes 

# This boolean parameter controls whether Samba attempts to sync the Unix 
# password with the SMB password when the encrypted SMB password in the 
# passdb is changed. 
   unix password sync = yes 

# For Unix password sync to work on a Debian GNU/Linux system, the following 
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for 
# sending the correct chat script for the passwd program in Debian Sarge). 
   passwd program = /usr/bin/passwd %u 
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* . 

# This boolean controls whether PAM will be used for password changes 
# when requested by an SMB client instead of the program listed in 
# 'passwd program'. The default is 'no'. 
   pam password change = yes 

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections 
   map to guest = bad user 

########## Domains ########### 

# Is this machine able to authenticate users. Both PDC and BDC 
# must have this setting enabled. If you are the BDC you must 
# change the 'domain master' setting to no 
# 
;   domain logons = yes 
# 
# The following setting only takes effect if 'domain logons' is set 
# It specifies the location of the user's profile directory 
# from the client point of view) 
# The following required a [profiles] share to be setup on the 
# samba server (see below) 
;   logon path = \\%N\profiles\%U 
# Another common choice is storing the profile in the user's home directory 
# (this is Samba's default) 
#   logon path = \\%N\%U\profile 

# The following setting only takes effect if 'domain logons' is set 
# It specifies the location of a user's home directory (from the client 
# point of view) 
;   logon drive = H: 
#   logon home = \\%N\%U 

# The following setting only takes effect if 'domain logons' is set 
# It specifies the script to run during logon. The script must be stored 
# in the [netlogon] share 
# NOTE: Must be store in 'DOS' file format convention 
;   logon script = logon.cmd 

# This allows Unix users to be created on the domain controller via the SAMR 
# RPC pipe.  The example command creates a user account with a disabled Unix 
# password; please adapt to your needs 
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u 

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system 
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u 

# This allows Unix groups to be created on the domain controller via the SAMR 
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g 

########## Printing ########## 

# If you want to automatically load your printer list rather 
# than setting them up individually then you'll need this 
#   load printers = yes 

# lpr(ng) printing. You may wish to override the location of the 
# printcap file 
;   printing = bsd 
;   printcap name = /etc/printcap 

# CUPS printing.  See also the cupsaddsmb(8) manpage in the 
# cupsys-client package. 
;   printing = cups 
;   printcap name = cups 

############ Misc ############ 

# Using the following line enables you to customise your configuration 
# on a per machine basis. The %m gets replaced with the netbios name 
# of the machine that is connecting 
;   include = /home/samba/etc/smb.conf.%m 

# Most people will find that this option gives better performance. 
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html 
# for details 
# You may want to add the following on a Linux system: 
#         SO_RCVBUF=8192 SO_SNDBUF=8192 
#   socket options = TCP_NODELAY 

# The following parameter is useful only if you have the linpopup package 
# installed. The samba maintainer and the linpopup maintainer are 
# working to ease installation and configuration of linpopup and samba. 
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' & 

# Domain Master specifies Samba to be the Domain Master Browser. If this 
# machine will be configured as a BDC (a secondary logon server), you 
# must set this to 'no'; otherwise, the default behavior is recommended. 
#   domain master = auto 

# Some defaults for winbind (make sure you're not using the ranges 
# for something else.) 
;   idmap uid = 10000-20000 
;   idmap gid = 10000-20000 
;   template shell = /bin/bash 

# The following was the default behaviour in sarge, 
# but samba upstream reverted the default because it might induce 
# performance issues in large organizations. 
# See Debian bug #368251 for some of the consequences of *not* 
# having this setting and smb.conf(5) for details. 
;   winbind enum groups = yes 
;   winbind enum users = yes 

# Setup usershare options to enable non-root users to share folders 
# with the net usershare command. 

# Maximum number of usershare. 0 (default) means that usershare is disabled. 
;   usershare max shares = 100 

# Allow users who've been granted usershare privileges to create 
# public shares, not just authenticated ones 
   usershare allow guests = yes 

#======================= Share Definitions ======================= 

# Un-comment the following (and tweak the other settings below to suit) 
# to enable the default home directory shares.  This will share each 
# user's home directory as \\server\username 
[homes] 
   comment = Home Directories 
   browseable = yes 

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

# Un-comment the following and create the netlogon directory for Domain Logons 
# (you need to configure Samba to act as a domain controller too.) 
;[netlogon] 
;   comment = Network Logon Service 
;   path = /home/samba/netlogon 
;   guest ok = yes 
;   read only = yes 
;   share modes = no 

# Un-comment the following and create the profiles directory to store 
# users profiles (see the "logon path" option above) 
# (you need to configure Samba to act as a domain controller too.) 
# The path below should be writable by all users so that their 
# profile directory may be created the first time they log on 
;[profiles] 
;   comment = Users profiles 
;   path = /home/samba/profiles 
;   guest ok = no 
;   browseable = no 
;   create mask = 0600 
;   directory mask = 0700 

[Vista Backups] 
   comment = Vista Backups 
   path = /home/roger/Vista_Backups 
   guest ok = yes 
   browseable = yes 
   create mask = 0777 
   directory mask = 0777 

[printers] 
   comment = All Printers 
   browseable = yes 
   path = /var/spool/samba 
   printable = yes 
   guest ok = no 
   read only = no 
;  create mask = 0700 

# Windows clients look for this share name as a source of downloadable 
# printer drivers 
[print$] 
   comment = Printer Drivers 
   path = /var/lib/samba/printers 
   browseable = yes 
   read only = yes 
   guest ok = yes 
# Uncomment to allow remote administration of Windows print drivers. 
# You may need to replace 'lpadmin' with the name of the group your 
# admin users are members of. 
# Please note that you also need to set appropriate Unix permissions 
# to the drivers directory for these users to have write rights in it 
;   write list = root, @lpadmin 

# A sample share for sharing your CD-ROM with others. 
;[cdrom] 
;   comment = Samba server's CD-ROM 
;   read only = yes 
;   locking = no 
;   path = /cdrom 
;   guest ok = yes 

# The next two parameters show how to auto-mount a CD-ROM when the 
#	cdrom share is accesed. For this to work /etc/fstab must contain 
#	an entry like this: 
# 
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0 
# 
# The CD-ROM gets unmounted automatically after the connection to the 
# 
# If you don't want to use auto-mounting/unmounting make sure the CD 
#	is mounted on /cdrom 
# 
;   preexec = /bin/mount /cdrom 
;   postexec = /bin/umount /cdrom
```

---

### Post by wabbit46 on 2009-12-26
I have tried a re-install of Ubuntu.I cannot see the ubuntu computer on the Vista one. However I can see the Vista computer from the Ubuntu one.

When I examine the network from the Ubuntu computer it does not reveal itself.

Also I no longer have an Internet connection on the ubuntu computer

I have tried setting the IP address via network connections but it does not make any difference. I cannot set the default gateway to point to the Vista box.

Also the /etc/network/interfaces file does not get modified. 

I have done this manually but it has no effect.

Is this a problem with this version of Ubuntu and should I revert back to version 8.04 ?

---

### Post by ELGL on 2009-12-26
That the file /etc/network/interfaces doesn't get modified is right. Ubuntu (with gnome) uses network-manager for the configuration of network interfaces as long as /etc/network/interfaces doesn't contain configuration for the interface you want to configure. You can use either method of configuring the network, but when you set the config in /etc/network/interfaces the network-manager (graphical tool) will do nothing for that interface.

When you edit /etc/network/interfaces, you have to run the 'sudo /etc/init.d/networking restart' command after that. That way it applies the changes.

The default gateway for Ubuntu should point to the router you're using if you have one. I don't know what your network looks like, but the default gateway is the address it sends all traffic to that's outside the local subnet. So to access an IP address on the local network (eg. your vista machine) a default gateway isn't necessary. From what you're saying that Ubuntu doesn't have an internet connection, it's probably because the default gateway isn't configured correctly.
When your Vista machine is sharing the internet connection with the rest of the network you should enter the IP address of the Vista machine as the default gateway.

There is no share definition in your smb.conf. You should create a share for it, in another post I've made a quick how to. I hope it helps.

[http://ubuntuforums.org/showthread.php?p=8561354#post8561354](http://ubuntuforums.org/showthread.php?p=8561354#post8561354)

good luck!

---

### Post by dmizer on 2009-12-27
First, take a look at teh 6th link in my sig.

---

### Post by Morbius1 on 2009-12-27
If you get your network connection problem resolved please post your smb.conf again. There was a share definition buried in there but you had to read through many many lines of comments to find it. You also had share level security enabled which some Windows clients have problems with. Since you reinstalled it's best to re-post your smb.conf. To do that for the benefit of people like me with short attention spans and poor eyesight :) please do it this way:

Open **Terminal**
Type [B]testparm -s

I[/B]n your original smb.conf you had a share with the path = /home/roger/Vista_Backups  but your original post said the backup was in /user/local.
 Is one a link to the other?

---

### Post by r.osmanov on 2009-12-27
Do you really need [samba]("https://help.ubuntu.com/community/SettingUpSamba")? Maybe to enable network sharing you just need right click on the folder and enable "Sharing options"? :-)

---

### Post by wabbit46 on 2009-12-30
Dear ELGL and Morbius1

I have Samba Installed but cannot see my Ubuntu computer from Itself. This used to be visable under ubuntu 8.04

I have moved the folder to /home/roger to make sure I have rights  to write to it.

The Vista computer is visable and I can retrieve data from it. I can also print to the printer attached to this PC.

Any advice would be appreciated.

---

### Post by Morbius1 on 2009-12-30
Please post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

One more thing: Is the directory under /home/roger just a regular folder or is it a mount point for another partition. If it's a mount point, please post the output of the following command:

[B]cat /etc/fstab

[/B]If it's amount point to a FAT32 or NTFS partition you may need to alter it's permissions in fstab.

---

### Post by wabbit46 on 2009-12-30
> **Morbius1 said:**
> Please post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

One more thing: Is the directory under /home/roger just a regular folder or is it a mount point for another partition. If it's a mount point, please post the output of the following command:

[B]cat /etc/fstab

[/B]If it's amount point to a FAT32 or NTFS partition you may need to alter it's permissions in fstab.

The output of your commands is shown below  :-

roger@ubuntu:~$ net usershare info 
roger@ubuntu:~$ testparm -s 
Load smb config files from /etc/samba/smb.conf 
Processing section "[homes]" 
Processing section "[Vista Backups]" 
Processing section "[printers]" 
Processing section "[print$]" 
Loaded services file OK. 
WARNING: You have some share names that are longer than 12 characters. 
These may not be accessible to some older clients. 
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.) 
Server role: ROLE_STANDALONE 
[global] 
	server string = %h server (Samba, Ubuntu) 
	security = SHARE 
	map to guest = Bad User 
	obey pam restrictions = Yes 
	pam password change = Yes 
	passwd program = /usr/bin/passwd %u 
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* . 
	unix password sync = Yes 
	syslog = 0 
	log file = /var/log/samba/log.%m 
	max log size = 1000 
	name resolve order = lmhosts host wins bcast 
	dns proxy = No 
	usershare allow guests = Yes 
	usershare owner only = No 
	panic action = /usr/share/samba/panic-action %d 

[homes] 
	comment = Home Directories 

[Vista Backups] 
	comment = Vista Backups 
	path = /home/roger/Vista_Backups 
	create mask = 0777 
	directory mask = 0777 
	guest ok = Yes 

[printers] 
	comment = All Printers 
	path = /var/spool/samba 
	read only = No 
	printable = Yes 
	browseable = No 
	browsable = No 

[print$] 
	comment = Printer Drivers 
	path = /var/lib/samba/printers 
	guest ok = Yes

The folder home/roger is just a regular folder

---

### Post by Morbius1 on 2009-12-30
Well, I would clean up two things:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Find this line:
> security = SHARE And put a # sign in front of it so that it looks like this:
```
#security = SHARE 
```You also need to take care of this warning:
> WARNING: You have some share names that are longer than 12 characters. So I would change:
> [[COLOR=Blue]Vista Backups[/COLOR]] 
    comment = Vista Backups 
    path = /home/roger/Vista_Backups 
    create mask = 0777 
    directory mask = 0777 
    guest ok = Yes To this:
> [[COLOR=Blue]VistaBackups[/COLOR]] 
    comment = Vista Backups 
    path = /home/roger/Vista_Backups 
    create mask = 0777 
    directory mask = 0777 
    guest ok = Yes [COLOR=Blue]*Just get rid of the space between Vista and Backups. Besides linux hates spaces.*[/COLOR]

Save the file, exit gedit, and back in the Terminal type:
[B]sudo service samba restart

[/B]Wait a few minutes and try to access the share again.

---

### Post by wabbit46 on 2009-12-31
> **Morbius1 said:**
> Well, I would clean up two things:

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Find this line:
And put a # sign in front of it so that it looks like this:
```
#security = SHARE 
```You also need to take care of this warning:
So I would change:
To this:
[COLOR=Blue]*Just get rid of the space between Vista and Backups. Besides linux hates spaces.*[/COLOR]

Save the file, exit gedit, and back in the Terminal type:
[B]sudo service samba restart

[/B]Wait a few minutes and try to access the share again.


Thanks Morbius1,

I have made your suggested changes but they have no effect. I do not think the problem is with SAMBA as I can access the Vista shares and print to the printer attached to the Vista computer.

The PC running ubuntu is not visible when I search the network using Places -> Network.

---

### Post by dmizer on 2009-12-31
> **wabbit46 said:**
> Thanks Morbius1,

I have made your suggested changes but they have no effect. I do not think the problem is with SAMBA as I can access the Vista shares and print to the printer attached to the Vista computer.

The PC running ubuntu is not visible when I search the network using Places -> Network.
Do you mean that the Ubuntu computer cannot see itself in Places -> Network?

If so, then why is this a problem? The files can be accessed directly. If I'm missing something, please bring me up to speed.

---

### Post by wabbit46 on 2009-12-31
> **dmizer said:**
> Do you mean that the Ubuntu computer cannot see itself in Places -> Network?

If so, then why is this a problem? The files can be accessed directly. If I'm missing something, please bring me up to speed.

Dear dmizer,

I have tried to make the folder shareable by right clicking it in Nautilus and selecting the share option. The result is still the same the computer is not visible from itself or the computer running Vista.

---

### Post by Morbius1 on 2009-12-31
I know this must be getting old but I have yet another request for information.

Open **Terminal**
Type **net usershare info**
Type [B]ls -dl /home/roger/Vista_Backups

[/B]BTW, It's generally not a good idea to mix sharing methods especially in your case. It sounds like your using "Classic" and "Nautilus" samba sharing on the same folder. I'm not sure who's in charge of sharing at this point.

---

### Post by dmizer on 2009-12-31
> **wabbit46 said:**
> BTW, It's generally not a good idea to mix sharing methods especially in your case. It sounds like your using "Classic" and "Nautilus" samba sharing on the same folder. I'm not sure who's in charge of sharing at this point.

This should not cause a problem. This is probably a problem with master browser elections. Vista doesn't like to cooperate well with SAMBA either as a client or with CIFS as a server.

---

### Post by wabbit46 on 2009-12-31
> **Morbius1 said:**
> I know this must be getting old but I have yet another request for information.

Open **Terminal**
Type **net usershare info**
Type [B]ls -dl /home/roger/Vista_Backups

[/B]BTW, It's generally not a good idea to mix sharing methods especially in your case. It sounds like your using "Classic" and "Nautilus" samba sharing on the same folder. I'm not sure who's in charge of sharing at this point.

The reply to net usershare info was:-

[ok=y vistabackups] 
path=/home/roger/VistaBackups 
comment= 
usershare_acl=Everyone:F, 
guest_ok=y vistabackups] 

The other command gave the following results :-

roger@ubuntu:~$ ls -dl /home/roger/VistaBackups 
drwxrwxrwx 5 roger roger 4096 2009-12-30 22:34 /home/roger/VistaBackups 
roger@ubuntu:~$

---

### Post by wabbit46 on 2009-12-31
> **dmizer said:**
> This should not cause a problem. This is probably a problem with master browser elections. Vista doesn't like to cooperate well with SAMBA either as a client or with CIFS as a server.

I have disabled sharing using Nautilus,

---

### Post by Morbius1 on 2009-12-31
First, using nautilus-share AND classic samba on the same folder can very much be a problem.

Second, It's good that you removed the nautilus share because that's either a big typo or it was really messed up.

Third, and I'm trolling for error messages here:

In Vista, open **Command Prompt** - not the Run command but Command prompt - and type **net view**

You should get a listing of all the machines on your network from Vista's perspective. If it can see the Ubuntu machine and while still in the Command Prompt type: **net view \\Ubuntu_machine_name**

It should give you a listing of all the available shares. If there are any errors anywhere in this process post the full output of those commands.

If Vista can't see the Ubuntu machine and doesn't output any errors I'm wondering if your ubuntu firewall is interfering with things.

---

### Post by wabbit46 on 2010-01-01
> **Morbius1 said:**
> First, using nautilus-share AND classic samba on the same folder can very much be a problem.

Second, It's good that you removed the nautilus share because that's either a big typo or it was really messed up.

Third, and I'm trolling for error messages here:

In Vista, open **Command Prompt** - not the Run command but Command prompt - and type **net view**

You should get a listing of all the machines on your network from Vista's perspective. If it can see the Ubuntu machine and while still in the Command Prompt type: **net view \\Ubuntu_machine_name**


It should give you a listing of all the available shares. If there are any errors anywhere in this process post the full output of those commands.

If Vista can't see the Ubuntu machine and doesn't output any errors I'm wondering if your ubuntu firewall is interfering with things.

Dear Morbius1,

net view only shows the Vista computer not the one running Ubuntu

I have re-run the other commands you asked me to after disabling File saving under Nautilus the output is detailed below :-

roger@ubuntu:~$ net usershare info (no response)
roger@ubuntu:~$ ls -dl /home/roger/VistaBackups 
drwxr-xr-x 5 roger roger 4096 2009-12-30 22:34 /home/roger/VistaBackups 
roger@ubuntu:~$

---

### Post by Morbius1 on 2010-01-01
I think the following will only bring you back to where you began but it is a problem that needs to be fixed. Sharing with samba is a two step process. Samba permissions dictate what you MAY do, linux file permissions dictate what you CAN do.

In your share definition you state that guests MAY access the share:

> [[COLOR=Blue]VistaBackups[/COLOR]] 
    comment = Vista Backups 
    path = /home/roger/Vista_Backups 
    create mask = 0777 
    directory mask = 0777 
    guest ok = Yes                      In your linux file permissions you state that guests ( others ) may not write to that folder.
> roger@ubuntu:~$ ls -dl /home/roger/VistaBackups 
drwxr-xr-x 5 roger roger 4096 2009-12-30 22:34 /home/roger/VistaBackups The easiest method to fix this is to do the following:

Add a line to your share definition in smb.conf that looks like this:

> [[COLOR=Blue]VistaBackups[/COLOR]] 
     comment = Vista Backups 
     path = /home/roger/Vista_Backups
[COLOR=Blue]force user = roger[/COLOR]
     create mask = 0777 
     directory mask = 0777 
     guest ok = Yes                      You won't need the create mask or directory mask anymore but it won't hurt anything if they're still there.

After you make the change restart samba: [B]sudo service samba restart

[/B]Second, and this is a long shot, check the file permissions on the parent directory: /home/roger. It should look like this:[B]

drwxr-xr-x 79 roger[/B][B] roger
[/B]At a minimum there has to be an "r" in all three locations.

---

### Post by wabbit46 on 2010-01-01
> **Morbius1 said:**
> I think the following will only bring you back to where you began but it is a problem that needs to be fixed. Sharing with samba is a two step process. Samba permissions dictate what you MAY do, linux file permissions dictate what you CAN do.

In your share definition you state that guests MAY access the share:

In your linux file permissions you state that guests ( others ) may not write to that folder.
The easiest method to fix this is to do the following:

Add a line to your share definition in smb.conf that looks like this:

You won't need the create mask or directory mask anymore but it won't hurt anything if they're still there.

After you make the change restart samba: [B]sudo service samba restart

[/B]Second, and this is a long shot, check the file permissions on the parent directory: /home/roger. It should look like this:[B]

drwxr-xr-x 79 roger[/B][B] roger
[/B]At a minimum there has to be an "r" in all three locations.

Dear Morbius1,

I have tried the change you suggested but if had no effect.

The permissions to /home/roger are drwxr-xr-x 32

---

### Post by Morbius1 on 2010-01-01
Let's recap all that you've done so far:

(1) You've made a number of changes to smb.conf and except for the share definition itself you've basically got it to its "out of the box" state.

(2) You've disabled the Ubuntu firewall

(3) You've disabled the Windows firewall

(4) You've disabled the Windows Anti-Virus

(5) It appears as though the permissions - both samba and linux - are correct.

So what you have now is that Ubuntu can see and access the Windows share but Windows can't see the Ubuntu share.

Can you even ping the Ubuntu machine from Windows by ip address. **ping 192.168.0.100** for example .from command prompt?

If you can, try to "map a network drive" from vista using the ip address:** \\192.168.0.100\vistabackups**
 Changing the ip address to Ubuntu's ip address. You may have to play with the capitalization of the "vistabackups" part.

---

### Post by wabbit46 on 2010-01-02
> **Morbius1 said:**
> Let's recap all that you've done so far:

(1) You've made a number of changes to smb.conf and except for the share definition itself you've basically got it to its "out of the box" state.

(2) You've disabled the Ubuntu firewall

(3) You've disabled the Windows firewall

(4) You've disabled the Windows Anti-Virus

(5) It appears as though the permissions - both samba and linux - are correct.

So what you have now is that Ubuntu can see and access the Windows share but Windows can't see the Ubuntu share.

Can you even ping the Ubuntu machine from Windows by ip address. **ping 192.168.0.100** for example .from command prompt?

If you can, try to "map a network drive" from vista using the ip address:** \\192.168.0.100\vistabackups**
 Changing the ip address to Ubuntu's ip address. You may have to play with the capitalization of the "vistabackups" part.

Dear Morbius1,

Thank you for your reply.

The latest state of the situation is not quite as you described. Here is a brief summary :-

The smb.conf file is essentially "out of the box" apart from the share definition.

I have no Ubuntu firewall apart from the permissions in the smb.conf file.

The Windows firewall and anti-virus software are still active.

The Ubuntu PC can access Windows shares, the Windows printer and the Internet via the Windows PC.

I can ping the PC running Ubuntu with no errors. However when I try to map to the share it requires a password. The Vista PC has no password and the Ubuntu PC password fails to authenticate.

Finally the Ubuntu PC can not see itself unter Places -> Network. Until this is resolved I cannot see how how another computer can access it.

---

### Post by Morbius1 on 2010-01-02
> However when I try to map to the share it requires a password. The Vista PC has no password and the Ubuntu PC password fails to authenticate.I'm not used to running any operating system without a password to login so I'm in uncharted territory here but there is a peculiarity about how windows broadcasts it's request for access to shares.

Do you, by any chance, have the same username on each machine - Vista and Ubuntu

Also when Vista prompts for a password , if you give it **guest** and no password ( just leave it blank ) does it give you access.

---

### Post by dmizer on 2010-01-02
> **Morbius1 said:**
> Also when Vista prompts for a password , if you give it **guest** and no password ( just leave it blank ) does it give you access.

I have high hopes for this potential fix. I've had it work for me in the past.

---

### Post by wabbit46 on 2010-01-03
> **Morbius1 said:**
> I'm not used to running any operating system without a password to login so I'm in uncharted territory here but there is a peculiarity about how windows broadcasts it's request for access to shares.

Do you, by any chance, have the same username on each machine - Vista and Ubuntu

Also when Vista prompts for a password , if you give it **guest** and no password ( just leave it blank ) does it give you access.

Dear Morbius1,

I really appreciate your attempts to help me resolve this problem.

Yes the username on both computers is the same.

Trying to map as guest without a password does not fail to authenticate but just hangs trying to connect.

---

### Post by Morbius1 on 2010-01-03
I'll be honest, I'm stalling for time here until I think through this thing.

Try this:

Open **Terminal**
Type **shares-admin**

When it opens select > **Unlock** > **Users**

Search through the list of users and see if you can find your Ubuntu username. If it's checked - uncheck it. Then select **Close**

I don't remember if shares-admin restarts the samba service so back in the terminal type:

[B]sudo service samba restart

[/B]Wait a few minutes,  then see if you can connect.

---

### Post by dmizer on 2010-01-03
Frankly, I think the Ubuntu side of things is working perfectly.

Tell me more about the Vista side of things. Are you sharing a separate hard drive or partition? Are you trying to share an entire hard drive? Have you tried configuring other shares with identical results? Do the Vista shares work with any other machines?

---

### Post by wabbit46 on 2010-01-04
> **Morbius1 said:**
> I'll be honest, I'm stalling for time here until I think through this thing.

Try this:

Open **Terminal**
Type **shares-admin**

When it opens select > **Unlock** > **Users**

Search through the list of users and see if you can find your Ubuntu username. If it's checked - uncheck it. Then select **Close**

I don't remember if shares-admin restarts the samba service so back in the terminal type:

[B]sudo service samba restart

[/B]Wait a few minutes,  then see if you can connect.

Dear Morbius1,

I have tried the commands you suggested.

When I type shares-admin, I get a dialog box with 3 tabs at the top being Shared Folders - which contains the Samba share. General properties and Users.

When I click on the Samba share I have a properties box with all entries greyed out. Interestingly the share name is still Vista Backup (with the space) and minus the "s" although I have deleted the space in the smb.conf file.

Both General Properties and Users only contain greyed out entries. There is no provision to unlock a user.

---

### Post by Morbius1 on 2010-01-04
I guess the wording on the dialog box has changed to make it as confusing as possible. "Unlock" has been replaced with "Click to make changes"

You can do this from a terminal:

Open **Terminal**
Type **sudo smbpasswd -x roger**

This will remove your samba account for roger if you had one.
If you need to add it back just issue a **sudo smbpasswd -a roger**

> Interestingly the share name is still Vista Backup (with the space) and minus the "s" although I have deleted the space in the smb.conf file.You might want to do a quick check on all your configuration files to make sure that share's name is 12 characters or less in **/etc/samba/smb.conf** and in **/var/lib/samba/usershares.**

---

### Post by wabbit46 on 2010-01-04
> **Morbius1 said:**
> I guess the wording on the dialog box has changed to make it as confusing as possible. "Unlock" has been replaced with "Click to make changes"

You can do this from a terminal:

Open **Terminal**
Type **sudo smbpasswd -x roger**

This will remove your samba account for roger if you had one.
If you need to add it back just issue a **sudo smbpasswd -a roger**

You might want to do a quick check on all your configuration files to make sure that share's name is 12 characters or less in **/etc/samba/smb.conf** and in **/var/lib/samba/usershares.**

The "Click to Make Changes" option is not active. I have deleted the account for the user roger from samba as per your instructions. 

The shares names did contain a space. I had deleted it from the directory but not the share name. It has not made any difference.

There currently is no entry in /var/lib/samba/usershares.

I am beginning to think that I should revert back to version 8.04 as this sharing worked under that version.

---

### Post by wabbit46 on 2010-01-08
> **wabbit46 said:**
> The "Click to Make Changes" option is not active. I have deleted the account for the user roger from samba as per your instructions. 

The shares names did contain a space. I had deleted it from the directory but not the share name. It has not made any difference.

There currently is no entry in /var/lib/samba/usershares.

I am beginning to think that I should revert back to version 8.04 as this sharing worked under that version.

I have partially solved the problem using a fresh install of Ubuntu 9.10 and downloading all the latest updates before modifying the SMB.CONF file.

I can see the Ubuntu share from both Vista and Ubuntu but cannot write to the share from the Vista computer. Also SAMBA does not automatically start on reboot but must be manually started

---

### Post by Morbius1 on 2010-01-08
What?

You can read and write to the Ubuntu share from another Ubuntu machine on the network but you can only read from a Vista machine on the network?

---

### Post by wabbit46 on 2010-01-08
> **Morbius1 said:**
> What?

You can read and write to the Ubuntu share from another Ubuntu machine on the network but you can only read from a Vista machine on the network?

I have only two computers on my mini-network. One runs Vista and the other one runs Ubuntu.

I can see the Ubuntu shares from the Vista machine but cannot write to it.

---

### Post by Morbius1 on 2010-01-08
Since you reinstalled can you post the output of these commands again please:
[B]
net usershare info[/B]
**testparm -s**

---

### Post by wabbit46 on 2010-01-14
> **Morbius1 said:**
> Since you reinstalled can you post the output of these commands again please:
[B]
net usershare info[/B]
**testparm -s**

The output of these commands is given below :-

roger@Ubuntu:/etc/samba$ net usershare info 
roger@Ubuntu:/etc/samba$ testparm -s 
Load smb config files from /etc/samba/smb.conf 
Processing section "[Vista_Backup]" 
Processing section "[printers]" 
Processing section "[print$]" 
Loaded services file OK. 
Server role: ROLE_STANDALONE 
[global] 
	server string = %h server (Samba, Ubuntu) 
	map to guest = Bad User 
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* . 
	syslog = 0 
	log file = /var/log/samba/log.%m 
	max log size = 1000 
	dns proxy = No 
	usershare allow guests = Yes 
	usershare owner only = No 
	panic action = /usr/share/samba/panic-action %d 

[Vista_Backup] 
	comment = Vista Backups 
	path = /home/roger/VistaBackups 
	read only = No 
	create mask = 0777 
	directory mask = 0777 
	guest ok = Yes 

[printers] 
	comment = All Printers 
	path = /var/spool/samba 
	create mask = 0700 
	printable = Yes 
	browseable = No 
	browsable = No 

[print$] 
	comment = Printer Drivers 
	path = /var/lib/samba/printers 
-----------------------------------------------------------------
By the way I can now see the Ubuntu share from the Vista PC but not write to it. Sorry for the delay in responding.

---

### Post by Morbius1 on 2010-01-14
Here's how I see the situation.

You created a share that allows write access and guest access and looks like this:
> [Vista_Backup] 
    comment = Vista Backups 
    path = /home/roger/VistaBackups 
    read only = No 
    create mask = 0777 
    directory mask = 0777 
    guest ok = Yes But the last time you posted the permissions on path = /home/roger/VistaBackups it looked like this:
> roger@ubuntu:~$ ls -dl /home/roger/VistaBackups 
drwxr-xr-x 5 roger roger 4096 2009-12-30 22:34The samba gate keeper is allowing the guest to write to that folder but the linux file permissions are not. You're going to have to change the permissions on /home/roger/VistaBackups from 755 to 777. Or you can add **force user = roger** into the share definition since at this point roger is the only one that can write to that folder.

---

### Post by wabbit46 on 2010-01-18
> **Morbius1 said:**
> Here's how I see the situation.

You created a share that allows write access and guest access and looks like this:
But the last time you posted the permissions on path = /home/roger/VistaBackups it looked like this:
The samba gate keeper is allowing the guest to write to that folder but the linux file permissions are not. You're going to have to change the permissions on /home/roger/VistaBackups from 755 to 777. Or you can add **force user = roger** into the share definition since at this point roger is the only one that can write to that folder.

This has not only fixed the problem but enabled me to place the directory where I originally wanted to put it. 

I greatly appreciate all of your assistance.

---

