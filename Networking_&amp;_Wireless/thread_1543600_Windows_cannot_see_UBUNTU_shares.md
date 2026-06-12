---
title: "Windows cannot see UBUNTU shares"
date: 2010-08-01
forum: Networking &amp; Wireless
---

### Post by fcchristian on 2010-08-01
Good morning all;

I've been fighting a problem for about a month now... Allow me to extend accolades to all who have worked on the UBUNTU project. This is my fifth pass at trying Unix and THIS one WORKS!  Okay, mostly or I would not be posting...

Desired Objective: Simply share a printer in a small, secure home network spread over 5 or 6 machines running mostly windows (98 through Win7) but using the UBUNTU box as the host for the printer.

The network has basic connectivity. I have no problem pinging any box from any box. Or surfing from any box. 

From UBUNTU box, can see and browse Windows Workgroup no problem.

Windows machines see the announcement of UBUNPRIN but cannot connect. Cannot seem to authenticate. I'm thinking that I have the share set up with NO security.

security = SHARE

And

map to guest = Bad User

Adding some terminal output that may be helpful and the smb.conf file...

christian@christian-desktop:/var/spool$ ls -l
total 24
drwxrwxrwt 2 root root 4096 2010-04-09 11:27 samba

christian@christian-desktop:~$ smbclient -L christian-desktop
Enter christian's password: 
Connection to christian-desktop failed (Error NT_STATUS_CONNECTION_REFUSED)

christian@christian-desktop:~$ smbclient -L UBUNPRIN
Enter christian's password: 
Connection to UBUNPRIN failed (Error NT_STATUS_CONNECTION_REFUSED)


christian@christian-desktop:~$ testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[tmp]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    netbios name = UBUNPRIN
    server string = %h server (Samba, Ubuntu)
    interfaces = 127.0.0.0/8, eth0
    bind interfaces only = Yes
    security = SHARE
    map to guest = Bad User
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    printcap name = cups
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    guest ok = Yes
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[tmp]
    comment = temporary files
    path = /tm


Clip from log.nmbd:

[2010/07/22 06:06:31,  0] nmbd/nmbd.c:854(main)
  nmbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/07/22 06:27:38,  0] nmbd/nmbd_packets.c:1175(process_lanman_packet)
  process_lanman_packet: On subnet 192.168.1.103 ignoring browse packet command code 21506 from TheRealLaptop<01> IP 192.168.1.101 to WORKGROUP<00>

---

### Post by marc.verwerft on 2010-08-01
Hello,

I can understand the frustration - been there, done that. I can only give you some pointers and ideas, you'll have to work out the rest since SAMBA of course also relies on how the domain has been setup etc.

Things to take a better look at (or explain):
- your log file shows two logins that fail. Is that the basic problem?
- have you tried sharing files between the ubuntu box and the windwos PC's? Printing is an 'extra' step/difficulty to pinpoint the problem
- try in small incremental steps: set maximum logging for smbd/nmbd, get a working example from the tutorials, share files, add security and finally share a printer. 

links:
- [http://www.debian-administration.org/article/Using_Samba_on_Debian_Linux/print](http://www.debian-administration.org/article/Using_Samba_on_Debian_Linux/print)
- [http://devel.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2553683](http://devel.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2553683)

Regards,

Marc

---

### Post by sikander3786 on 2010-08-01
Hi.
Under global settings
security = user is always a good idea.

Is firewall enabled on Ubuntu?

On windows machine go to your browser and enter
http://<hostname>:631/printers/<printername>

Replace <hostname> with Ubuntu Box name and <printername> with whatever your printer name is. What does it say?

---

### Post by fcchristian on 2010-08-01
> **marc.verwerft said:**
> Hello,

I can understand the frustration - been there, done that. I can only give you some pointers and ideas, you'll have to work out the rest since SAMBA of course also relies on how the domain has been setup etc.

Things to take a better look at (or explain):
- your log file shows two logins that fail. Is that the basic problem?
- have you tried sharing files between the ubuntu box and the windwos PC's? Printing is an 'extra' step/difficulty to pinpoint the problem
- try in small incremental steps: set maximum logging for smbd/nmbd, get a working example from the tutorials, share files, add security and finally share a printer. 

links:
- [http://www.debian-administration.org/article/Using_Samba_on_Debian_Linux/print](http://www.debian-administration.org/article/Using_Samba_on_Debian_Linux/print)
- [http://devel.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2553683](http://devel.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2553683)

Regards,

Marc

Marc, I've started the /tmp share to test exactly that and eliminate the added layer of the CUPS... on the other hand the CUPS runs fine and prints easily from the UBUNTU BOX.

It almost has to be an authentication issue but I'm stumped since, as I understand it, Security = Share means no authentication.  Please note that there is a guest user account established with rw on the SAMBA spooling directory..

Thx FCChristian

---

### Post by fcchristian on 2010-08-01
> **sikander3786 said:**
> Hi.
Under global settings
security = user is always a good idea.

Is firewall enabled on Ubuntu?

On windows machine go to your browser and enter
http://<hostname>:631/printers/<printername>

Replace <hostname> with Ubuntu Box name and <printername> with whatever your printer name is. What does it say?

Hello Sikander,

There is no firewall that I can find...

When I try: [http://christian-desktop:631/HL-2140-series](http://christian-desktop:631/HL-2140-series) simply replies that Internet Exploder cannot display this page.... 

When I try: [http://UBUNPRIN:631/HL-2140-series](http://UBUNPRIN:631/HL-2140-series) simply replies that Internet Exploder cannot display this page.... 

trying to install the printer share using the IP address and port call also fails....

---

### Post by Morbius1 on 2010-08-01
You have no shares defined unless you used Nautilus to set up shares ( in which case they wouldn't show up in smb.conf ).

That means you only have one shared resource and you've made it invisible:
> [printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    guest ok = Yes
    printable = Yes
    [COLOR=Blue]browseable = No
    browsable = No[/COLOR]


---

### Post by Morbius1 on 2010-08-01
(1) You do have a share defined, didn't see that at the end :
> [tmp]
    comment = temporary files
    path = /tm
That share is expecting authentication even if it's only a password.

(2) I'd follow sikander3786's advice and set your security level to USER. Nobody living remembers all the rules in share level security. 

(3) I'm probably misinterpreting this error message:
> nmbd/nmbd_packets.c:1175(process_lanman_packet)
  process_lanman_packet: On subnet 192.168.1.103 ignoring browse packet  command code 21506 from TheRealLaptop<01> IP 192.168.1.101 to  WORKGROUP<00>     Is the request coming from a Win98 machine by any chance?

---

### Post by fcchristian on 2010-08-01
> **Morbius1 said:**
> You have no shares defined unless you used Nautilus to set up shares ( in which case they wouldn't show up in smb.conf ).

That means you only have one shared resource and you've made it invisible:


Hello Moribus,

Check this out, clip from the smb.conf, not the output of testparms

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

And i completely overlooked that testparm comes back with browesable = no

Can't find a browseable = no without a leading semicolon in the smb.conf file so far.

Thanks

FCChristain

---

### Post by fcchristian on 2010-08-01
> **Morbius1 said:**
> (1) You do have a share defined, didn't see that at the end :
That share is expecting authentication even if it's only a password.

(2) I'd follow sikander3786's advice and set your security level to USER. Nobody living remembers all the rules in share level security. 

(3) I'm probably misinterpreting this error message:
Is the request coming from a Win98 machine by any chance?


I can set security to user... I thought that setting it to share with guest  = bad user essentially removed all authentication...

#3 came from a Vista machine...

---

### Post by Morbius1 on 2010-08-01
If you go into smb.conf itself and look at the [printers] section you'll see this:
> [printers]
      comment = All Printers
;    browseable = no
      path = /var/spool/samba
      printable = yes
      guest ok = yes
;    guest ok = no
;    read only = yes
      create mask = 0700I'' admit it's subtle but unlike a "#" which is clearly a comment, a ";" means it's the default and so is not expressed explicitly but will show up in a testparm. Remove the ";" and change no to yes and restart samba:
```
sudo service smbd restart
```

---

### Post by fcchristian on 2010-08-01
> **Morbius1 said:**
> If you go into smb.conf itself and look at the [printers] section you'll see this:
I'' admit it's subtle but unlike a "#" which is clearly a comment, a ";" means it's the default and so is not expressed explicitly but will show up in a testparm. Remove the ";" and change no to yes and restart samba:
```
sudo service smbd restart
```

I completely missed the difference... but as soon as you pointed it out I remember that it is clearly stated on the full smb.conf how that works... changed as suggested and restarted smb....

We are making progress, 'cause now the Vista box is looking for a username and password to access whatever is shared on the UBUNPRIN machine.

Tried both the Unix username/password combo and the Windows username and combo, same name different passwords. 

Several weeks ago think I put the user name and password combo in the samba suite with the smbpasswd command.  (Can I easily see the TIB file?? And see what and who is in it???)

In passing, really don't want to set up accounts for all the users on the Ubuntu box... would like to use the guest as default...

Thx.

FCChristian

---

### Post by fcchristian on 2010-08-01
Things are getting less clear

I searched the smb.conf file for browseable and changed all three instances to yes...

ran test parm and it reports browseable = no...

am posting both for your eyes to quickly scan...

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
   netbios name = UBUNPRIN    
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
   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
   bind interfaces only = yes



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
   ;encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

  ;obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   ;unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   ;passwd program = /usr/bin/passwd %u
   ;passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   ;pam password change = yes

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
   load printers = yes

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
;[homes]
;   comment = Home Directories
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
    guest ok = yes
    browseable = yes
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

[tmp]
comment = temporary files
path = /tmp
read only = yes

AND HERE IS THE TESTPARM OF THE SAME FILE

christian@christian-desktop:~$ testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[tmp]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    netbios name = UBUNPRIN
    server string = %h server (Samba, Ubuntu)
    interfaces = 127.0.0.0/8, eth0
    bind interfaces only = Yes
    map to guest = Bad User
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    printcap name = cups
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
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
    guest ok = No

[tmp]
    comment = temporary files
    path = /tmp

---

### Post by Morbius1 on 2010-08-01
If you're talking about this share:
> [tmp]
    comment = temporary files
    path = /tm
Just add a "guest ok = yes" so that it looks like this:
> [tmp]
     comment = temporary files
     path = /tm
[COLOR=Blue]guest ok = yes[/COLOR]And restart samba again.

Are you saying it's requesting authentication to access the printer?

---

### Post by Morbius1 on 2010-08-01
You only needed to change the "; browseable = no" in the printers section. Each section of smb.conf indicated by a [  ] can run as a complete subsytem by itself. Do you remember where else you changed it?

[COLOR=Blue]EDIT: Wait, After you made the changes did you:[/COLOR]
(1) Save the file
(2) Restart samba
(3) And then ran testparm

---

### Post by fcchristian on 2010-08-01
Moribus, thanks for hanging in with me...

From the Vista box, as soon as I click the icon for UBUNPRIN; a username and password box pops up.

also here is a current clip from smb.conf

[tmp]
comment = temporary files
path = /tmp
read only = yes
guest ok = yes

saved and smb restarted

ran testparm again... Please note last section... ????? Where is the guest ok???

christian@christian-desktop:~$ testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[tmp]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    netbios name = UBUNPRIN
    server string = %h server (Samba, Ubuntu)
    interfaces = 127.0.0.0/8, eth0
    bind interfaces only = Yes
    map to guest = Bad User
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    printcap name = cups
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
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
    guest ok = No

[tmp]
    comment = temporary files
    path = /tmp

---

### Post by fcchristian on 2010-08-01
Yes I did the save and restart... Double did it in case I forgot!!!

Does the Global guest ok = yes impact all the sections???

---

### Post by fcchristian on 2010-08-01
Only appears in (and was changed in)

[homes]
[profiles]
[printers]
[print$]

Can easily change back if and when home directories for users becomes an issue... first want to share the printer.

Thx Christian

---

### Post by Morbius1 on 2010-08-01
>   ran testparm again... Please note last section... ????? Where is the guest ok???testparm reads AND interprets the smb.conf file - it's basically a simulator to show you how it would read your file in production. You have a guest ok = yes in an earlier place in the file so it's redundant and testparm is ignoring it. 

>  From the Vista box, as soon as I click the icon for UBUNPRIN; a username and password box pops up.That's a different situation. You by any chance using the same username on Vista that you're using on the Ubuntu box. AND did you create a samba user password for that user? For some odd reason all the HowTo's state that MUST be done but it just gets in the way. If you've done that make sure the password matches exactly the login password of the Vista machine.

---

### Post by fcchristian on 2010-08-01
Some days....

First, Just printed a test page to the printer that I have been trying to share for a month...

Second, Windows Vista IN THE PRINTER DIALOG BOX H'line

"HL-2140-series on UBUNPRIN Access denied, unable to connect"

So just to make sure opened a simple txt file on the Vista box and printed to the shared printer...

Still not sure what is going on... maybe the guest ok = yes

BTW can see the tmp file folder from the Vista box but I did that as a diagnostic only and will remove from the SMB.CONF file... simply wanted to share the printer.

Next is to see iffen I can get it from the Win98 Box, the Win7 box and the WinXP box...

Moribus, I have read your replies in many many threads over the last month... thank you for your patience and persistence....

---

### Post by fcchristian on 2010-08-01
Moribus,

FYI
Have connected the Win7 box to printer....

Working on Win 98...

Here is interesting part... Vista demanded Authentication.  Win 7 did not.

In passing, about 30 minutes ago I made sure that the smbpasswd had my user name (logged in on the Vista box. ) by running the smbpasswd command as appropriate...

Will keep this thread updated for others in this same pickle...

And when I figure out the exact issue (suspect both the username/password combination ('cause same user name on UBUNTU and Windows Vista) and guest ok = yes being applied globally...

Again, allow me to salute your help and dedication to the group of newbies that cannot fathom the documentation.  Moribus, you ROCK!!!

Thx 

FC Christian

---

### Post by Morbius1 on 2010-08-01
Here's my guess as to what's happening.

First: No one should be asking anyone else for a username and password because every shared resource on your Linux server is set to allow guest access.

Second, There's only one situation that I can think of at this moment that would cause Vista to ask for authentication to a guest share and not Win7: The Vista login username and the Linux login username match AND the Linux login user created an smbpasswd for himself on the Linux machine. Another indication that this is what may be happening is that the authentication prompt happens at the machine name level and not the share level. That ain't supposed to happen.

When a windows user browses network shares, windows will actually pass his login username and password in the greeting. Now if you use the same username on both the Windows client and the Samba server and you created an smbpasswd for that user it will prompt for a username and password ( even if all you have are guest shares ) unless the passwords are exactly alike. 

The answer is never create an smbpasswd for anyone if all you have is guest shares OR use a completely different set of usernames for network access only .

At this point you may be in too deep so just make absolutely sure that the smbpasswd and the vista login password matches exactly.

---

### Post by fcchristian on 2010-08-01
My Friend,

I am sure that the passwords match... but FYI subsequent login's to the shared printer no longer require username and password.   I will be rebooting the entire network and starting from scratch.  I will in any case advise you of further issues. Again, thank you for your patience and working with us newbies as we struggle to understand the simple yet complex relationships within UBUNTU.  

My son, who is an educated and experienced network engineer, passed on this issue once we had cups up and part of samba.  I have 30 years with PC's and most operating systems. I get how it grew.  

The details escape me!

Again, thank you for your time and patience!  

As I sort through the last few issues, I will keep you in the loop.

FCChristian

---

### Post by JKyleOKC on 2010-08-04
> **Morbius1 said:**
> Here's my guess as to what's happening.

First: No one should be asking anyone else for a username and password because every shared resource on your Linux server is set to allow guest access.

Second, There's only one situation that I can think of at this moment that would cause Vista to ask for authentication to a guest share and not Win7: The Vista login username and the Linux login username match AND the Linux login user created an smbpasswd for himself on the Linux machine. Another indication that this is what may be happening is that the authentication prompt happens at the machine name level and not the share level. That ain't supposed to happen.
I'm having a quite similar situation, trying to print across my LAN from one Lucid box to another. I tried to print one page of this thread, and here's what happened (see attached screen shot). I tried every possible password but none was accepted; finally cancelled the job.

Note that Windows is not involved here at all, although I do have samba installed as a server on the machine where the printer is connected, to permit sharing the printer across my LAN. And I've been able to access a shared directory with no such problem, so it must be something in the way CUPS and samba deal with each other...

However, additional searching took me to another thread that suggested not using SAMBA at all for the connection, but rather going direct to CUPS on the other machine -- and that worked!

---

### Post by Morbius1 on 2010-08-04
JKyleOKC, the real problem is that you're using samba to connect a printer between two linux boxes. My preference is to connect to it directly:

Administration > Printing > New > Other  > In the "Enter URI" box enter one of the following:[FONT=monospace]
[/FONT]```
ipp://MACHINE_NAME:631/printers/Linux-Printer-Name
ipp://192.168.0.100:631/printers/Linux-Printer-Name
```By ip address seems to work the best.

But if using samba to do this you need to make a change to the [printers] section of smb.conf. Find the following line in that section:
> [printers]
   comment = All Printers
   browseable = No
   path = /var/spool/samba
   printable = yes
   [COLOR=Blue]**guest ok = no**[/COLOR]
;  read only = yes
   create mask = 0700And change no to yes, then restart samba

[COLOR=Blue]EDIT: Sorry about that. It took me so long to write this I didn't notice you edited your post.[/COLOR]

---

### Post by MartinusEx on 2010-08-05
Folks,

i had this very problem.
Tried to solve the smb configuration as per this thread.
That didn't work.
My history:
First I edited the smb.conf manually
Then i used GADMIN SAMBA Config Editor GUI
This program added A LOT OF entries to the smb.conf.

At last I suspected this lot of entries to be somewhat irritable.
I changed back to the very original smb.conf that comes with the installation. (Had a backup :guitar:)

Only changed the absolute necessary entries and crosschecked with this thread.

And Thor be praised it works.
My WinXP  Box (there still are some minor necessities to run a Windows box :( )  detected the printers and installation worked.
And  printing is possible .. 

So my advice is..
switch back to the original smb.conf
only apply small necessary changes

then the other advices in your thread might work as well

cheers

Martin

---

### Post by JKyleOKC on 2010-08-05
> **Morbius1 said:**
> [COLOR=Blue]EDIT: Sorry about that. It took me so long to write this I didn't notice you edited your post.[/COLOR]No need to apologize! I had been using the Samba method for several years, with 8.04, so figured that it should still work with 10.04. The direct CUPS-to-CUPS way is, of course, much simpler and should continue to work indefinitely. Now if I could just solve some of the other upgrading problems as easily ... But that's for other threads.

Thanks for the suggestion. I always appreciate the help I get here!

---

