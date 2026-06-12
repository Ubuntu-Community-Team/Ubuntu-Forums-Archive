---
title: "Can't access Samba shares from Windows"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by SteinbergerNate on 2009-03-09
Ok, I've searched everywhere. Sorry if it's posted somewhere else but it's driving me nuts. 

I've started setting up Samba on my Ubuntu 8.04 machine. So far, I can see and access my Windows machine over the network. I can browse all the files and such. 

When I try to access the Ubuntu machine from Windows, I browse to it and when I try to click on my Ubuntu machine, it tells me that it's not accessible and that I might not have permission to use it. 

I don't have the same user names on my windows machine as I do the Linux one nor do I want to. I've tried all I can figure out. I've posted my smb.conf below:

```
# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

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

guest account = nobody
   invalid users = root

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

# This option controls how nsuccessful authentication attempts are mapped 
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
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

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
;   load printers = yes

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
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

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

wins support = no
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
```

---

### Post by sanderj on 2009-03-09
I might be overlooking something, but I don't any "easy" shares in your samba config. I do see user shares, but those shares are not easy. So create an easy share:

[LIST=1]
[*]Start Nautilus
[*]In your home directory, create a directory you want to share. Put something in that directory, like readme.txt with some text content.
[*]Then, right click that directory, and select "Sharing Options".
[*]In those options, select **two** options: "Share this folder" AND "Guest Access". The click Create Share.
[*]Then reboot your machine (just to be sure)
[*]You should then be able to see and access that share from others machines.
[/LIST]

HTH

---

### Post by SteinbergerNate on 2009-03-09
Yup. I did that. Still not working. Although, now for some reason (not sure if it's because I created the shares) I can't browse the network from Ubuntu anymore. I can put in a share location and it will open it up but I can't browse to it anymore.

Edit: Scratch that about not being able to browse from Ubuntu. For some reason it went back to working.

---

### Post by sanderj on 2009-03-09
Well, your samba conf does NOT show any share that accessible for a guest ...

---

### Post by ddnev45 on 2009-03-09
I don't see the lines in your configuration that define your workgroup or netbios name (edited out intentionally?); and the lines that define your interfaces and shares are still commented out with the ";".

[http://ubuntuforums.org/showthread.php?t=202605&highlight=smb.conf]("http://ubuntuforums.org/showthread.php?t=202605&highlight=smb.conf")

[http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2545972]("http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html#id2545972")

---

### Post by SteinbergerNate on 2009-03-09
Alright, I started fresh with the example smb.conf that you posted. Here's what I have so far:
```
[global]
    ; General server settings
    netbios name = bassmannate
    server string = bassmannate
    workgroup = reynolds
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
;[print$]
;    path = /var/lib/samba/printers
;    browseable = yes
;    guest ok = yes
;    read only = yes
;    write list = root
;    create mask = 0664
;    directory mask = 0775

;[printers]
;    path = /tmp
;    printable = yes
;    guest ok = yes
;    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Shared]
    path = /home/Shared
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = bassmannate
    force group = bassmannate
```
I commented out the printer info as I don't need it. 
Now when I go to get on the share from windows, it gives me a logon prompt. I have my user added so I put in my info and it lets me on. How do I get it to just let any guest on? I don't want to have to put my credentials to get on the server since this is just a small home network.

Edit: I'm back to not being able to browse from Nautilus. smbclient -L localhost -U% shows all the shares available to me but I can't see them from Nautilus without typing them in.

---

### Post by ddnev45 on 2009-03-09
I usually just create a user in linux specifically for samba sharing and let guests log in with that account. My samba share is just a common folder - typically /mnt/samba. No security issues since it's just for home.

---

### Post by villain_s_deeds on 2009-03-09
I've been having the same problem since I reinstalled Ubuntu the other day (It crashed on me).  Before, I was dual booting with XP, and I had no problem with my home network.  Now, I'm able to see the other computer's shared folders on my Ubuntu machine, but I can't see my shared folders on the Windows machine.  I'm a newbie at this Linux stuff too, which only adds to my confusion.  It worked last week, and now it doesn't.  Weird.  Also I tried to change the shared folder's permissions to see if that would help, but it immediately resets itself as if I, the owner and *only* user of this machine, somehow do not have the right to change permissions.  Like I said, I'm new here; hopefully someone can help, because I really don't want to reinstall again, just to see if I can get it to work.

---

### Post by SteinbergerNate on 2009-03-10
Well, and something else that's weird is that the share I have created in the smb.conf doesn't show up on other computers. However, the ones I created through Nautilus do. Not a huge deal but I'm just a bit confused on what's exactly is going on.

---

