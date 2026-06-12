---
title: "which samba"
date: 2011-07-20
forum: Networking &amp; Wireless
---

### Post by bobk_nyc on 2011-07-20
I need to connect with windows, in order to use ubuntu, so I went to softwarecenter, and typed in samba, there are a whole slew of things there. which is samba that I need, I don't want to load a ton of stuff I may not need.   andI searched for a install guide, but all I find is a lot of tech jargen, and code...isn't there a simple install, and config for this?  thanks Bobk

---

### Post by capscrew on 2011-07-20
> **bobk_nyc said:**
> I need to connect with windows, in order to use ubuntu, so I went to softwarecenter, and typed in samba, there are a whole slew of things there. which is samba that I need, I don't want to load a ton of stuff I may not need.   andI searched for a install guide, but all I find is a lot of tech jargen, and code...isn't there a simple install, and config for this?  thanks Bobk

There are a multiple of ways to install Samba. Be aware that there are 2 versions of Samba listed.  The one you want is Samba 3.5, not Samba4.  Samba 4 is still experimental.

The first and simplest way is to right click on a folder you want to share and  select "sharing options".  Samba 3.5 will be installed the first time you do this.

The second way is to use Synaptics (System>>Administration>>Synaptic Package Manager).  Type Samba in the Quick Search box (Upper Middle) and find ***[COLOR="Blue"][SIZE="3"]samba[/SIZE][/COLOR]*** (***SMB/CIFS file print and login server***). Tick the boxes and click on apply. NOTE: You can see that there is only Samba and Samba4 with this listing -- Use Samba 3.5

Another way to install the same packages above is from the terminal with this command ```
sudo apt-get install samba
```

But you can also just install these packages from the Software Center: ***SMB/CIFS file print and login server***.  Just make sure it says Samba 3.5.

There are no "simple guides"  There are a million different opinions on what to do though.  If you choose the first option the shares can be configured using the GUI (as you would do it with windows).  There may be glitches, but that's way we have this forum.

---

### Post by bobk_nyc on 2011-07-20
i clicked, and picked install service...thanksI hope it works...

---

### Post by capscrew on 2011-07-20
> **bobk_nyc said:**
> i clicked, and picked install service...thanksI hope it works...

We're here if it doesn't.  :D

---

### Post by bobk_nyc on 2011-07-20
from windows, I can copy both way to linux box. but. from linux, I can see widows network/mshome,  but can not mount server  "Failed to retrieve share list from server"works from windows, but not from linux....50 %

---

### Post by capscrew on 2011-07-20
> **bobk_nyc said:**
> from windows, I can copy both way to linux box. but. from linux, I can see widows network/mshome,  but can not mount server  "Failed to retrieve share list from server"works from windows, but not from linux....50 %

Post the output of these two commands from the terminal```

hostname

```

and ```
cat /etc/samba/smb.conf
```

---

### Post by bobk_nyc on 2011-07-20
> **capscrew said:**
> Post the output of these two commands from the terminal```

hostname

```and ```
cat /etc/samba/smb.conf
```
no such file or directory

what does that mean?

---

### Post by bobk_nyc on 2011-07-20
hostname=penguin

---

### Post by capscrew on 2011-07-20
> **bobk_nyc said:**
> no such file or directory

what does that mean?

Those are two separate commands.  Lets do just one at a time.

From the terminal do this ```
hostname
```

If I do this on my machine I get the following```
capscrew@malibu:~$ hostname
malibu
capscrew@malibu:~$ 
```

The hostname of my machine is indeed *malibu*.

---

### Post by capscrew on 2011-07-20
> **bobk_nyc said:**
> hostname=penguin
So hostname returned *penguin*

The file /etc/samba/smb.conf must be there.  Maybe it was a typo. Don't forget the leading slash (/). Send me what you get, even if it is a error.  :-)

---

### Post by bobk_nyc on 2011-07-20
cat: /etc/samba/smb.conf:  no such file or directory

---

### Post by bobk_nyc on 2011-07-20
ilooked for the file and it is there

---

### Post by capscrew on 2011-07-20
> **bobk_nyc said:**
> cat: /etc/samba/smb.conf:  no such file or directory

:-)

```
cat**[COLOR="Red"]:[/COLOR]** /etc/samba/smb.conf
``` is not the same as ```
cat /etc/samba/smb.conf
```

---

### Post by capscrew on 2011-07-20
> **bobk_nyc said:**
> ilooked for the file and it is there

And I need to see at least the [Global] section of the file.  The command *cat* displays the file to the screen.  You can do the same thing this way too```
more /etc/samba/smb.conf
```

No colon ( : ) after the command.

---

### Post by bobk_nyc on 2011-07-20
cat: is what came back
typed it 3 times

---

### Post by bobk_nyc on 2011-07-20
thatcomes back the same

no such file or directory

---

### Post by bobk_nyc on 2011-07-20
this is what is in the file, but the commands don't get it

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
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

---

### Post by bobk_nyc on 2011-07-20
I'm gonna mess with this tommoeow, I have t get up early....this command line stuff puts me to sleep....thanks for what you tried to do....

bobk

---

### Post by capscrew on 2011-07-20
> **bobk_nyc said:**
> I'm gonna mess with this tommoeow, I have t get up early....this command line stuff puts me to sleep....thanks for what you tried to do....

bobk

Fine by me.

---

### Post by bobk_nyc on 2011-07-21
After a lossey nights sleep, I am going to spend a little time today trying to solve this.seems the issue is with linus, probably some security thing that needs to be over riddin. windows seems to work fine...so how do I make linux play nice on the network?  or am I asking too much....I guess I can always go back to the sneaker net... thanks ahead for any ideas.

Bobk:)

---

### Post by capscrew on 2011-07-21
> **bobk_nyc said:**
> After a lossey nights sleep, I am going to spend a little time today trying to solve this.seems the issue is with linus, probably some security thing that needs to be over riddin. windows seems to work fine...so how do I make linux play nice on the network?  or am I asking too much....I guess I can always go back to the sneaker net... thanks ahead for any ideas.

Bobk:)
It's not a security issue.  It's a naming issue.  In the [global] section of the /etc/samba/smb.conf file add the following ```
netbios name = penguin
```

---

### Post by bobk_nyc on 2011-07-21
> **capscrew said:**
> It's not a security issue.  It's a naming issue.  In the [global] section of the /etc/samba/smb.conf file add the following ```
netbios name = penguin
```

I tried to edit the file, but it won't let me, when I go to properties, to see if it is read only ,sas I can 't change it becuase i am not the owner...I am the only one on the computer....

---

### Post by capscrew on 2011-07-21
> **bobk_nyc said:**
> I tried to edit the file, but it won't let me, when I go to properties, to see if it is read only ,sas I can 't change it becuase i am not the owner...I am the only one on the computer....
What editor do you want to use?

---

### Post by bobk_nyc on 2011-07-21
I clicked on it, and it opened, saya gedit

---

### Post by capscrew on 2011-07-21
> **bobk_nyc said:**
> I clicked on it, and it opened, saya gedit

You have to use the editor as the user "root".  To edit the file you need to:
[LIST]
[*]Select Alt+f2
[*]In the box type: gksudo gedit
[*]Click on the button that says: Run with file.. 
[*]Navigate to the file /etc/samba/smb.conf
[*]Edit and save the file
[*]Restart Samba from the terminal with: sudo service smbd restart 
[/LIST]

---

### Post by bobk_nyc on 2011-07-21
well, i did  that stuff, an it didn't work, so I rebooted to be sure, and still "Failed to retrieve share list from server"

here is the change, is it correct?

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

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
;   netbios name = penguin


di I have to change where it says workgroup?  my windows machine all have msnome as a domain...or should maybe I rename my windows machines to workgroup

---

### Post by capscrew on 2011-07-21
> **bobk_nyc said:**
> well, i did  that stuff, an it didn't work, so I rebooted to be sure, and still "Failed to retrieve share list from server"

here is the change, is it correct?

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

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
;   netbios name = penguin


di I have to change where it says workgroup?  my windows machine all have msnome as a domain...or should maybe I rename my windows machines to workgroup

This is wrong```
[COLOR="Red"]**;**[/COLOR]   netbios name = penguin


```

The correct way is ```
   netbios name = penguin


```

You can change the WORKGROUP to```
workgroup = MSHOME
```

You have to restart Samba everythime you modify the confing file, so restart it or reboot the whole system.

FYI -- the semicolon ( ; ) tells Samba to ignore this line.  That's why nothing happened.

---

### Post by bobk_nyc on 2011-07-21
well, that didn't work...here is the new


[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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
   netbios name = penguin


I remember using samba back with redhat i think 8, and with mandrake(before I gave up on them then)..and it just worked. what is different

---

### Post by capscrew on 2011-07-21
> **bobk_nyc said:**
> well, that didn't work...here is the new


```
[global]

...

   netbios name = penguin

```

I remember using samba back with redhat i think 8, and with mandrake(before I gave up on them then)..and it just worked. what is different

Samba is basically the same.  Maybe version 2 to version 3.  When you say "that didn't work..."; what do you see?  What do you get with this command?```
smbtree -d3
```

What is the output of ```
smbclient -d3 -L penguin
```

---

### Post by bobk_nyc on 2011-07-21
bobk@penguin:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::200:94ff:feb6:d4b5%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=fe80::76ea:3aff:fe8d:9a0f%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.192 bcast=192.168.0.255 netmask=255.255.255.0
Enter bobk's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Got a positive name query response from 192.168.0.115 ( 192.168.0.115 )
Connecting to host=192.168.0.115
Connecting to 192.168.0.115 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.198 ( 192.168.0.198 )
Got a positive name query response from 192.168.0.115 ( 192.168.0.115 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.198 ( 192.168.0.198 )
Connecting to host=192.168.0.198
Connecting to 192.168.0.198 at port 445
Connecting to 192.168.0.198 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Receiving SMB: Server stopped responding
SPNEGO login failed: NT_STATUS_IO_TIMEOUT
anonymous failed session setup with NT_STATUS_IO_TIMEOUT
Connecting to host=ASUS-I7
Connecting to 192.168.0.198 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.30
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
SPNEGO login failed: Logon failure

---

### Post by bobk_nyc on 2011-07-21
bobk@penguin:~$ smbclient -d3 -L penguin
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::200:94ff:feb6:d4b5%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=fe80::76ea:3aff:fe8d:9a0f%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.192 bcast=192.168.0.255 netmask=255.255.255.0
Client started (version 3.5.8).
Enter bobk's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name penguin<0x20>
resolve_wins: Attempting wins lookup for name penguin<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name penguin<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.5.8]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    IPC$            IPC       IPC Service (penguin server (Samba, Ubuntu))
    torrents        Disk      ubuntu
resolve_lmhosts: Attempting lmhosts lookup for name penguin<0x20>
resolve_wins: Attempting wins lookup for name penguin<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name penguin<0x20>
Connecting to 127.0.1.1 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.5.8]

    Server               Comment
    ---------            -------
    BOBK-PC              
    PENGUIN              penguin server (Samba, Ubuntu)

    Workgroup            Master
    ---------            -------
    MSHOME               BOBK-PC
bobk@penguin:~$

---

### Post by capscrew on 2011-07-21
A quick look tells me that Samba is working, but not successfully logging into your windows hosts.

I have to be gone for a few hours.  I had hoped this would be simple and quick.  I will look at it again later.

---

### Post by bobk_nyc on 2011-07-21
thanks, I got no clue.

---

### Post by capscrew on 2011-07-21
Looking at the data from the 2 commands (smbtree and smbclient) shows that you have at least 2 problems.
[LIST=1]
[*]You can't login to the windows machines
[*]Your Ubuntu machine uses a non network IP address 127.0.1.1
[/LIST] 

This shows the smbtree login problems```
Connecting to host=192.168.0.115
Connecting to 192.168.0.115 at port 445

SPNEGO login failed: Logon failure
...

Connecting to 192.168.0.198 at port 445
Connecting to 192.168.0.198 at port 139
Doing spnego session setup (blob length=5

Receiving SMB: Server stopped responding
SPNEGO login failed: NT_STATUS_IO_TIMEOUT
...
anonymous failed session setup with NT_STATUS_IO_TIMEOUT
Connecting to host=ASUS-I7
Connecting to 192.168.0.198 at port 445
SPNEGO login failed: Logon failure
```

Smbclient reveals the loopback address in use rather than a LAN address```
resolve_hosts: Attempting host lookup for name penguin<0x20>
Connecting to 127.0.1.1 at port 445
```

Post the output of ```
cat /etc/hosts
```

Is the users on the Windows machines the same as the user on the Ubuntu machine?  Do they all have the same username/login.  Have you added this to the smbpasswd database?  Post the output of ```
sudo pdbedit -L
```

---

### Post by bobk_nyc on 2011-07-22
all the windows machines have the same user, me

here is the other thing

bobk@penguin:~$ sudo pdbedit -L
[sudo] password for bobk: 
nobody:65534:nobody
bobk:1000:bobk
bobk@penguin:~$

---

### Post by bobk_nyc on 2011-07-22
bobk@penguin:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    penguin

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
bobk@penguin:~$

---

### Post by capscrew on 2011-07-22
> **bobk_nyc said:**
> bobk@penguin:~$ ```
cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    penguin

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
bobk@penguin:~$
```

Lets work on this first.  I want you to replace this line```
[COLOR="Red"]**;**[/COLOR] name resolve order = lmhosts host wins [COLOR="Red"]**bcast**[/COLOR]
```

With this line ```
 name resolve order = **[COLOR="Red"]bcast[/COLOR]** lmhosts host wins 
```

With this we are making Samba look for all services via broadcasts on the local network and not internally.

---

### Post by bobk_nyc on 2011-07-22
> **capscrew said:**
> Lets work on this first.  I want you to replace this line```
[COLOR=Red]**;**[/COLOR] name resolve order = lmhosts host wins [COLOR=Red]**bcast**[/COLOR]
```With this line ```
 name resolve order = **[COLOR=Red]bcast[/COLOR]** lmhosts host wins 
```With this we are making Samba look for all services via broadcasts on the local network and not internally.

OK,now I see the ctive  win machine, but it wil not accept a passwod...I will mess with it

---

### Post by capscrew on 2011-07-22
> **bobk_nyc said:**
> OK,now I see the ctive  win machine, but it wil not accept a passwod...I will mess with it

Make notes of what you do in case we need to undo stuff.

Are you sure the user *"bobk"* is a user on the Windows machine?  Did you password protect the share on the Windows machine?

FYI -- when I say user I'm not referring to a human, I'm referring to the user account.  I assume *"me" *is not a user account.

---

### Post by bobk_nyc on 2011-07-23
> **capscrew said:**
> 

Are you sure the user *"bobk"* is a user on the Windows machine?  Did you password protect the share on the Windows machine?

FYI -- when I say user I'm not referring to a human, I'm referring to the user account.  I assume *"me" *is not a user account.

bobk is my login onall my machines.I don't PW anything if I can help it, but if I do, there is only one pw for all the things on machines...I can't remember otherwise.

---

### Post by bobk_nyc on 2011-07-23
Iwhen I try to open any folder on windows, says I don't have permission. I don't get it, now it is not asking for a PW, but tells me I don't have permission...this is too much ecurity...Is there a way to turn off all the security on linu? or is just built in.....

---

### Post by Morbius1 on 2011-07-23
@capscrew, Sorry for the interruption I hope you don't mind.
> Iwhen I try to open any folder on windows, says I don't have permission.  I don't get it, now it is not asking for a PW, but tells me I don't  have permission...this is too much ecurity...Is there a way to turn off  all the security on linu? or is just built in.....     
Based on that description it' not Linux that's asking you for permissions, it's just relaying the message it's getting from Windows. What would be very helpful to capscrew I think would be if you told him what version of Windows you are using. I couldn't find it in your posts.

---

### Post by bobk_nyc on 2011-07-23
> **Morbius1 said:**
> @capscrew, Sorry for the interruption I hope you don't mind.
Based on that description it' not Linux that's asking you for permissions, it's just relaying the message it's getting from Windows. What would be very helpful to capscrew I think would be if you told him what version of Windows you are using. I couldn't find it in your posts.

I am runnibg win 7,I have permission s set to everyone...with full rights, and password set to off. I have 2 win machines, adnI can copy between them with no passwords, or other issues.

---

