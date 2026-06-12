---
title: "Share Folder outside of Home Directory"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by QKC on 2011-07-09
Dear members,
I have got 11.04 install on my dell system.The system has got 2 harddisk,all my data is store in the 2nd harddisk.How do I share the folder in the 2nd harddisk.Samba is already install in the system.

Appreciate soonest reply
Thanks

---

### Post by capscrew on 2011-07-09
> **QKC said:**
> Dear members,
I have got 11.04 install on my dell system.The system has got 2 harddisk,all my data is store in the 2nd harddisk.How do I share the folder in the 2nd harddisk.Samba is already install in the system.

Appreciate soonest reply
Thanks

You share that folder just like any other folder.  

Once the disk (really the partition) is mounted it acts just like the other partitions.  Are you using GUI shares or configuring the /etc/samba.smb.conf file to create the share?

---

### Post by QKC on 2011-07-10
Hi Capscrew,
I share the folders using the GUI share but cannot.How do I know if the HDD is mounted?

---

### Post by lmarmisa on 2011-07-10
Your second HDD will be probably not mounted automatically by Ubuntu. Please, open a terminal, type these commands and post the results:

```

sudo parted -l
sudo blkid
mount
cat /etc/fstab

```

---

### Post by QKC on 2011-07-11
Hi Imarmisa,
Please see below information as per your request

dell@dell-Vostro-200:~$ sudo parted -l
[sudo] password for dell: 
Model: ATA WDC WD3200AAKS-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  314GB  314GB   primary   ext4            boot
 2      314GB   320GB  6439MB  extended
 5      314GB   320GB  6439MB  logical   linux-swap(v1)


Model: ATA WDC WD5000AADS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ext4


dell@dell-Vostro-200:~$ 


dell@dell-Vostro-200:~$ sudo blkid
/dev/sda1: UUID="aef3a1b7-3b44-4c2a-a39f-68c2edf7aac8" TYPE="ext4" 
/dev/sda5: UUID="27bb60cc-31cd-44d0-86b5-e658b2ed2714" TYPE="swap" 
/dev/sdb1: LABEL="New Volume" UUID="84a6e4c2-2ad4-4b96-b924-8575279487ae" TYPE="ext4" 
dell@dell-Vostro-200:~$ 

dell@dell-Vostro-200:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dell/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dell)
dell@dell-Vostro-200:~$ 

dell@dell-Vostro-200:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=aef3a1b7-3b44-4c2a-a39f-68c2edf7aac8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=27bb60cc-31cd-44d0-86b5-e658b2ed2714 none            swap    sw              0       0
dell@dell-Vostro-200:~$ 


Appreciate your reply
Thanks

---

### Post by lmarmisa on 2011-07-11
Hi QKC,

your second hdd is not mounted automatically by Ubuntu at startup.

I recommend to follow this procedure. Open a terminal and type this command:

```

sudo mkdir /media/MyData

```Then edit the file **/etc/fstab** and add these two lines at the bottom of the file:

```

sudo gedit /etc/fstab

``````

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=aef3a1b7-3b44-4c2a-a39f-68c2edf7aac8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=27bb60cc-31cd-44d0-86b5-e658b2ed2714 none            swap    sw              0       0
[COLOR=Blue]# MyData
UUID=84a6e4c2-2ad4-4b96-b924-8575279487ae /media/MyData ext4 defaults,noatime 0 2[/COLOR]

```Save & Exit.

Reboot your system. The "New Volume" partition will be mounted on **/media/MyData**.

You will be able to see your data files there:

```

ls -l /media/MyData

```Tell me if you get some trouble accessing to those files or folders due to permissions or owner:group.

Best regards,

Luis

---

### Post by QKC on 2011-07-12
Hi lmarmisa,
I have done as your advise.When accessing from my window 7 laptop,an error appear.Please see attach file.

Appreciate your help
Thanks

---

### Post by lmarmisa on 2011-07-12
According to your capture, it seems that there is a problem related to user/password logon of Samba.

If you are typing correctly the username and password of your user account in your Ubuntu system, you have to verify that you have followed the correct steps for sharing a folder.

First of all, I recommend to type the command **ls -l /media/MyData**:
 
```

luis@UB1010ENG:~$ ls -l /media/MyData
total 20
drwx------ 2 root root 16384 2011-07-13 00:56 lost+found
drwxrwxrwx 2 luis luis  4096 2011-07-13 01:00 MyPhotos
luis@UB1010ENG:~$ 

```

This is an example. You can see here the folder MyPhotos that I am going to share. **Important:** the user and group of the folder MyPhotos is my user account and group: **luis**. Therefore I am the owner of the contents of that folder and I have privileges for read/write the files and folders included in MyPhotos. Try to check the owner and group of your shared folder.

The next step is to share the folder. Open Nautilus, go to the folder **/media/MyData**, select the folder MyPhotos, then  right button of mouse and **Sharing Options** (Fig01).

Tick **Share this folder**, **Allow others to create files in this folders** and finally select **CreateShare** (Fig02).

Finally, I was able to connect to the shared folder from a Windows system without any problem.

Best regards,

Luis

---

### Post by QKC on 2011-07-15
Hi lmarmisa,
I did as you advise but the error still appear.Please see attach files.The folder that I am sharing is Music.

Appreciate your reply

---

### Post by lmarmisa on 2011-07-15
> **QKC said:**
> Hi lmarmisa,
I did as you advise but the error still appear.Please see attach files.The folder that I am sharing is Music.

Appreciate your reply

It seems that a different icon is shown in the icon of the folder Music. This is due because you have shared that folder.

Try to check if you are able to connect to the shared folder Music from Ubuntu. Please, open Nautilus, select Network, your computer and finally the folder Music. Ubuntu will ask for your username and password. I attach a capture (your domain will be workgroup).

Tell me if you are able to access successfully to the shared folder from Ubuntu. If so, the problem is limited to Windows 7 (maybe you would need to renew the credentials).

Best regards,

Luis

---

### Post by QKC on 2011-07-16
Hi Imarmisa,
I cannot access the folder after key in the password.When I key in the password,it just jump up to the "Username", unable to key in the password

Thanks

---

### Post by lmarmisa on 2011-07-16
Create a folder named test on the Desktop and try to share it. Tell me if you get the same problems with this other folder.

---

### Post by QKC on 2011-07-16
Hi
Same problem happen on the Test folder

---

### Post by lmarmisa on 2011-07-16
I suppose that you are typing username = dell and its associated password. Are you sure that the password is good?. Do you use the password for login in your account?.

---

### Post by lmarmisa on 2011-07-16
The command **smbclient** is useful for solving problems related to samba. Type this command:

```

smbclient '//dell-Vostro-200/test' -U dell

```If the samba server is running, the command will ask for a password. If you get an error, please post the result.

I copy here a similar example:

```

luis@UB1104ENG:~$ smbclient '//UB1104ENG/test' -U luis
Enter luis's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.8]
smb: \> quit
luis@UB1104ENG:~$

```

---

### Post by QKC on 2011-07-16
> **lmarmisa said:**
> I suppose that you are typing username = dell and its associated password. Are you sure that the password is good?. Do you use the password for login in your account?.
Hi,
It is the same password when I need to have root access.My system is config to log in automatically when I am doing first installation of 11.04.

---

### Post by QKC on 2011-07-16
> **lmarmisa said:**
> The command **smbclient** is useful for solving problems related to samba. Type this command:

```

smbclient '//dell-Vostro-200/test' -U dell

```If the samba server is running, the command will ask for a password. If you get an error, please post the result.

I copy here a similar example:

```

luis@UB1104ENG:~$ smbclient '//UB1104ENG/test' -U luis
Enter luis's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.8]
smb: \> quit
luis@UB1104ENG:~$

```
Hi,
I have the below error.

dell@dell-Vostro-200:~$ smbclient '//dell-Vostro-200/test' -U dell
Enter dell's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
dell@dell-Vostro-200:~$ 

Thanks

---

### Post by QKC on 2011-07-16
> **kena12 said:**
> Once the disk (really the partition) is mounted it acts just like the  other partitions.  Are you using GUI shares or configuring the  /etc/samba.smb.conf file to create the share? Try to check if you are able to connect to the shared folder Music from  Ubuntu. Please, open Nautilus, select Network, your computer and finally  the folder Music. Ubuntu will ask for your username and password. I  attach a capture (your domain will be workgroup).
Hi,
Already try that out with error.

Thanks

---

### Post by lmarmisa on 2011-07-16
> **QKC said:**
> Hi,
I have the below error.

dell@dell-Vostro-200:~$ smbclient '//dell-Vostro-200/test' -U dell
Enter dell's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
dell@dell-Vostro-200:~$ 

Thanks

Ok. This information is interesting.

How did you install Samba?. Did you install it from the Ubuntu repositories?. Did you install the package **system-config-samba**?. Have you modified the file **/etc/samba/smb.conf?**.

---

### Post by QKC on 2011-07-16
Hi 
I install Samba through Ubuntu Software Center that is in 11.04.Pls see attach file.In the config,I change only the below,while the rest remain as default.

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = JINQUAN <------ This is the only one I change.

Below is the full config for your checking.

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
	workgroup = JINQUAN

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
;   name resolve order = lmhosts host wins bcast

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
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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
;	printing = cups
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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	username map = /etc/samba/smbusers
	security = user
;	guest ok = no
;	guest account = nobody

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
;   read only = yes

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

[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
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

---

### Post by lmarmisa on 2011-07-16
I think that your problem is due to the package **system-config-samba **that does not match very well with the shared folder management of Nautilus.

I recommend to uninstall completely the packages **samba** and **system-config-samba** and then try to share the folder **Music** again. In this case, Ubuntu will install automatically the samba packages needed for the management of the shared folders and your problem will be fixed.

Best regards,

Luis

---

### Post by QKC on 2011-07-16
Hi Imarmisa,
Okay.Have done it.Copy,cut and paste function is all working well.Thank you very much.

---

