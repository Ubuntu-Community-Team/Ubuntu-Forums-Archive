---
title: "Cannot file share! =("
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by bcraig24 on 2010-10-27
Ok Ive tried soooo many tutorials and been through sooo many forums but I cant get my file sharing to work from any computer. 

Ive got a 
- Ubuntu 10.04(64bit) desktop to use as a home web/file server, wired.(BEN-SERVER)
- Vista(32bit) laptop, wireless.(BEN-LAPTOP)
- Windows 7(64bit) desktop, wireless.(BEN-LAVIE)

- EchoLife HG520s ADSL2 wireless modem.

At the moment...

In Ubuntu network browswer it only displays BEN-LAPTOP.
But trying to browse BEN-LAPTOP I get "Unable to mount location Failed to retrieve share list from server".

Vista only displays BEN-LAVIE and browsing gives me "Windows cannot access \\BEN-LAVIE"

And Windows 7 doesn't display any.

Previously I was able to share between Windows 7 and Ubuntu but I don't know what I did but it stopped working. I have since reinstalled Ubuntu and tried again from scratch but no luck =(

I hope thats enough info for people to drop me some advice?
Thanks in advance.

Ben

---

### Post by johnnytm on 2010-10-27
Are you using samba? is ufw enabled? too many places to start. gonna hafta be a little more specific

---

### Post by bcraig24 on 2010-10-27
Sorry I am fairly newb with all this.

I am using samba. I only just found out what UFW was by Google and just tried to install it and it says I have the latest version already.

What other info do I need to give?

---

### Post by johnnytm on 2010-10-27
check the output of ```
sudo ufw status
```
if it says ufw enabled then try ```
sudo ufw disable
``` and then try to access your shares again

---

### Post by bcraig24 on 2010-10-27
Status says inactive.
Assuming that mean I don't need to disable it but I tried the command anyway. Sharing still not wokring.

---

### Post by bcraig24 on 2010-10-28
Another weird thing that I haven't read about before..

I installed samba with apt-get install samba but when I use commands like samba restart it says samba is not installed try use apt-get install samba4...

---

### Post by johnnytm on 2010-10-28
I hope you didn't install samba 4. Its way too complicated. do u have a samba gui installed? what's the output of ```
testparm -s
```

---

### Post by bcraig24 on 2010-10-28
I did try installing samba4 thinking that it probably would make things worse but it didn't help and I have reinstalled Ubuntu since.

output of testparm -s

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Processing section "[Downloads]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = HOMESERVER
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

[share]
    comment = Ubuntu Filer Server Share
    path = /srv/samba/share
    read only = No
    create mask = 0755
    guest ok = Yes

[Downloads]
    path = /home/ben/Downloads
    valid users = ben
    read only = No
```

---

### Post by bcraig24 on 2010-10-28
This is my entire smb.conf

```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = homeserver

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
    security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;    encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using. 
;    passdb backend = tdbsam

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
;    printing = cups
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
;    usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes
    username map = /etc/samba/smbusers
;    guest ok = no
;    guest account = nobody

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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
;    read only = yes
;    guest ok = no
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
[share]
    comment = Ubuntu Filer Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

[Downloads]
    path = /home/ben/Downloads
    writeable = yes
    browseable = yes
    valid users = ben

```

---

### Post by johnnytm on 2010-10-29
One thing I can see from here is you don't have any guest access to your /Home/ben/downloads folder,
It has only Ben as a valid user. As far as I know you have to allow guests in order to share a folder. If you are using the samba gui make the folder is writeable and visible then click on access and click allow access to everyone.

---

### Post by bcraig24 on 2010-10-29
ok I change it to this

[Downloads]
    path = /home/ben/Downloads
    writeable = yes
    browseable = yes
    valid users = ben
    guest ok = yes
    read only = no

still not visible.
[share] allready had guest access but thats not visible either.

---

### Post by Morbius1 on 2010-10-29
I wonder if nmbd is not running. To find out run the following command:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```Then run the following command to see if there are any intesting error messages:
```
smbtree
```

---

### Post by bcraig24 on 2010-10-29
ben@ben-server:~$ smbtree
Enter ben's password: 
HOMESERVER
    \\FREEAGENT              NETGEAR WNDR3700
        \\FREEAGENT\IPC$               IPC Service (NETGEAR WNDR3700)
    \\BEN-SERVER             ben-server server (Samba, Ubuntu)
cli_start_connection: failed to connect to BEN-SERVER<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE

---

### Post by bcraig24 on 2010-10-29
Oh and yesterday I decided to buy a Netgear WNDR3700 N600 router and using it with a D-Link 526b adsl2 modem.
The freeagent is my external harddrive plugged into my router directly

---

### Post by johnnytm on 2010-10-29
Try to edit your smb.conf file.
```
sudo gedit /etc/samba/smb.conf
```
scroll to ######Authentication####### go to the line where it has security=user and put  # at the very beginning of that line. then go to the beginning of line that says encrypt passwords and remove the ; there and change the word 'yes' to 'true' . Thats the biggst difference I see between what you have and what I have in my smb.conf file.

---

### Post by bcraig24 on 2010-11-02
Ok I am going to mark this thread as solved but not 100%

I discovered the connection was there the whole time when I manually directed the explorer to the server ip \\192.168.1.2 and it worked so then I just created a new network map and manually configured the path to the server ip.

But still not displaying my server in the Network browser but im not too worried about that anymore.


Thanks for all the help =)

---

