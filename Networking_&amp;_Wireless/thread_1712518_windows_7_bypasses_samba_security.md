---
title: "windows 7 bypasses samba security"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by tfpsound on 2011-03-22
Hello.  I'm having a strange problem here.  When I run this share the ubuntu machines and the windows 2000 machines ask for a user name and password,  This all works well and I can access the shares.  When I access the shares with a windows 7 laptop it bypasses all the security.  When I check the log files the ubuntu and win2k machines looks ok.  With the win7 machine the log is just an empty ip address.  My smb conf files is posted below.  (forgive me if it's long and obnoxious)

[global]

## Browsing/Identification ###

   workgroup = ****

   server string = %h server (cube-x)

     wins support = yes

     dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
    name resolve order = lmhosts host wins bcast


#### Debugging/Accounting ####


   log file = /var/log/samba/log.%m

   max log size = 1000

   syslog = 0

   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

    security = user

    client ntlmv2 auth = yes 

    encrypt passwords = true
  
    passdb backend = tdbsam

    obey pam restrictions = yes

    unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).

    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\successfully* .

    pam password change = no

    map to guest = bad user

########## Domains ###########


    domain logons = no


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

    usershare max shares = 25

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
    usershare allow guests = yes

#======================= Share Definitions =======================

;[homes]
;      comment = Home Directories
;      browseable = no
;    read only = no
;    create mask = 0775
;    directory mask = 0700


# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S


[netlogon]
    comment = Network Logon Service
       path = /home/tim
    guest ok = no
      read only = no
     directory mask = 0700
    valid users = tim
*
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700


;[printers]
;   comment = All Printers
;   browseable = no
;   path = /var/spool/samba
;   printable = yes
;   guest ok = no
;   read only = yes
;   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
;[print$]
;   comment = Printer Drivers
;   path = /var/lib/samba/printers
;   browseable = yes
;   read only = yes
;   guest ok = no


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

