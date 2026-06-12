---
title: "Folder sharing: password required for share. What password??"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by Prium on 2009-07-01
What password indeed. Because it isn't one of mine. 

To begin with, I right clicked on my folder of interest and selected 'share options'. Then I checked 'share this folder' and let Ubuntu take care of the requisite service installations. When file manager reloaded I was presented with only two options: 'allow other people to write in this folder' and 'guest access..'; neither of which interested me. So, I clicked 'create share'. Then, from another PC, also running Ubuntu (Intrepid), I found the folder in the windows share and attempted to access it. I was then prompted to supply a password - 'username' and 'domain' were already entered in for me. How nice. But I already knew those anyway. What I don't know, and what wasn't entered in for me was some kind of password needed to access the folder. Not knowing what was being asked of me (i mean I never actually specified a password, see above) I tried the only 3 passwords I have ever entered into either machine. None worked. The folder couldn't be mounted. I'm stuck without network access to my folder (physical access is besides the point). 

sudo apt-get password? 

:lolflag:

---

### Post by Boondoklife on 2009-07-04
Was it not your login password?

---

### Post by superprash2003 on 2009-07-04
are you trying to share folders between 2 ubuntu machines?if your doing it via samba , then post contents of the following 2 files
1)/etc/samba/smb.conf
2)/etc/samba/smbusers

---

### Post by DSL5 on 2009-07-05
I am having a very simmilar problem

I am trying to access a folder I am sharing from a Windows 7 RC, but when I double click on the Computer in the network, I am propmted with the same screen that Prium described. None of my passwords work, and chaning the username from my linux one to my Windows one still doesn't work.

the contents of /etc/samba/smb.conf is:
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
```

I have no file called smbusers within /etc/samba

---

### Post by Boondoklife on 2009-07-06
Ok guys try this and tell me what you get back:
```
smbclient -L <servername>
```

Replace servername with you servers ip.

---

### Post by Prium on 2009-07-06
> Was it not your login password?

The login password for machine B, which is hosting the file? No, this doesn't work. Neither does any password I have ever set up on either machine A or B. That's what I meant by it being strange. 

> are you trying to share folders between 2 ubuntu machines?if your doing it via samba , then post contents of the following 2 files

Yes, both machines A and B run Ubuntu (although A is running Jaunty, and B is running Intrepid). I have not tried folder sharing through Samba yet. What I described was through the file manager/file browser (whtever it is called....via 'Places' -> 'Network' in the menubar)

Here is a screenshot of the password prompt:

[IMG]http://img268.imageshack.us/img268/9144/screenshotexr.png[/IMG]

---

### Post by superprash2003 on 2009-07-06
try this

remove the # from the security = user line .. and then add users to samba like this 
sudo smbpasswd -a username

then restart samba

---

### Post by DSL5 on 2009-07-06
> **Boondoklife said:**
> Ok guys try this and tell me what you get back:
```
smbclient -L <servername>
```

Replace servername with you servers ip.

I get a prompt asking for the password, which I enter, and then get the following output

```
session setup failed: SUCCESS - 0
```


> **superprash2003 said:**
> try this

remove the # from the security = user line .. and then add users to samba like this 
sudo smbpasswd -a username

then restart samba

doesn't seem to change anything. Still doesn't work

---

### Post by meeples on 2009-07-06
im getting this when trying to access folders on windows pc.

frustrating...

---

### Post by meeples on 2009-07-06
> Before showing a computer's shares, your system may prompt you for a name and password. Fill in the form with the credentials of a valid user for the computer you are connecting to. You may additionally store that password in your keyring for convenience.

Note: The default installation of Samba does not synchronize passwords. You may have to run "smbpasswd" for each user that needs to have access to his Ubuntu home directory from Microsoft Windows. 

thats from [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")

i'll try and get on my laptop to see if it works.

if this is the solution, samba should really have told us this itself.



USABILITY NIGHTMARE.

---

### Post by Boondoklife on 2009-07-06
try to use the computers ip instead of a hostname.
```
smbclient -L IPADDRESS
```

---

### Post by DSL5 on 2009-07-06
> **Boondoklife said:**
> try to use the computers ip instead of a hostname.
```
smbclient -L IPADDRESS
```

Guess I missunderstood before. I used the computer name when i got the previous results. Using the network name (WORKGROUP), and entering my password for my linux machine, I get the following:

```

Sharename       Type      Comment
---------       ----      -------
print$          Disk      Printer Drivers
IPC$            IPC       IPC Service (<COMPUTER NAME> server (Samba, Ubuntu))

Server               Comment
---------            -------

Workgroup            Master
---------            -------
WORKGROUP            <COMPUTER NAME>

```

<COMPUTER NAME> is the name for linux machine that I ran this command on (that's not the actual name, I replaced for my own privacy)

---

### Post by Boondoklife on 2009-07-06
ok you need to do this
```
smbclient -L <IP ADDRESS OF SERVER YOU WANT TO CONNECT TO>
```
and run it from the computer you are trying to connect from.

---

### Post by Prium on 2009-07-07
From what I gather after reading a little more online about it,  Windows-to-Ubuntu or Mac-to-Ubuntu file sharing requires: 

a) one to right click on a folder of interest and enable share (download services as necessary); 

b) [COLOR="Blue"]define a Samba account password using this command in the terminal:[/COLOR] [COLOR="Red"]sudo smbpasswd -a *username*
[I][/COLOR]
(replace 'username' with your own username)[/I]

What confuses me is in the case of Ubuntu-to-Ubuntu filesharing - is defining a Samba password really necessary? I mean it wasn't mentioned in any guide I read. In any case I will have a play around with Samba tonight and report back.

---

### Post by Boondoklife on 2009-07-07
> **Prium said:**
> From what I gather after reading a little more online about it,  Windows-to-Ubuntu or Mac-to-Ubuntu file sharing requires: 

a) one to right click on a folder of interest and enable share (download services as necessary); 

b) [COLOR=Blue]define a Samba account password using this command in the terminal:[/COLOR] [COLOR=Red]sudo smbpasswd -a *username*
[/COLOR][I]
(replace 'username' with your own username)[/I]

What confuses me is in the case of Ubuntu-to-Ubuntu filesharing - is defining a Samba password really necessary? I mean it wasn't mentioned in any guide I read. In any case I will have a play around with Samba tonight and report back.

Yes it is, most people that use a multi-nix network don't use samba, instead nfs is often used.

---

### Post by Prium on 2009-07-07
> **Boondoklife said:**
> Yes it is

How is it Boondoklife that you know what I have read? :tongue:

And for the record, there is no option to set filesharing to NFS or SMB when simply right-clicking on a folder of interest (at least using Intrepid or Jaunty). One is only presented with 'Share this folder' and 'Create this share'.

---

### Post by Boondoklife on 2009-07-07
LOL I meant yes it is needed =P

And yes you are right that there is not a way to point and click share via nfs but the time taken to setup such a share is normally worth it if you are interested in high speed transfers. My experience is that nfs is both a fast upload and download then samba.

---

### Post by DSL5 on 2009-07-08
> **Boondoklife said:**
> ok you need to do this
```
smbclient -L <IP ADDRESS OF SERVER YOU WANT TO CONNECT TO>
```
and run it from the computer you are trying to connect from.

Assuming that the <IP ADDRESS OF SERVER YOU WANT TO CONNECT TO> is the name of the workgroup (for me, WORKGROUP), then typing this in the terminal does not change anything. I still get a prompt for a password that doesn't work.

---

### Post by Prium on 2009-07-08
> **superprash2003 said:**
> try this

remove the # from the security = user line .. and then add users to samba like this 
sudo smbpasswd -a username

then restart samba

When trying these steps on the host machine I get: 

```
drmatt@drmatt-laptop:~$ sudo smbpasswd -a matt
New SMB password:
Retype new SMB password:
Failed to modify password entry for user matt
drmatt@drmatt-laptop:~$ 
```

---

### Post by Prium on 2009-07-08
_Sorry for the double post - but I have a solution_

Download **Samba** from Applications -> Add/Remove..

Once installed, run Samba from System -> Administration

Open Preferences from the menubar -> Samba Users

Add a new user. Don't worry about the Unix username. Just fill out everything else with respect to the client PC that will access the files. 

Next, Add Share (from the main Samba GUI).

Find your directory of interest and add it. Then click the Access tab and enable access for your newly created user. 

Close Samba. Now try accessing the share. Hopefully it should work.

---

### Post by Boondoklife on 2009-07-08
What part of "IP ADDRESS OF SERVER YOU WANT TO CONNECT TO" sounds like workgroup? You need to put in the ip of the machine that has the share you are trying to get to.

I persoanlly agree that I think it is just a user/permissions issue but that error might mean something else too.

---

### Post by DSL5 on 2009-07-09
> **Boondoklife said:**
> What part of "IP ADDRESS OF SERVER YOU WANT TO CONNECT TO" sounds like workgroup? You need to put in the ip of the machine that has the share you are trying to get to.

I persoanlly agree that I think it is just a user/permissions issue but that error might mean something else too.

Ok. It then prompts me for my password, which I enter, and then it tells me:
```
session setup failed: SUCCESS - 0
```

---

### Post by Bimps on 2009-10-25
I just had this problem myself, and was trying to access folders on a PC running WinXP, from a Ubuntu machine.
When I turned off Simple File Sharing in XP, and enabled sharing for the folders, I wasn't asked for a password anymore.

Control Panel --> Folder Options --> View tab --> uncheck "Use Simple File Sharing"

Then:

right-click on folder/drive --> Sharing tab

---

### Post by negora on 2010-09-26
Although it has passed 1 year since this thread was started, I've been facing the same problem on Ubuntu 10.04 (and also on previous versions). I believe that Ubuntu should provide some kind of option to synchronize the system users with Samba's when you share something from the Nautilus interface. Obviously, if you shared something from the command line, it should be you who took care of that aspect.

Anyway, thanks to the information of Prium on this thread, I could add a custom user to the Samba database and make it work. So thank you a lot :) .

---

### Post by tracar on 2010-12-19
i think i found an easier solution 

on the ***puter that has a folder you want to share....
 right click on that folder and enable sharing options.
then right click on that folder again and goto properties / permissions
and under "group" where it says "folder access" select anything but "---"
i chose "create and delete files" as this was intended to be a share folder.

once i did this i could access it from any of my windows or Linux systems over the network

hope this helps someone.

---

### Post by GordonFreeman69 on 2012-05-27
> **Bimps said:**
> I just had this problem myself, and was trying to access folders on a PC running WinXP, from a Ubuntu machine.
When I turned off Simple File Sharing in XP, and enabled sharing for the folders, I wasn't asked for a password anymore.

Control Panel --> Folder Options --> View tab --> uncheck "Use Simple File Sharing"

Then:

right-click on folder/drive --> Sharing tab

This fixed my problem, which was that I could see and open shared directories on the XP box (from Ubuntu), But I could not log into drives that were not shared. It (Ubuntu) would ask me for login name and password, but would not take it. Turned off "Simple File Sharing" on the XP box and now it works how I want it too.

Thanks

---

### Post by w-sky on 2012-07-20
Same old story with the most recent Ubuntu 12.04

In Nautilus I open the Sharing Options for the folder I want to share, then click "Share this folder", "Guest access" and "Create share".

But when I want to access that share from another computer, it will ask for username and password.

I chose "Guest access" because I do not want necessarily use a login, instead I want to have a free and easy local share. But How? Just to mention, I do trust everybody in my home network. :)

I guess this is necessary if anyone might care to help:
> **"smb.conf"]#======================= Global Settings =======================

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
 said:**
>  share to be setup on the
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

### Post by CharlesA on 2012-07-20
Please create a new thread. This one is from 2009.

---

