---
title: "Samba - Absolutely cannot share new folders with Windows 7 or XBMC"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by mdsc on 2010-09-13
I have had folder sharing under Samba working for several past versions of Ubuntu.  I recently upgraded to 10.04 and my old shares are still working, but any new folders I attempt to share I cannot get to work, despite attempting multiple workarounds.

The Windows 7 error I get is:

"Windows can't find "\\MYSERVER\shared_folder".  The name might be misspelled."

The XBMC error I get is:

"Error -1073741772: share not available."

Any help is much appreciated.

---

### Post by mdsc on 2010-09-13
Sorry, some further information may be useful.  I created the new share with Nautilus, using the right click, "Sharing Options" menu.  I then checked my old working shares and they all have the same options ticked on this menu.

I then went to /var/lib/samba/usershares, and opened up the info on each share.  Both my old working shares and new non-working shares have the following:
```

#VERSION 2
path=/path/to/share
comment=
usershare_acl=S-1-1-0:R
guest_ok=y

```
The output of the command
```
net usershare info
``` is
 ```

info_fn: file /var/lib/samba/usershares/video_tv is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[movies]
path=/path/to/movies
comment=
usershare_acl=Everyone:R,
guest_ok=y

[images]
path=/path/to/images
comment=
usershare_acl=Everyone:R,
guest_ok=y

[tv]
path=/path/to/tv
comment=
usershare_acl=Everyone:R,
guest_ok=y

[downloads]
path=/path/to/downloads/complete
comment=
usershare_acl=Everyone:R,
guest_ok=y

info_fn: file /var/lib/samba/usershares/video_movies is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[audio]
path=/path/to/audio
comment=
usershare_acl=Everyone:R,
guest_ok=y

```

My "tv" and "movies" shares are the ones not working.  

Before I had 2 HDs die, I had file system folders named "video" on each HD that mapped to the share names "video_tv" and "video_movies," so these shares aren't supposed to be working.  

Now with the new HDs the file system folders are now simply "tv" and "movies."  Of course the new HDs have new volume labels and mount points, so I'm not sure how it all could get confused.

The "audio" and other shares have been working all along.

---

### Post by mdsc on 2010-09-14
More info on the problem.  It is actually also present on my Ubuntu server itself.  I didn't realize that Firefox could open smb links, but apparently it can.  On my Ubuntu machine, Firefox can open 

smb://SERVER/audio/

but cannot open

smb://SERVER/tv

Meanwhile, Nautilus browses both of these locations via the "Places > Network" menu equally well.

Hmmm....

---

### Post by elico on 2010-09-14
just to make sure i understood:
the other shares are working? you can get hold of the from the windows 7 machine?

what is your smb.conf file content?
and also on the top of the command output you are getting errors.

---

### Post by mdsc on 2010-09-14
Thanks for your reply!

Yes, I can access, the "audio", "images", and "downloads" shares from both my Windows 7 laptop and my Xbox running XBMC.  These shares were created before the 10.04 upgrade -- probably back in the 8.04 or 8.10 days, though I'm not sure.

I cannot access the new shares "tv" and "movies".

Yes, I do have an error from the "net usershare info" command, because the hard drives that my "video_tv" and "video_movies" shares were on died a sudden death shortly after the 10.04 upgrade.  I installed two new hard drives where the new "tv" and "movies" shares are located.  My old working shares are formatted in ext3, and the new not working ones in ext4, but I didn't think that would make any difference.

Here is my smb.conf (I assume you need the one from /etc/samba/)

As far as I know, I have not made any changes to the default.

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
	workgroup = workgroup

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
#   	security = user

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

;	wins support = no
	security = user
	username map = /etc/samba/smbusers
;	guest ok = no
;	guest account = nobody
;	guest ok = no
;	guest account = nobody
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

```

---

### Post by endotherm on 2010-09-14
try running ```
sudo testparm
``` to see if there are any errors processing your config. 
have you cleared up the error above about your tv and movie shares being in /var/.../?
/var isn't a normal location, so you probably shouldn't host files from there.

---

### Post by Morbius1 on 2010-09-14
Your smb.conf is factory fresh without any modifications and your Nautilus-shares look fine - it's kind of hard to mess up a nautilus-share.

One thing that might explain this phenomenon is the permissions of the path leading up to path=/path/to/tv

As an example, let's say the real mountpioint of the partition that holds the tv share is Disk2. So the real path to the shared folder is:

> /Disk2/tvNautilus-share will automatically modify the permissions of the shared folder but it does not modify it's parent. If /Disk2 has permissions of say 700 then to the remote guest user there is no tv share because he can't open /Disk2 to see what's inside. See what the permissions are on the parent folder:

```
ls -dl /path/to/parent/folder/of/tv
```endotherm, He's using usershare ( Nautilus-share ) to create his samba shares. The share definitions are in /var/lib/samba/usershares not in smb.conf where a classic share definition would be. The errors won't harm anything since those share definitions are pointing to a path that no longer exists.

---

### Post by endotherm on 2010-09-14
> **Morbius1 said:**
> endotherm, He's using usershare ( Nautilus-share ) to create his samba shares. The share definitions are in /var/lib/samba/usershares not in smb.conf where a classic share definition would be. The errors won't harm anything since those share definitions are pointing to a path that no longer exists.

I was thinking the same thing, until I noticed some global section edits at the very bottom of the smb.conf. thats why I requested teh testparm. regardless you are more knowledgeable than I with samba, so I will bow out. op is in good hands.

---

### Post by Morbius1 on 2010-09-14
Don't bow out too early my last post was a guess :p

---

### Post by elico on 2010-09-14
well it is looks like fresh.
are you sure it's the /etc/samba/smb.conf 
??

---

### Post by mdsc on 2010-09-14
Morbius1 - 

If it was a guess it was a really good one.  The parent folder (which is the entire disk volume) had permissions of "drwx------".  I changed this to allow read access for my group and "others" via the nautilus right click > Properties > Permissions menu.  Now it appears to be working well!  Still need to apply to my other share "movies" and test on XBMC.  Will update as I find out more, but may not have much more time to tinker tonight.

Just out of curiosity, I thought "nautilus-shares" automatically updated file/folder permissions so that this wouldn't be an issue?  Seems this might be a really common way Ubuntu users could get frustrated!

endotherm -

Thanks also for taking a look.  I ran the testparm command as you suggested, but since it now seems to be working, I'm not sure it will be any use to us.

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

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


```

---

### Post by Morbius1 on 2010-09-15
> Just out of curiosity, I thought "nautilus-shares" automatically updated  file/folder permissions so that this wouldn't be an issue?  Seems this  might be a really common way Ubuntu users could get frustrated!It does change the permissions on the target directory itself ( tv ) but not on the entire path leading up to the target. Normally when a linux partition is mounted it will by default have permissions set to 755 so this isn't an issue.

[COLOR=Blue]**EDIT**[/COLOR]: BTW if you want to get rid of those errors from "net usershare info" you have a problem in that you can't 
"unshare" them from nautilus since the target no longer exists. You can do it from the terminal:
```
net usershare delete video_tv
net usershare delete video_movies
```Or you can just go to /var/lib/samba/usershares in nautilus and delete them.

---

### Post by endotherm on 2010-09-15
> **elico said:**
> well it is looks like fresh.
are you sure it's the /etc/samba/smb.conf 
??
glad you got it worked out!

---

### Post by mdsc on 2010-09-15
Thanks again to everybody for your help.  Got all my shares working in Windows 7 and XBMC!

> Normally when a linux partition is mounted it will by default have permissions set to 755 so this isn't an issue.

Again, not essential to my issue, but perhaps to prevent it happening again, wonder why my drives were mounted with 700 permissions instead?

I formatted them with System > Admin > Disk Utility, then edited my etc/fstab so they would auto mount.  The last 3 columns on their fstab entries are "defaults  0  2".

---

### Post by endotherm on 2010-09-15
> **mdsc said:**
> Thanks again to everybody for your help.  Got all my shares working in Windows 7 and XBMC!



Again, not essential to my issue, but perhaps to prevent it happening again, wonder why my drives were mounted with 700 permissions instead?

I formatted them with System > Admin > Disk Utility, then edited my etc/fstab so they would auto mount.  The last 3 columns on their fstab entries are "defaults  0  2".

not sure if this is what you are asking, but samba implements it;s own directory masks with the "Create" and "Directory" masks, so yours may have gotten tweaked. 
from smb.conf:
```
create mask = 0644
directory mask = 0755 

```yours may have gotten changed. 
if you mean the drive itself, check your umask value. the default is 022.
you can confirm by just typing 'umask' at a terminal. 777 = 022 + 755.

just fyi, the trailing two numbers in your fstab line set whether and in what order, a disk will be scanned for errors. if you change the first number to 1, save and reboot, you will notice a disk scan on that drive during next boot. the second value dictates the order in which the disks are checked, from 0-x. your drive will be checked 3rd based on the '2' you have set.

---

### Post by Morbius1 on 2010-09-15
> **mdsc said:**
> Again, not essential to my issue, but perhaps to prevent it happening again, wonder why my drives were mounted with 700 permissions instead?

I formatted them with System > Admin > Disk Utility, then edited my etc/fstab so they would auto mount.  The last 3 columns on their fstab entries are "defaults  0  2".
And if I remember right your partition is formatted in ext4. That's very strange. It should have mounted with owner = root and permissions set to 0755. I don't even have a guess for how that changed to 0700.

---

### Post by mdsc on 2010-09-15
Yeah, my umask is 022.

Oh well, sometimes you can't figure everything out.  As long as it works, and it does now.  And I will know what to look for next time.

Thanks!

---

