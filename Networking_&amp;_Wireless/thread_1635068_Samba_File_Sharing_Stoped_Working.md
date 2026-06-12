---
title: "Samba File Sharing Stoped Working"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by BlueVark on 2010-12-01
Hi All,

I set up a Ubuntu Server for my home network to share among Win XP and Ubuntu machines.  Initially everything worked fine with all Win XP machines being able to share files on the server; however, after I installed and setup SSH between my Ubuntu machines and my Ubuntu Server I now _cannot_ share and/or even see my Server directory from Win XP or Ubuntu machines through the Samba.  I have tried for 2 days to figure out the problem without success.  

Now I need your help.  Did I break something while setting up the SSH?  How can I fix Samba?  

Here's some things I have setup or tried so far:
1.  Samba users are setup and were working previously.
2.  Samba share drives were setup and working previously.
3.  I can see the Server using SSH or SFTP from my Ubuntu machines.
4.  I have gone over the Samba config file numerous times.  
5.  I am administering Samba on the server via the terminal and Webmin 

Thanks so much for your help...BlueVark

---

### Post by lrgmmc on 2010-12-01
could you post your samba config file?

---

### Post by BlueVark on 2010-12-01
Here's the config file.

Thanks for looking...BlueVark


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
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	sync always = yes
	interfaces = eth0
	map to guest = bad user
	encrypt passwords = yes
	passdb backend = tdbsam
	dns proxy = no
	browseable = true
	server string = %h server (Samba, Ubuntu)
	wide links = no
	delete readonly = yes
	writeable = yes
	unix password sync = yes
	workgroup = WORKGROUP
	os level = 20
	socket address = 192.168.0.xxx
	security = user
	syslog = 0
	create mode = 700
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes
	directory mode = 700

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of

# server string is the equivalent of the NT Description field

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.

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

# Cap the size of the individual log files (in KiB).

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.

# Do something sensible when Samba crashes: mail the admin a backtrace


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  


# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections

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

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

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

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
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



[ext1]
	create mode = 755
	public = yes
	path = /mymounts/ext1
	directory mode = 755
        

[ihd2]
	public = yes
	path = /mymounts/int2



[zip1]
	public = yes
	path = /mymounts/zip1

---

### Post by lrgmmc on 2010-12-01
this is just to test to make sure everything is ok, and i am unfortanatly on a work windoze machine so i dont know the exact paths so bear with me. make a backup of the samba config file to smb.conf.bk 
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bk
```
then open smb.conf.
```
sudo nano /etc/samba/smb.conf
``` 
change 
```
####### Authentication #######
 
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
# security = user

```
to 
```
####### Authentication #######
 
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
  security = share
  guest account = nobody
 

```
that way you dont need an account to login.
then change 
```
[ext1]
create mode = 755
public = yes
path = /mymounts/ext1
directory mode = 755
 
 
[ihd2]
public = yes
path = /mymounts/int2
 
 
 
[zip1]
public = yes
path = /mymounts/zip1 
```
 
to
```
[ext1]
comment = Guest access ext1
path = /mymounts/ext1
browseable = yes
guest ok = yes
 
[ihd2]
comment = Guest access ihd2
path = /mymounts/int2
browseable = yes
guest ok = yes
 
 
 
 
[zip1]
comment = Guest access zip1
path = /mymounts/zip1
browseable = yes
guest ok = yes
 
 
```
save the file then in terminal run
```
sudo /etc/init.d/samba reload
```
then if no errors test

---

### Post by BlueVark on 2010-12-01
Sorry, I tried those changes and still no luck.  I will make a new config file without all the comments and post again.  

Thanks for helping...BlueVark

---

### Post by lrgmmc on 2010-12-01
i'll be home in like 1 hour and post a sample i know works.

---

### Post by BlueVark on 2010-12-01
OK...thanks again.  I ran a "testparm" with the config file and it all checked.  Here's the new config file in an easier to read format.  Sorry, about the other long format...I changed to back to an original file to see if it would work and it didn't.  Anyway, here's the shortened current config file.  

[global]
	log file = /var/log/samba/log.%m
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	sync always = yes
	interfaces = eth0
	map to guest = bad user
	encrypt passwords = yes
	passdb backend = tdbsam
	dns proxy = no
	browseable = true
	server string = %h server (Samba, Ubuntu)
	wide links = no
	delete readonly = yes
	writeable = yes
	unix password sync = yes
	workgroup = WORKGROUP
	os level = 20
	socket address = 192.168.0.xxxx
	security = user
	syslog = 0
	create mode = 700
	usershare allow guests = yes
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000
	pam password change = yes
	directory mode = 700

   security = share
   guest account = nobody

   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[ext1]
	comment = Guest access ext1
	path = /mymounts/ext1
	browseable = yes
	guest ok = yes
  
[ihd2]
	comment = Guest access ihd2
	path = /mymounts/int2
	browseable = yes
	guest ok = yes

[zip1]
	comment = Guest access zip1
        path = /mymounts/zip1
        browseable = yes
        guest ok = yes

---

### Post by Morbius1 on 2010-12-01
Can the client see the server just not the shares?

Or does the client see neither?

You might want to check to see is all the samba services are running ( I'm assuming you're using 10.04 or later ):
```
sudo service smbd status
sudo service nmbd status
```And did you intend to add this option:
>      socket address = 192.168.0.xxxx

---

### Post by BlueVark on 2010-12-01
All services are running.  

The clients (Ubuntu and Win XP) can't see the server or the shares using Samba.  They could until yesterday when I set up the SSH Server. 

The client (Ubuntu) can see the server and shares using SSH.

The socket address is correct.

The non-server Ubuntu machines can share their folders with my Win XP machines using Samba. I can not share or see the Ubuntu Server machine or folders using Samba.

---

### Post by SteIMG on 2010-12-01
I have *just* seen the same thing.  I just installed the latest set of updates (4 updates - just a few kernel headers and bind type things I think -- can't remember).

Suddenly it has stopped appearing in the 'Network' on my Win 7 box.

You can browse to it by IP address -- and all works -- however this still need fixing. 

The smb.conf hasn't been touched.

Update:
I've just run Wireshark - and the Ubuntu box can see the 'Name Query' packets from the Win7 box -- but just is not replying to them.

---

### Post by SteIMG on 2010-12-01
Wireshark running on the Ubuntu box can see the 'Name Query' packets from the Win7 box -- but just does not reply to them.

---

### Post by BlueVark on 2010-12-01
My issue doesn't seem to be update related...although I guess it could be as there was a fairly large kernal update to Ubuntu Server on Tuesday (I believe).  I am running Ubuntu Server 10.04 and I am pretty sure that it worked after the update.  I think it started having the problem after I set up the SSH server.  Could this be the source of the problem?  

I am running Samba on a laptop with regular Ubuntu 10.04 and it works fine.  All the Win XP machines can share with this laptop, but not the server. 

I'm just plain stumped and have probably changed so many things on the server that it may be just as fast to reformat and start over from scratch.  

Thanks again to all who have tried to help...BlueVark

---

### Post by BlueVark on 2010-12-02
Morning bump...does anyone have any other ideas on how to fix this problem before I reformat my hard drive and start over? 

Thanks so much for the help...BlueVark

---

### Post by lrgmmc on 2010-12-02
hey what is the print out of ```
testparm -s
```

---

### Post by BlueVark on 2010-12-02
Here's the printout of testparm -s:

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[ext1]"
Processing section "[ihd2]"
Processing section "[zip1]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	interfaces = eth0
	security = SHARE
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	socket address = 192.168.0.350
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	comment = Home Directories
	read only = No
	create mask = 0700
	directory mask = 0700
	sync always = Yes
	delete readonly = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	read only = Yes
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = Yes

[ext1]
	comment = Guest access ext1
	path = /mymounts/ext1
	guest ok = Yes

[ihd2]
	comment = Guest access ihd2
	path = /mymounts/int2
	guest ok = Yes

[zip1]
	comment = Guest access zip1
	path = /mymounts/zip1
	guest ok = Yes

---

### Post by lrgmmc on 2010-12-02
forgot to add ```
browseable = yes
``` after guest ok = yes 
in the shares. add that and see if anything happens

---

### Post by BlueVark on 2010-12-02
The "browseable = yes" command is in the config file shares, but doesn't show up in the "testparm" file.  Don't exactly know why?

---

### Post by lrgmmc on 2010-12-02
```
smbtree
``` output?

---

### Post by BlueVark on 2010-12-02
Reply to smbtree = 
The program 'smbtree' is currently not installed.  You can install it by typing: sudo apt-get install smbclient

Should I install?  FYI...This is on a server, not a client.

---

### Post by lrgmmc on 2010-12-02
i know its the server. ```
sudo apt-get install smbclient
``` then run ```
smbtree
```

---

### Post by BlueVark on 2010-12-02
Result from "smbtree"=
WORKGROUP
	\\MIKE-LAPTOP    		mike-laptop server (Samba, Ubuntu)
		\\MIKE-LAPTOP\dropbox        	
		\\MIKE-LAPTOP\downloads      	
		\\MIKE-LAPTOP\IPC$           	IPC Service (mike-laptop server (Samba, Ubuntu))
		\\MIKE-LAPTOP\Darrell Backup Drive	
		\\MIKE-LAPTOP\Study          	
		\\MIKE-LAPTOP\Documents      	
		\\MIKE-LAPTOP\print$         	Printer Drivers

FYI...MIKE-LAPTOP is another one of my Ubuntu machines that is running Samba and works fine with all my Win XP machines.  

Thanks so much for helping...BlueVark

---

### Post by lrgmmc on 2010-12-02
i just stumbled on to a tool that may be of some use.```
sudo apt-get install swat
``` then conect to it from your remote pc like this [http://serverip:901](http://serverip:901) just use your servers ip . its i web tool in configuring samba looks promising.

---

### Post by Morbius1 on 2010-12-02
My only recommendation concerning swat is to make a backup of the smb.conf that worked 2 days ago. swat is destructive in that it rewrites and rearranges the existing smb.conf it doesn't edit it.

---

### Post by BlueVark on 2010-12-02
OK...I loaded the Samba Web Admin Tool.  It shows some strange indications.  It says:
version:	3.4.7
smbd:	not running
nmbd:	not running
winbindd:	not running

However, they do appear to be running on the server.  Not sure where to go from here?

---

### Post by Morbius1 on 2010-12-02
Excuse my ignorance but how difficult would it be to undo whatever you did to install the SSH server?

It all worked before SSH and now it doesn't so it sure does appear as if SSH is doing something to your ports or services. Did you follow a HowTo on SSH or is this something you just know how to do?

---

### Post by lrgmmc on 2010-12-02
have you changed root password on the server? if not on the server ```
sudo passwd root
``` then create the new password. when you login through the web use username = root and password = the one you just created. now you can go to status and start the proceses.

---

### Post by lrgmmc on 2010-12-02
well if it all comes down to it it might be better to start fresh. hopefully you have your drives set up in a manner that allows you to restore fast. then start installing things again.

---

### Post by BlueVark on 2010-12-02
Thanks folks for all the help...I think I'm just going to start over.  I have tried reversing and/or turning off the SSH and at least 2 dozen other things with no result so it's time to start over.  This is a learning process anyway.  

Thanks again...this is a really helpful forum and because of that I am a Ubuntu user for life (or at least as long as Ubuntu is around ;))

:D

---

### Post by lrgmmc on 2010-12-02
now thats the right attidude. try try try again. and like you said, it's a learning experiance. good luck.

---

### Post by Francisco on 2010-12-04
> **SteIMG said:**
> I have *just* seen the same thing.  I just installed the latest set of updates (4 updates - just a few kernel headers and bind type things I think -- can't remember).

Suddenly it has stopped appearing in the 'Network' on my Win 7 box.

You can browse to it by IP address -- and all works -- however this still need fixing. 

The smb.conf hasn't been touched.

Update:
I've just run Wireshark - and the Ubuntu box can see the 'Name Query' packets from the Win7 box -- but just is not replying to them.


I had the same issue happen after installing the update.

I fixed it by running:

> dpkg --configure -a and then I restarted smbd service it now pops up in Windows 7 network

---

