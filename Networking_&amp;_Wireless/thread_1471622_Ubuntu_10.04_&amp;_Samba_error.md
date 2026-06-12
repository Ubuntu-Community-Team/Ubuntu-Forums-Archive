---
title: "Ubuntu 10.04 &amp; Samba error"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by verbitan on 2010-05-03
Hi there,

I recently upgraded my server from 9.10 to 10.04 via the command prompt, pretty standard. However, I have noticed one thing that now doesn't work. Samba.

What happens is samba says that it is running, my smb.conf is the same as before, but now it does not show up on my network on the windows computers. It is like samba is ignoring the "netbios name" in the conf file.

I ran testparm, and it showed that all my shares were correctly recognised, in fact it showed everything as in the conf file, apart from "netbios name".

Has this been changed in the most recent version of samba, or is it an Ubuntu thing?

Many thanks,

Nick

---

### Post by apetlund on 2010-05-03
I have experienced the same issue. nmblookup does not return any address for my hostname. It worked until the upgrade to 10.04.

Here is my smb.conf. removed the "share modes"-directives since they were listed as deprecated in the logs. The smb share works, but netbios lookup does not.

The netbios-ssn port (139) is listed open on my system.

Below is my smb.conf

Cheers,
Andreas
===============


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
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = hostname

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
#   name resolve order = lmhosts host wins bcast

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
   security = user

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
printing = cups
printcap name = cups

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
#  browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

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

[Share]
comment = My Samba share
path = /share/path
guest ok = no
read only = no
#share modes = no

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
browseable = yes
path = /var/spool/samba
printable = yes
guest ok = yes
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
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

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

### Post by jaredheath on 2010-05-03
Same issue.

Installed from update manager.  Samba starts/stops/restarts successfully with the new startup process.

testparm shows the smb.conf has no problems, smbclient -L localhost -U% shows the shares, but smbclient -L <server name> gives NT_STATUS_CONNECTION_REFUSED.

---

### Post by verbitan on 2010-05-04
Hmm I'm glad it's not just me then! I can't imagine that they removed this from samba, as that would be pretty stupid. I guess it's just a new conf keyword or something.

I can't find anything from Google though, hence I posted here...

---

### Post by Morbius1 on 2010-05-04
verbitan,

You stated that "samba says that it's running". I presume you did something like this:

**sudo service smbd status**

Did you make sure nmbd was running:

**sudo service nmbd status**

The old "samba" service combined the smbd and nmbd daemons into one service. Now that we're back to the good old days, each daemon needs to be started separately.

---

### Post by verbitan on 2010-05-04
> **Morbius1 said:**
> verbitan,

You stated that "samba says that it's running". I presume you did something like this:

**sudo service smbd status**

Did you make sure nmbd was running:

**sudo service nmbd status**

The old "samba" service combined the smbd and nmbd daemons into one service. Now that we're back to the good old days, each daemon needs to be started separately.
Yeah, both those services are running...which results in me being able to access the share in windows by typing \\192.168.1.100 but not \\netbiosName

This is the real problem...

[B]EDIT:

[/B][QUOTE=smb.conf]
[global]
# Browsing / Identification #
        workgroup = JAMES FAMILY
        netbios name = Backup
        server string = Server

# Authentication #
        security = user
        encrypt passwords = true
        map to guest = bad user
        guest account = nobody

        passdb backend = tdbsam
        obey pam restrictions = yes
        unix password sync = yes
        pam password change = yes
        invalid users = root

        socket options = TCP_NODELAY
        preferred master = yes

# Public shares
[Music]
        comment = Family Music
        path = /media/NAS DRIVE/Music
        public = no
        browsable = yes
        read only = no
        writeable = yes
        create mask = 0777
        directory mask = 0777
        valid users = @sambashare
        write list = verbitan

[Upload Music Here]
        comment = Any music needing to go into the Music share.
        path = /media/NAS DRIVE/PendingMusic
        public = no
        browsable = yes
        read only = no
        writeable = yes
        create mask = 0777
        directory mask = 0777
        valid users = @sambashare
        write list = @sambashare

[Photos]
        comment = Family Photos
        path = /media/NAS DRIVE/Photos
        public = no
        browsable = yes
        read only = no
        writeable = yes
        create mask = 0777
        directory mask = 0777
        valid users = @sambashare
        write list = @sambashare

[Programs]
        comment = Installers for programs
        path = /media/NAS DRIVE/Programs
        public = no
        browsable = yes
        read only = no
        writeable = yes
        create mask = 0777
        directory mask = 0777
        valid users = @sambashare
        write list = @sambashare

# private shares
[Nick]
        comment = Nicks Backup
        path = /media/NAS DRIVE/Nick
        public = no
        browsable = yes
        read only = no
        writeable = yes
        create mask = 0777
        directory mask = 0777
        valid users = verbitan
        write list = verbitan
[Mum]
        comment = Mums Backup
        path = /media/NAS DRIVE/Mum
        public = no
        browsable = yes
        read only = no
        writeable = yes
        create mask = 0777
        directory mask = 0777
        valid users = karen
        write list = karen

[Dad]
        comment = Dads Backup
        path = /media/NAS DRIVE/Dad
        public = no
        browsable = yes
        read only = no
        writeable = yes
        create mask = 0777
        directory mask = 0777
        valid users = gerry
        write list = gerry

[Amber]
        comment = Ambers Backup
        path = /media/NAS DRIVE/Amber
        public = no
        browsable = yes
        read only = no
        writeable = yes
        create mask = 0777
        directory mask = 0777
        valid users = ambeth
        write list = ambeth

[MSDNAA]
        comment = Nicks MSDNAA Programs
        path = /media/NAS DRIVE/MSDNAA
        public = no
        browsable = yes
        read only = no
        writeable = yes
        create mask = 0777
        directory mask = 0777
        valid users = verbitan
        write list = verbitan
[Public]
        comment = A public share.
        path = /media/NAS DRIVE/Public
        public = no
        browsable = yes
        read only = no
        writeable = yes
        create mask = 0777
        directory mask = 0777
        valid users = @sambashare nobody
        write list = @sambashare nodoby

[/QUOTE]
[QUOTE=testparm]
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Music]"
Processing section "[Upload Music Here]"
Processing section "[Photos]"
Processing section "[Programs]"
Processing section "[Nick]"
Processing section "[Mum]"
Processing section "[Dad]"
Processing section "[Amber]"
Processing section "[MSDNAA]"
Processing section "[Public]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = JAMES FAMILY
        server string = Server
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        unix password sync = Yes
        preferred master = Yes
        invalid users = root

[Music]
        comment = Family Music
        path = /media/NAS DRIVE/Music
        valid users = @sambashare
        write list = verbitan
        read only = No
        create mask = 0777
        directory mask = 0777

[Upload Music Here]
        comment = Any music needing to go into the Music share.
        path = /media/NAS DRIVE/PendingMusic
        valid users = @sambashare
        write list = @sambashare
        read only = No
        create mask = 0777
        directory mask = 0777

[Photos]
        comment = Family Photos
        path = /media/NAS DRIVE/Photos
        valid users = @sambashare
        write list = @sambashare
        read only = No
        create mask = 0777
        directory mask = 0777

[Programs]
        comment = Installers for programs
        path = /media/NAS DRIVE/Programs
        valid users = @sambashare
        write list = @sambashare
        read only = No
        create mask = 0777
        directory mask = 0777

[Nick]
        comment = Nicks Backup
        path = /media/NAS DRIVE/Nick
        valid users = verbitan
        write list = verbitan
        read only = No
        create mask = 0777
        directory mask = 0777

[Mum]
        comment = Mums Backup
        path = /media/NAS DRIVE/Mum
        valid users = karen
        write list = karen
        read only = No
        create mask = 0777
        directory mask = 0777

[Dad]
        comment = Dads Backup
        path = /media/NAS DRIVE/Dad
        valid users = gerry
        write list = gerry
        read only = No
        create mask = 0777
        directory mask = 0777

[Amber]
        comment = Ambers Backup
        path = /media/NAS DRIVE/Amber
        valid users = ambeth
        write list = ambeth
        read only = No
        create mask = 0777
        directory mask = 0777

[MSDNAA]
        comment = Nicks MSDNAA Programs
        path = /media/NAS DRIVE/MSDNAA
        valid users = verbitan
        write list = verbitan
        read only = No
        create mask = 0777
        directory mask = 0777

[Public]
        comment = A public share.
        path = /media/NAS DRIVE/Public
        valid users = @sambashare, nobody
        write list = @sambashare, nodoby
        read only = No
        create mask = 0777
        directory mask = 0777
[/QUOTE]

As you can see, some of the smb.conf settings are not parsed like they were before. Although I can see all the shares via \\192.168.1.100 I cannot actually access any of them, as it is saying the credentials are incorrect...even though they have been working fine before the upgrade!

---

### Post by jaredheath on 2010-05-04
Wanted to say the nmbd service was entirely my issue.

It isn't auto-starting for me with 10.04....something that really should be publicized and/or fixed if a split up of such a common system app happens in a release.

---

### Post by capscrew on 2010-05-04
> **jaredheath said:**
> Wanted to say the nmbd service was entirely my issue.

It isn't auto-starting for me with 10.04....something that really should be publicized and/or fixed if a split up of such a common system app happens in a release.

I certainly am no expert with Samba and Lucid (is anybody yet?).  I can say that Samba services are now started by Upstart scripts and that is why NMBD is separated from SMBD.  I believe that the init.d script is what put them together.

A second point to note is that if the interface is not "up" when NMBD is initiated it will die.   Are you using DHCP? Or worse yet network-manager?

You can always make the Samba server a WINS server and Windows hosts will use that instead of broadcasting.  They are normally set to "hybrid" mode for just that purpose.

---

### Post by joe_newbie on 2010-05-04
same problem here running: "initctl status smbd
returns: smbd start/running, process 689

initctl status nmbd
nmbd start/running, process 1224


I have found that running: sudo restart smbd
will fix the problem temporarily; however after a reboot the daemon needs to be restarted again before it will work properly.

I am using a static IP for this machine.

In my case I cannot access the share using an ip address or the hostname of the server.

Joe

---

### Post by verbitan on 2010-05-05
My server is also setup with a static ip. Everything else on it works fine, just the samba share that doesnt. I have even tried apt-get remove --purge samba, and reinstalled it with no avail...

This is like the main feature of my server so I need it fixed...

[B]EDIT:

[/B]I have tried this again, and even with the default settings, the server is not accessible.

---

### Post by pettitti on 2010-05-06
I had the same problem after I installed 10.04, replacing 9.04 (to go from 32 to 64bit). I copied across the smb.conf and installed the required packages but it wouldn't work until I created a smbpassword

I used these instructions:

[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)

---

### Post by verbitan on 2010-05-06
> **pettitti said:**
> I had the same problem after I installed 10.04, replacing 9.04 (to go from 32 to 64bit). I copied across the smb.conf and installed the required packages but it wouldn't work until I created a smbpassword

I used these instructions:

[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)

Interestingly, manually updating all the passwords seemed to fix the file access issue. I didnt think to try that, as it was an upgrade via the terminal rather than a fresh install... Thanks! = )

However, although this now works with \\192.168.1.100 it still does not work with \\serverName ..? I defiantly have smbd and nmbd running.

---

### Post by pettitti on 2010-05-06
This is what I have done on every Ubuntu install I have done on my work machines:[FONT=monospace]```
sudo apt-get install SMBFS winbind
```[/FONT]
 edit /etc/nsswitch.conf: change: 
 [LEFT][FONT=monospace]```
hosts: files dns
```[/FONT][/LEFT]
 to: 
 [LEFT][FONT=monospace]```
hosts: files dns wins
```
[FONT=Arial]I have also including the information on the wins server in smb.conf and I can access shares on my Ubuntu machine from Windows XP [/FONT]
[/FONT][/LEFT]

---

### Post by pricetech on 2010-05-06
Fixed it for me also.  All I did was run the smbpasswd command and everything started working just fine.

I already had everything installed via Synaptics and set up via the gui tool.

All my shares are hidden though, so I don't use browsing anyway.

---

### Post by verbitan on 2010-05-07
> **pettitti said:**
> This is what I have done on every Ubuntu install I have done on my work machines:[FONT=monospace]```
sudo apt-get install SMBFS winbind
```[/FONT]
 edit /etc/nsswitch.conf: change: 
 [LEFT][FONT=monospace]```
hosts: files dns
```[/FONT][/LEFT]
 to: 
 [LEFT][FONT=monospace]```
hosts: files dns wins
```[FONT=Arial]I have also including the information on the wins server in smb.conf and I can access shares on my Ubuntu machine from Windows XP [/FONT]
[/FONT][/LEFT]

What did you include in your smb.conf about the wins server? This is the last little step now...such an annoying thing too!

---

### Post by Tiberion on 2010-05-11
These instructions worked great except you don't have to modify the smb.conf file.  Just set the password.  Thanks for the post


 					Originally Posted by **pettitti** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9248116#post9248116") 				
 				[I]I had the same problem after I  installed 10.04, replacing 9.04 (to go from 32 to 64bit). I copied  across the smb.conf and installed the required packages but it wouldn't  work until I created a smbpassword

I used these instructions:

[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)[/I]

---

### Post by Rangelus on 2010-05-18
I have this same error.  Further, my Ubuntu box is unable to view any windows machines on the network.  I, too, upgraded from 9.10 to 10.04 using the GUI updater.

---

### Post by Vock on 2010-05-18
> **pettitti said:**
> I had the same problem after I installed 10.04, replacing 9.04 (to go from 32 to 64bit). I copied across the smb.conf and installed the required packages but it wouldn't work until I created a smbpassword

I used these instructions:

[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)

I spent 3 days wasting me time trying to get my old samba share working using the old config file. For some reasong nothing was working. I decided to try from a clean smb.conf file.

 I removed my old samba config files that i had edited, to do this I used nautilus as root to remove them, as I am a bit cautious using sudo rm -rf /etc/samba. If someone knows a better way please correct me, this is just what I did and I'd hate to have people make mistakes that could hurt their system, so I tend to use a GUI when playing around with removing system folders.

```
 gksu nautilus 
```

and from there I went to /etc/samba and deleted everything inside the folder. I then copied the original smb.conf file that comes when you install samba from /usr/share/samba and put it into /etc/samba and started with that.

Followed the guide above, and for some reason it decided to work this time around. I really don't know what to attribute it to, I did the smbpasswd -a before.

What I would recommend to people is really go through the How-To mentioned above, starting with the basic samba share that is mentioned, and once you know for sure that's working, then you've eliminated any possible firewall/routing problems. Then it's just a matter of setting up your shares.

Good luck everyone.

---

### Post by verbitan on 2010-08-13
Hi again,

I just thought I would update everyone...

Basically I gave up on this, and totally reinstalled Ubuntu 10.04, whacked in my smb.conf and it worked straight away! As far as I could tell, nothing was different to before. So, annoyed yet pleased I continued happily.

However, after many weeks of it working fine, I have been away on holiday for two weeks, I come back and it's broken again! Exactly the same as before! Now I haven't touched or changed anything, I haven't been here to do so! :mad:

Ah well, hopefully this is something that gets fixed in 10.10...

---

### Post by verbitan on 2010-08-13
Also, I have discovered that I cannot access the server via its hostname under any protocol...so I can't SSH using hostname, only the IP, same with http, or MySQL :(

---

### Post by capscrew on 2010-08-13
> **verbitan said:**
> Also, I have discovered that I cannot access the server via its hostname under any protocol...so I can't SSH using hostname, only the IP, same with http, or MySQL :(

This can only mean that you are not running local name services (DNS, etc.) or it is broken.

---

### Post by verbitan on 2010-08-14
> **capscrew said:**
> This can only mean that you are not running local name services (DNS, etc.) or it is broken.
So how can I fix it? :)

---

### Post by capscrew on 2010-08-14
> **verbitan said:**
> So how can I fix it? :)

I would start by making sure that there is no firewall running that could block the NetBIOS broadcasts.  You can check by running Wireshark on the suspected machine.

---

### Post by Morbius1 on 2010-08-14
I've always used some variation of the nmap command on linux to see if the remote machine has ports open. For example:
```
nmap -PN 192.168.0.110
```Where 192.168.0.110 is the remote machine's ip address.

This will output the following if the necessary ports are open:
> Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-08-14 12:42 EDT
Interesting ports on 192.168.0.110:
Not shown: 997 closed ports
PORT    STATE SERVICE
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
631/tcp open  ipp
I don't know if this is the best tool to use but it's the one I choose first.

---

### Post by capscrew on 2010-08-14
> **Morbius1 said:**
> I've always used some variation of the nmap command on linux to see if the remote machine has ports open. For example:
```
nmap -PN 192.168.0.110
```Where 192.168.0.110 is the remote machine's ip address.

This will output the following if the necessary ports are open:
I don't know if this is the best tool to use but it's the one I choose first.

A good point.  The diagnosis can be from either end of the chain.  

I feel that seeing actual broadcast packets shows that the ports are open and that broadcasts are being sent.  With nmap you can only tell that the ports are open on the host.

---

### Post by verbitan on 2010-08-14
A scan from my laptop shows this...

```

Interesting ports on 192.168.1.100:
Not shown: 993 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
10000/tcp open  snet-sensor-mgmt
20000/tcp open  unknown
49153/tcp open  unknown

```

---

### Post by capscrew on 2010-08-14
> **verbitan said:**
> A scan from my laptop shows this...

```

Interesting ports on 192.168.1.100:
Not shown: 993 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
10000/tcp open  snet-sensor-mgmt
20000/tcp open  unknown
49153/tcp open  unknown

```

Does that mean there is no broadcast NetBIOS traffic to UDP ports 137 and 138?  To browse you need UDP broadcast traffic.

Edit:  See [**_here_**]("http://en.wikipedia.org/wiki/NetBIOS").

---

### Post by verbitan on 2010-08-14
As far as I can tell yeah...Although I haven't setup any firewall :confused:

---

### Post by verbitan on 2010-08-14
I have also tried [this]("https://bugs.launchpad.net/ubuntu/+bug/140663") which seemed hopeful! But with no luck :(

---

### Post by capscrew on 2010-08-14
> **verbitan said:**
> As far as I can tell yeah...Although I haven't setup any firewall :confused:

How did you "scan" the ports.  Ntop allows you to scan UDP ports.  Wireshark will definitely tell you whether you have UDP broadcasts.

---

### Post by capscrew on 2010-08-14
> **verbitan said:**
> I have also tried [this]("https://bugs.launchpad.net/ubuntu/+bug/140663") which seemed hopeful! But with no luck :(

Guessing is rarely the answer.

---

### Post by verbitan on 2010-08-14
I scanned only using nmap, I don't have a GUI on the server so I couldn't install wireshark...unless it has a CLI?

Also, now I can access the server using hostname.local AND the IP, but not just hostname. I think i'm getting there!

Although if I ping hostname.local it returns the IPv6 address interestingly...

---

### Post by capscrew on 2010-08-14
> **verbitan said:**
> I scanned only using nmap, I don't have a GUI on the server so I couldn't install wireshark...unless it has a CLI?

Yes it does.> 

Also, now I can access the server using hostname.local AND the IP, but not just hostname. I think i'm getting there!

This means you are using Avahi to resolve local hostnames rather than DNS or NetBIOS.  I don't think Avahi is a good idea with Samba running.  Samba can resolve DNS to NetBIOS.  I have no idea about mDNS (Avahi).  I would return the /etc/nsswitch.conf to original configuration.

---

### Post by verbitan on 2010-08-14
Ok I've reverted it, turns out it made no difference anyway...

So what exactly do I need to do with wireshark?

Ps. Thanks for trying!

---

### Post by capscrew on 2010-08-14
> **verbitan said:**
> Ok I've reverted it, turns out it made no difference anyway...

So what exactly do I need to do with wireshark?

Ps. Thanks for trying!

Since you are using NMap, let's try this first:

```
nmap -sS -sU -T4 <The_IP_address>
```

Post your results.

---

### Post by verbitan on 2010-08-14
> **capscrew said:**
> Post your results.
```

Interesting ports on 192.168.1.100:
Not shown: 1987 closed ports
PORT      STATE         SERVICE
22/tcp    open          ssh
25/tcp    open          smtp
53/tcp    open          domain
139/tcp   open          netbios-ssn
445/tcp   open          microsoft-ds
10000/tcp open          snet-sensor-mgmt
20000/tcp open          unknown
53/udp    open|filtered domain
68/udp    open|filtered dhcpc
137/udp   open|filtered netbios-ns
138/udp   open|filtered netbios-dgm
5353/udp  open|filtered zeroconf
10000/udp open|filtered unknown

```

---

### Post by capscrew on 2010-08-14
> **verbitan said:**
> ```

Interesting ports on 192.168.1.100:
Not shown: 1987 closed ports
PORT      STATE         SERVICE
22/tcp    open          ssh
25/tcp    open          smtp
53/tcp    open          domain
139/tcp   open          netbios-ssn
445/tcp   open          microsoft-ds
10000/tcp open          snet-sensor-mgmt
20000/tcp open          unknown
53/udp    open|filtered domain
68/udp    open|filtered dhcpc
[COLOR="Red"][B]137/udp   open|filtered netbios-ns
138/udp   open|filtered netbios-dgm[/B][/COLOR]
5353/udp  open|filtered zeroconf
10000/udp open|filtered unknown

```

The ports we have been talking about are shown in red.  They are open.

I assume this is a scan of an Ubuntu host with Samba running.  Do you have a Windows host that you can scan this way?

---

### Post by verbitan on 2010-08-14
> **capscrew said:**
> Do you have a Windows host that you can scan this way?
I do, my Windows 7 laptop...

When I ran "nmap -sS -sU -T4 192.168.1.103" I got,
```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-15 00:36 BST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 0.54 seconds

```So I ran "nmap -sS -sU -T4 -PN 192.168.1.103" and I got,
```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-15 00:36 BST
Interesting ports on 192.168.1.103:
Not shown: 1000 open|filtered ports, 995 filtered ports
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2869/tcp open  unknown
5357/tcp open  unknown
MAC Address: 00:15:AF:26:18:92 (AzureWave Technologies)

Nmap done: 1 IP address (1 host up) scanned in 10.45 seconds

```Now I have disabled the built in firewall, and am running the first scan again...but it is taking ages...and so far has produced the message,
```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-15 00:37 BST
Warning: Giving up on port early because retransmission cap hit.

```

---

### Post by capscrew on 2010-08-14
> **verbitan said:**
> I do, my Windows 7 laptop...

When I ran "nmap -sS -sU -T4 192.168.1.103" I got,
```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-15 00:36 BST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 0.54 seconds

```So I ran "nmap -sS -sU -T4 -PN 192.168.1.103" and I got,
```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-15 00:36 BST
Interesting ports on 192.168.1.103:
Not shown: 1000 open|filtered ports, 995 filtered ports
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2869/tcp open  unknown
5357/tcp open  unknown
MAC Address: 00:15:AF:26:18:92 (AzureWave Technologies)

Nmap done: 1 IP address (1 host up) scanned in 10.45 seconds

```Now [COLOR="Red"]**I have disabled the built in firewall**[/COLOR], and am running the first scan again...but it is taking ages...and so far has produced the message,
```

Starting Nmap 5.00 ( http://nmap.org ) at 2010-08-15 00:37 BST
Warning: Giving up on port early because retransmission cap hit.

```

Built in Firewall?  :-(  I thought we had no firewall on the network.  This can be the culprit.  I run no LAN side FW's.  I have a FW on the edge of the network (router).  Do you need the FW running at all.

This is why it wise to test the system end to end first using wireshark.  

The reason it is taking along time is that you have added ping to the port scan with -PN.

---

### Post by verbitan on 2010-08-14
> **capscrew said:**
> Built in Firewall> I thought we had no firewall on the network.  This can be the culprit.
It always used to work fine with this firewall, so I presumed it would be ok. Anyway, after disabling it I still can't access via hostname. So as it stands now (for these tests) there is no firewall between the two computers.

The scan says ~ 10 mins remaining...I shall post the results when it has finished.

---

### Post by verbitan on 2010-08-14
> **verbitan said:**
> I shall post the results when it has finished.
```

Interesting ports on 192.168.1.103:
Not shown: 1970 closed ports
PORT      STATE         SERVICE
135/tcp   open          msrpc
139/tcp   open          netbios-ssn
445/tcp   open          microsoft-ds
2869/tcp  open          unknown
5357/tcp  open          unknown
49152/tcp open          unknown
49153/tcp open          unknown
49154/tcp open          unknown
49155/tcp open          unknown
49156/tcp open          unknown
68/udp    open|filtered dhcpc
137/udp   open|filtered netbios-ns
138/udp   open|filtered netbios-dgm
500/udp   open|filtered isakmp
1900/udp  open|filtered upnp
3702/udp  open|filtered unknown
4500/udp  open|filtered nat-t-ike
5353/udp  open|filtered zeroconf
5355/udp  open|filtered unknown
16938/udp open|filtered unknown
17533/udp open|filtered unknown
18234/udp open|filtered unknown
21649/udp open|filtered unknown
24594/udp open|filtered unknown
28122/udp open|filtered unknown
30656/udp open|filtered unknown
41774/udp open|filtered unknown
49171/udp open|filtered unknown
53589/udp open|filtered unknown
62699/udp open|filtered unknown

```

---

### Post by capscrew on 2010-08-14
```

```> **verbitan said:**
> ```

Interesting ports on 192.168.1.103:
Not shown: 1970 closed ports
PORT      STATE         SERVICE
135/tcp   open          msrpc
139/tcp   open          netbios-ssn
445/tcp   open          microsoft-ds
2869/tcp  open          unknown
5357/tcp  open          unknown
49152/tcp open          unknown
49153/tcp open          unknown
49154/tcp open          unknown
49155/tcp open          unknown
49156/tcp open          unknown
68/udp    open|filtered dhcpc
137/udp   open|filtered netbios-ns
138/udp   open|filtered netbios-dgm
...

```

How many computers are in this LAN network.  Can you list them like this:```
<IP_address>   <hostname>   <OS type>
```

Is the 'netbios name" of your Ubuntu host the same as it's hostname?

Edit:  Post the results of:```
smbtree
```

---

### Post by verbitan on 2010-08-15
> **capscrew said:**
> How many computers are in this LAN network.  Can you list them like this:```
<IP_address>   <hostname>   <OS type>
```
```

192.168.1.100        server          Ubuntu 10.04
192.168.1.101        office-pc        Windows XP
192.168.1.102        ps3            PS3OS?
192.168.1.103        nicks-laptop    Windows 7
192.168.1.104        nicks-iphon    iOS4.0.2
192.168.1.105        wii            WiiOS?
192.168.1.106        amber-laptop    Windows Vista

```> **capscrew said:**
> Is the 'netbios name" of your Ubuntu host the same as it's hostname?
Yes.
> **capscrew said:**
> Post the results of:```
smbtree
```
```

JAMES FAMILY
        \\SERVER                        Backup Server
                \\SERVER\IPC$                   IPC Service (Backup Server)
                \\SERVER\PDF Printer            Create a PDF and receive it via email.
                \\SERVER\Laser Printer          Samsung ML-2010
                \\SERVER\Public                 A public share.
                \\SERVER\MSDNAA                 Nicks MSDNAA Programs
                \\SERVER\Amber                  Ambers Backup
                \\SERVER\Dad                    Dads Backup
                \\SERVER\Mum                    Mums Backup
                \\SERVER\Nick                   Nicks Backup
                \\SERVER\Programs               Installers for programs
                \\SERVER\Photos                 Family Photos
                \\SERVER\Upload Music Here      Any music needing to go into the Music share.
                \\SERVER\Music                  Family Music


```

---

### Post by bilkay on 2010-08-15
> **Morbius1 said:**
> verbitan,

You stated that "samba says that it's running". I presume you did something like this:

**sudo service smbd status**

Did you make sure nmbd was running:

**sudo service nmbd status**

The old "samba" service combined the smbd and nmbd daemons into one service. Now that we're back to the good old days, each daemon needs to be started separately.
What's to do when you get "smbd: unrecognized service"?

You'd think this would be in a basic installation.

apt-cache search smbd returned: "samba4 - LanManager-like file server for Unix (version 4)"

Installed samba4 but still no smbd (or nmbd) service recognized!

I thought ubuntu was supposed to be user-friendly.

---

### Post by capscrew on 2010-08-15
> **verbitan said:**
> ```

192.168.1.100        server          Ubuntu 10.04
...

```
I think that if you add the hostname (server) to the /etc/hosts file you should be able to browse the Samba shares.

The format should be ```
192.168.1.100 server
```

There should be no reference to the hostname "server" with any IP address that starts with 127.

---

### Post by capscrew on 2010-08-15
> **bilkay said:**
> What's to do when you get "smbd: unrecognized service"?

The most direct way to check to see if the smbd and nmbd daemons are running is this:```
ps -ef | grep mbd
``` > 

You'd think this would be in a basic installation.

apt-cache search smbd returned: "samba4 - LanManager-like file server for Unix (version 4)"

Installed samba4 but still no smbd (or nmbd) service recognized!

I thought ubuntu was supposed to be user-friendly.
Sanba4 is still beta software.  Samba3 the stable version.

Please don't hijack the thread.  If you have a specific problem that needs addressing please start your own thread.

---

### Post by Morbius1 on 2010-08-15
I just noticed something:

> [COLOR=Blue]JAMES FAMILY[/COLOR]
        \\SERVER                        Backup Server
                \\SERVER\IPC$                   IPC Service (Backup Server)
                \\SERVER\PDF Printer            Create a PDF and receive The workgroup name has a space in it. I know there are rules about netbios name length and such but I don't remember the rules about workgroup names. Can you have a space in a workgroup name?

[COLOR=Blue]EDIT: Did a quick search and found this: [http://technet.microsoft.com/en-us/library/cc962757.aspx](http://technet.microsoft.com/en-us/library/cc962757.aspx)[/COLOR]
> A workgroup name can contain up to 15 characters, including letters,  numbers, and the following characters:    ! @ # $ % ^ & ( ) _ - ; : '  " , .  It cannot contain any spaces, and must begin with a letter or  number. 
The above was in reference to a Win2K Server but I don't think the rules world have changed since then.

---

### Post by capscrew on 2010-08-15
> **Morbius1 said:**
> I just noticed something:

The workgroup name has a space in it. I know there are rules about netbios name length and such but I don't remember the rules about workgroup names. Can you have a space in a workgroup name?

I believe you can have a space in the workgroup name.  You can see the browse list at:  /var/cache/samba/browse.dat

I'm not 100% sure of this, but if @**verbitan** can post this info we will see.  Personally I never have spaces in any names.
[COLOR="Green"]
Edit:  To further muddy the waters, it appears that the Samba team issued an INTERNET-DRAFT re: SMB URI that allows spaces.

See [**_here _**]("http://davenport.sourceforge.net/draft-crhertel-smb-url-07.txt")(buried deep within). [/COLOR]

---

### Post by capscrew on 2010-08-15
> **Morbius1 said:**
> I just noticed something:
...

[COLOR=Blue]EDIT: Did a quick search and found this: [http://technet.microsoft.com/en-us/library/cc962757.aspx](http://technet.microsoft.com/en-us/library/cc962757.aspx)[/COLOR]

The above was in reference to a Win2K Server but I don't think the rules world have changed since then.

But we are talking about Samba (smbd).  I don't think they are necessarily are identical.  Really, the only way to tell is by checking it.

I wonder how the OP created the workgroup (GUI???).

---

### Post by Morbius1 on 2010-08-15
> **capscrew said:**
> Really, the only way to tell is by checking it.


Changed the workgroup name on one linux machine to "WORK GROUP", restarted nmbd and smbd, and both a linux client and a Win2K client were able to access the server with the the space in the workgroup name.

Sorry for wasting everyone's time. I'm getting sloppy and lazy in my old age :(

---

### Post by capscrew on 2010-08-15
> **Morbius1 said:**
> Changed the workgroup name on one linux machine to "WORK GROUP", restarted nmbd and smbd, and both a linux client and a Win2K client were able to access the server with the the space in the workgroup name.

Sorry for wasting everyone's time. I'm getting sloppy and lazy in my old age :(

:D  I did the same thing.  I changed one of my laptops.  Interesting to to see the lag in the update of the browse list.

An interesting diversion **Morbius1**.

---

### Post by verbitan on 2010-08-15
> **capscrew said:**
> I think that if you add the hostname (server) to the /etc/hosts file you should be able to browse the Samba shares.

The format should be ```
192.168.1.100 server
```There should be no reference to the hostname "server" with any IP address that starts with 127.
My /etc/hosts file said,
```

127.0.0.1       localhost
127.0.1.1       server.home server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```It now says,
```

127.0.0.1          localhost
192.168.1.100   server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```It still doesn't work :(

I just find it so weird that I had this problem after the upgrade to 10.04, I gave up, reinstalled 10.04 and it worked fine, along with "JAMES FAMILY" etc. Then after two weeks alone, it broke. Seemingly for no reason. I just don't get it!

Edit: I've also tried,
```

127.0.0.1          localhost
192.168.1.100   server

```
and still no luck.

---

### Post by capscrew on 2010-08-15
Post the contents of:```

 /var/cache/samba/browse.dat
```

---

### Post by verbitan on 2010-08-15
> **capscrew said:**
> Post the contents of:```

 /var/cache/samba/browse.dat
```
```

"JAMES FAMILY"            c0001000 "SERVER"                      "JAMES FAMILY"
"SERVER"                  40859a03 "Backup Server"               "JAMES FAMILY"

```

---

### Post by capscrew on 2010-08-15
> **verbitan said:**
> ```

"JAMES FAMILY"            c0001000 "SERVER"                      "JAMES FAMILY"
"SERVER"                  40859a03 "Backup Server"               "JAMES FAMILY"

```

Well... The above is the browse list from the local Browse Master.

We have everything in place for successful browsing of the shares as far as Samba is concerned. 

Do you have "sharing" enabled on the Windows hosts? Are there firewalls on these hosts? How about installing Wireshark on Windows?

---

### Post by capscrew on 2010-08-15
A while back I asked: "*Is the 'netbios name" of your Ubuntu host the same as it's hostname?*.  I believe your answer was yes.  looking at your smb.conf file shows that this is not true. See below in red


> ```
# Browsing / Identification #
workgroup = JAMES FAMILY
[COLOR="Red"]**netbios name = Backup**[/COLOR]
server string = Server
```

I think you should change this to **server** as this is the hostname.  Weird things happen when the hostname does not match the NetBIOS name.  The Samba uses the hostname if no NetBIOS name is declared in the smb.conf file.  You can just comment it out for now.

---

### Post by verbitan on 2010-08-16
> **capscrew said:**
> Do you have "sharing" enabled on the Windows hosts? Are there firewalls on these hosts? How about installing Wireshark on Windows?
Yeah sharing is enabled on all the windows hosts. And yeah they all use the windows firewall. But as I said before, even with this disabled it doesn't work. All the windows machines can see each other fine. And they used to be able to see the server too, but hey ho.
I could install wireshark on windows, what should I do with it though?
> **capscrew said:**
> A while back I asked: "*Is the 'netbios name" of your Ubuntu host the same as it's hostname?*.  I believe your answer was yes.  looking at your smb.conf file shows that this is not true. See below in red

I think you should change this to **server** as this is the hostname.   Weird things happen when the hostname does not match the NetBIOS name.   The Samba uses the hostname if no NetBIOS name is declared in the  smb.conf file.  You can just comment it out for now.
Sorry for the confusion, that smb.conf was before I installed a fresh copy of Ubuntu 10.04 (when samba worked fine again), it is exactly the same now, apart from Backup is now server.

Ps. Sorry for the new delay in replying, I have just started a new job!

---

### Post by capscrew on 2010-08-16
> **verbitan said:**
> Yeah sharing is enabled on all the windows hosts. And yeah they all use the windows firewall. But as I said before, even with this disabled it doesn't work. All the windows machines can see each other fine. And they used to be able to see the server too, but hey ho.

I could install wireshark on windows, what should I do with it though?

I use wireshark to check end to end network connectivity.  At this point the only thing I see wrong is the lack of NetBIOS broadcasts.  This should be apparent when comparing the output of both hosts.  Wireshark should installed at both ends 

If you now have the hostname (*server *in your case) as the NetBIOS name, then you should be able to add the IP address hostname to this file on the Windows host.```
 C:\Windows\System32\drivers\hosts

```

That should make it possible to ping by hostname.  Then I would try to map a share with the Windows host.  This should be done while Wireshark is running.  You can filter out the non-essential protocols (i.e http)

As I am writing this I have Wireshark running and I can see my laptop running broadcast queries.  The laptop is kona and it is looking for RINCON.

```
364	62.854844	kona	192.168.1.255	NBNS	Name query NB RINCON<00>
```  

This is the description of this packet:
```
User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)
```

---

### Post by verbitan on 2010-08-17
On my laptop I get this...
```

16699    29.366414    192.168.1.103    192.168.1.255    NBNS    Name query NB SERVER<20>

User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)

```I am going to try and attempt this on the server now...

EDIT: Ok, I have it running on the server (good old X Win)...What am I looking for? :)
EDIT2: The server shows this...So I don't understand why it didn't respond??

```

4494      27.03   192.168.1.103      192.168.1.255    NBNS     Name query NB SERVER<20>

User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)

```

---

### Post by capscrew on 2010-08-17
> **verbitan said:**
> On my laptop I get this...
```

16699    29.366414    192.168.1.103    192.168.1.255    NBNS    Name query NB SERVER<20>

User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)

```I am going to try and attempt this on the server now...

EDIT: Ok, I have it running on the server (good old X Win)...What am I looking for? :)
EDIT2: The server shows this...So I don't understand why it didn't respond??

```



4494      27.03   192.168.1.103      192.168.1.255    NBNS     Name query NB SERVER<20>

User Datagram Protocol, Src Port: netbios-ns (137), Dst Port: netbios-ns (137)

```

Have you enabled "capture options" = name resolution for MAC,  network, and transport?

Notice how my hosts have their network names resolved.  The source on yours is 192.168.1.103 while mine is kona.

Have you tried this on the client?

---

### Post by verbitan on 2010-08-18
> **capscrew said:**
> Have you enabled "capture options" = name resolution for MAC,  network, and transport? ... Have you tried this on the client?
Yup! [IMG]http://imgur.com/8Qrnz.png[/IMG]

---

### Post by capscrew on 2010-08-18
What else have you done to diagnose your problem?

I can see the Browse Master being setup on my network.  See the attached JPEG

You will need to find the appropriate filter under "Expressions" >> expand SMB and look for smb.cmd.

I would read up on how browsing works.  See: [**_here_**]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html").

---

### Post by verbitan on 2010-08-21
I have never even heard of a browse master :oops: So I shall have to look into that...

As far as diagnosis goes, I have done everything in this thread...I have removed and purged samba, reinstalled and tried with the default smb.conf, still no luck!

---

### Post by verbitan on 2010-08-21
Also, I have played around with wireshark...

The server CAN see the broadcast request for server, but it won't respond. However when I access it via the IP, it connects fine. And you can see it doing so. I get this feeling it is DNS related, but I don't understand what it could be.
The server does have BIND DNS installed, but that basically came as default, I have never configured it, and it always used to work with in there, so I can't see that causing the problem. I guess i could try removing and purging it.

EDIT: There was recently an update for samba, so I installed that, and used the smb.conf it provided. Compared it to mine, and found a few things off, ie I had "wins support = true" rather than "wins support = yes". I also found a new option (to me) called "dns proxy" which I have set to yes, hoping that nmbd could find the NetBIOS name through DNS. I have also now defined "name resolve order = wins lmhosts hosts bcast". Interestingly, the fresh smb.conf **didn't** have "netbios name = whatever" in it?

Either way, none of this still works! Here is my smb.conf...

```

[global]
# Browsing / Identification #    
    # Change this to the workgroup/NT-domain name your Samba server will part of
        workgroup = JAMES FAMILY
    
    # server string is the equivalent of the NT Description field        
    server string = %h server (Samba, Ubuntu)
    
    # Windows Internet Name Serving Support Section:
    # WINS Support - Tells the NMBD component of Samba to enable its WINS Server
    wins support = yes    
    
    # This will enable nmbd to search for NetBIOS names through DNS.    
    dns proxy = yes

    # What naming service and in what order should we use to resolve host names
    # to IP addresses
    name resolve order = wins lmhosts hosts bcast

    follow symlinks = true
    wide links = yes
    unix extensions = no
    netbios name = Server
    *local master = yes*[I]
  preferred master = yes[/I]
        
# Authentication #
        security = user
        encrypt passwords = true
        map to guest = bad user
        guest account = nobody

        passdb backend = tdbsam
        obey pam restrictions = yes
        unix password sync = yes
        pam password change = yes
        invalid users = root

        socket options = TCP_NODELAY
        preferred master = yes

    # For Unix password sync to work on a Debian GNU/Linux system, the following
    # parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
    # sending the correct chat script for the passwd program in Debian Sarge).
       passwd program = /usr/bin/passwd %u
       passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# Printing
    load printers = yes
    printing = cups
    printcap name = cups

# Public shares
[Music]
    comment = Family Music
    path = /media/RAID/Media/Music
    public = no
    browsable = yes
    read only = no
    writeable = yes
    create mask = 0777
    directory mask = 0777
    valid users = @sambashare
    write list = verbitan

[Upload Music Here]
    comment = Any music needing to go into the Music share.
    path = /media/RAID/Media/PendingMusic
    public = no
    browsable = yes
    read only = no
    writeable = yes
    create mask = 0777
    directory mask = 0777
    valid users = @sambashare
    write list = @sambashare

[Photos]
    comment = Family Photos
    path = /media/RAID/Media/Photos
    public = no
    browsable = yes
    read only = no
    writeable = yes
    create mask = 0777
    directory mask = 0777
    valid users = @sambashare
    write list = @sambashare

[Programs]
    comment = Installers for programs
    path = /media/RAID/Software/General
    public = no
    browsable = yes
    read only = no
    writeable = yes
    create mask = 0777
    directory mask = 0777
    valid users = @sambashare
    write list = @sambashare

# private shares
[Nick]
    comment = Nicks Backup
    path = /media/RAID/Personal/Nick
    public = no
    browsable = yes
    read only = no
    writeable = yes
    create mask = 0777
    directory mask = 0777
    valid users = verbitan
    write list = verbitan

[Mum]
    comment = Mums Backup
    path = /media/RAID/Personal/Mum
    public = no
    browsable = yes
    read only = no
    writeable = yes
    create mask = 0777
    directory mask = 0777
    valid users = supermum
    write list = supermum

[Dad]
    comment = Dads Backup
    path = /media/RAID/Personal/Dad
    public = no
    browsable = yes
    read only = no
    writeable = yes
    create mask = 0777
    directory mask = 0777
    valid users = gerry
    write list = gerry

[Amber]
    writeable = yes
    writable = yes
    path = /media/RAID/Personal/Amber
    write list = ambeth
    create mask = 0777
    comment = Ambers Backup
    directory mask = 0777
    valid users = ambeth
    public = no
    browsable = yes

[MSDNAA]
    comment = Nicks MSDNAA Programs
    path = /media/RAID/Software/MSDNAA
    public = no
    browsable = yes
    read only = no
    writeable = yes
    create mask = 0777
    directory mask = 0777
    valid users = verbitan
    write list = verbitan
[Public]
    comment = A public share.
    path = /media/RAID/Public
    public = no
    browsable = yes
    read only = no
    writeable = yes
    create mask = 0777
    directory mask = 0777
    valid users = @sambashare nobody
    write list = @sambashare nodoby

[Laser Printer]
    printer = ML-2010
    comment = Samsung ML-2010
    printable = yes
    path = /var/spool/samba
        guest ok = yes
        writable = no
    create mode = 0700
    browseable = yes
    printer admin = @sambashare guest

[PDF Printer]
           comment = Create a PDF and receive it via email.
           printing = LPRNG
           path = /var/spool/samba
           guest ok = no
    printable = yes
    browsable = yes
    printer admin = @sambashare
    # Parameters below: spool file name, job name, user name, user home dir
           print command = /usr/local/bin/printpdf %s %u %H "%J"

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
       comment = Printer Drivers
       path = /var/lib/samba/printers
       browseable = yes
       read only = yes
       guest ok = yes

```

---

### Post by Morbius1 on 2010-08-21
Man this has become unbelievably  complicated. You've changed the original smb.conf you've posted and have shared completely different directories than you did originally.

Let's take [Photos] for example:
Old path:
> [Photos]
        comment = Family Photos
        path = /media/NAS DRIVE/Photos
        New path:
> [Photos]
    comment = Family Photos
    path = /media/RAID/Media/Photos
    The only thing I'd like to point out here is that every way along that path the "execute" bit need to turned on or else the remote user will never get to the target. If you created the paths the default permissions should be set correctly but if you've modified it it may not work. For example, if you do an "ls -dl /media/RAID", and a "ls -dl /media/RAID/Media" you should get something like this:
> drwxr-xr-x If instead you get something like this:
> drwx------Then from the remote users perspective the "Photos" directory ( /media/RAID/Media/Photos ) doesn't exist.

I don't want to interfere with capscrew's analysis of all this but I'd also like to point out two other additions that he knows more about than I do:
> name resolve order = wins lmhosts hosts bcast
wins support = Yes
Have you set your Ubuntu machine to be a WINS server and have you done the winbind - nsswitch.conf thing. Having a WINS server is a legitimate method as long as you have fixed ip addresses but you have to modify all the clients on your network to make it work. As far as the winbind thing, capscrew may get ... well let's just say he will give you his opinion of that in no uncertain terms ;)

---

### Post by verbitan on 2010-08-21
> **Morbius1 said:**
> Man this has become unbelievably  complicated. You've changed the original smb.conf you've posted and have shared completely different directories than you did originally.

Let's take [Photos] for example:
Old path:
New path:
The only thing I'd like to point out here is that every way along that path the "execute" bit need to turned on or else the remote user will never get to the target. If you created the paths the default permissions should be set correctly but if you've modified it it may not work. For example, if you do an "ls -dl /media/RAID", and a "ls -dl /media/RAID/Media" you should get something like this:
If instead you get something like this:
Then from the remote users perspective the "Photos" directory ( /media/RAID/Media/Photos ) doesn't exist.
All this is irrelevant, the directory access/location and all that jazz works fine. I just have to access it with \\192.168.1.100 rather than \\hostname.

> **Morbius1 said:**
> I don't want to interfere with capscrew's analysis of all this but I'd  also like to point out two other additions that he knows more about than  I do:
Have you set your Ubuntu machine to be a WINS server and have you done  the winbind - nsswitch.conf thing. Having a WINS server is a legitimate  method as long as you have fixed ip addresses but you have to modify all  the clients on your network to make it work. As far as the winbind  thing, capscrew may get ... well let's just say he will give you his  opinion of that in no uncertain terms :wink:
Ha right ok...I figured from the samba web pages that I needed to set the Ubuntu machine to be a WINS server in order for it to work. I haven't touched nsswitch.conf, should I have? :roll:

---

### Post by capscrew on 2010-08-21
> **Morbius1]  
Man this has become unbelievably complicated...[/QUOTE]

I agree completely.  It is getting to the point where I am reluctant to mention how things work or ideas on how to diagnose the problem.  The information always seems to be misinterpreted and then misapplied.    



[QUOTE=verbitan said:**
> ...
Ha right ok...I figured from the samba web pages that I needed to set the Ubuntu machine to be a WINS server in order for it to work. I haven't touched nsswitch.conf, should I have? :roll:

I really don't understand why you would say that you *need * a WINS server.  You absolutely do not need a WINS server to resolve NetBIOS names.  I do not run a WINS server in my network.  It works perfectly fine.  The the section on browsing I refered you to certainly doesn't state that.  

As a matter of fact, almost nothing is needed in a basic smb.conf file for Samba to function correctly.  When there is no directive the DEFAULT configuration applies.  The majority of time the default configuration is the most logical for most users.  All of the modifications you have made only take you farther away fromsuccessful implementation of Samba sharing.

There is no need to modify anthing in the OS system other than file permissions.  Do not modify the /etc/nsswitch.conf file or any other systems files.

A few points you should know.  There is no need to reinstall Samba when you want to start over again.  Samba is configured completely by the smb.conf file.  There is an additional place that *usershares *are configured, but that is not relevant to this discussion.  If you decide to start over just replace the smb.conf file with the original copy.  You did make a backup copy. right?

I recommend that you start over.  If this means that you have to roll back things in the OS to achieve that end then do it.  I feel you turn off ALL LAN side firewalls.  You should only need a firewall on the edge of the LAN (i.e. at the router).  You should have connectivity between all hosts BEFORE you start configuring Samba. 

With an original copy of the smb.conf file in place, I would follow (generally) [**_this tutorial_**]("http://www.samba.org/samba/docs/man/Samba-Guide/").  The tutorial has most of what we have discussed and starts with a very simple smb.conf file.  There are references to RedHat but you should be able to follow it (but not blindly).

---

### Post by verbitan on 2010-08-22
> **capscrew said:**
> I agree completely.  It is getting to the point where I am reluctant to mention how things work or ideas on how to diagnose the problem.  The information always seems to be misinterpreted and then misapplied.
Sorry :( I don't mean to be confusing things. I think the reason I'm getting frustrated is because I had this problem before, instantly after upgrading to Ubuntu 10.04, without making any other changes to the system, just the command line based upgrade.
I couldn't diagnose the problem (even with the initial help of this thread) so I installed a fresh copy of 10.04, presuming that something had got corrupt! And hey, it seemed that it had. I just copied in my smb.conf, and all was fine (that was when i changed the file paths).
Then, for seemingly no reason, it stopped working. I absolutely didn't change my smb.conf between when it was working and when it died. In fact I am 99% sure I didn't change anything as I was on holiday and nobody was at home. It was working before I went away, everything was shut down for two weeks, and then when I returned and booted it all back up, suddenly it didn't work!
I know I have mentioned all this before, but I hope you can understand my frustrations. I really do appreciate all your help and I'm trying to do everything you tell me.

> **capscrew said:**
> A few points you should know.  There is no need to reinstall Samba when you want to start over again.  Samba is configured completely by the smb.conf file.  There is an additional place that *usershares *are configured, but that is not relevant to this discussion.  If you decide to start over just replace the smb.conf file with the original copy.  You did make a backup copy. right?

I recommend that you start over.  If this means that you have to roll back things in the OS to achieve that end then do it.  I feel you turn off ALL LAN side firewalls.  You should only need a firewall on the edge of the LAN (i.e. at the router).  You should have connectivity between all hosts BEFORE you start configuring Samba. 

With an original copy of the smb.conf file in place, I would follow (generally) [**_this tutorial_**]("http://www.samba.org/samba/docs/man/Samba-Guide/").  The tutorial has most of what we have discussed and starts with a very simple smb.conf file.  There are references to RedHat but you should be able to follow it (but not blindly).
Again, I had connectivity between all the hosts to start with. I now don't (ie they all cant see the server via it's hostname [but can via its IP]). So now, even with the default supplied smb.conf, and all firewalls disabled, nothing changes.

---

### Post by capscrew on 2010-08-22
> **verbitan said:**
>  ...
Again, I had connectivity between all the hosts to start with. I now don't (ie they all cant see the server via it's hostname [but can via its IP]). So now, even with the default supplied smb.conf, and all firewalls disabled, nothing changes.

TCP/IP connectivity is not NetBIOS connectivity.

Are you following the tutorial?

---

### Post by kalyp on 2011-01-10
I don't know if anybody still has that problem, but in case, this could be useful.
I ran into the same problem (hostname not resolved anymore) right after installing samba (although I didn't realize it was connected). What seemed to happen in that the DNS entry for my computer changed and became associated with the wireless network in one case, ipv6 in the other case (2 computers had the problem). The network admin deleted the DNS entry, I disabled ipv6 and the wireless (only the wired connection is on the network) and that solved the problem (minus reinstalling samba and samba-common-bin).
Cf [http://ubuntuforums.org/showthread.php?p=10341434#post10341434](http://ubuntuforums.org/showthread.php?p=10341434#post10341434)

---

