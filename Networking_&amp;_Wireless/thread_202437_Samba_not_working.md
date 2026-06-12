---
title: "Samba not working?"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by zneastman on 2006-06-23
So here's the situation:

I have two computers, both running Dapper, hooked up to the same router (one wired, one wireless).  A pretty simple setup.   

I want to share folders and a printer between them, and so installed samba, set both computers domain names to the same thing, and under System/Administration/Shared Folders chose a couple folders to share with Samba.  It didn't work -- that is, neither computer can see anything on the other.  NFS has the same problem.

I've been to the ubuntu Wiki, searched throught the forums, reviewed my smb.conf, and still nothing.  Does anyone have any idea what could possibly be going wrong?

---

### Post by christhemonkey on 2006-06-23
Can the computers ping each other?

```
ping ipadress
```

Replacing ip adress with actual ip adress, in the form: 123.456.123.456

Can you post us your smb.conf?

---

### Post by zneastman on 2006-06-23
Yup.  They can both ping each other.  Here's the smb.conf from the computer that's got shared folders:

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = 517

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
;   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

#======================= Share Definitions =======================

wins support = no
[homes]
   comment = Home Directories
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

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
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

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



[Media]
path = /media/Media
comment = 517 Media
available = yes
browseable = yes
public = yes
writable = yes

[Shared]
path = /home/nate/Shared
comment = Testing Samba Shares
available = yes
browseable = yes
public = yes
writable = yes

---

### Post by christhemonkey on 2006-06-25
If you go into firefox, and type into the location bar:
```
smb://ip.add.ress/sharename
```
Can you connect then?



Just a thought,
Try changing the line:
> security = user

To:
```
security = share
```

This is less secure but is one less obstacle to have to get through for now.

---

### Post by tturrisi on 2006-06-25
make sure you are NOT logged in as root because:
; guest account = nobody
invalid users = root

---

### Post by timmr72 on 2006-06-25
I didn't see that you've created a samba user yet.

On each machine type:

sudo smbpasswd -a

This will create a new user for samba and prompt you for a password. Make it the same as  you regular user account if you want.

Also, it looks like your home directory is not set to be browseable. Change that line to "yes". Or, go to "system, administration, and then "shared folders" and add your shared folders there. Restart samba or reboot.

Restart samba with:

sudo /etc/init.d/smb restart 

-Tim

---

### Post by timmr72 on 2006-06-25
Sheesh. Just reread your post and saw that  you had shared folders out from the gui tool under System/Administration. 

Sorry about that.

---

### Post by zneastman on 2006-06-26
Thanks for all of your help so far.

1]  I've changed the security setting from "user" to "share."  I didn't think to do that earlier, and it makes sense.  At least it takes out a layer of complexity.

2]  Neither firefox nor nautilus gets anywhere with smbfs.  That is, with IP 192.168.1.3 sharing a folder called "Shared," typing "smb://192.168.1.3/Shared" into the location bar doesn't get anywhere.

3]   I've created a samba username and password on each machine.  

So far as I can tell, nothing's yet changed.  Browsing network shares still totally fails.

---

### Post by jrd on 2006-06-26
I'm pretty new to linux so I probly don't know what I'm talking about but.....
Is creation mask the same as umask? If it is then shouldn't it be 0077?
I'm probly wrong but I thought I'de ask anyway.

---

### Post by shilliard on 2006-06-27
Hi

What do you get if you type:

$ smbclient -L ip_address

You should see a list of the samba shares that are available

---

### Post by zneastman on 2006-06-27
Thanks for the idea.

I get a timeout.  It times out trying to connect on port 445, then on the next port it tries (139), then fails.

---

### Post by shilliard on 2006-06-27
ok

what if you try:

$ smbclient -L localhost

---

### Post by zneastman on 2006-06-27
The problem?  Firestarter.  I'm running a firewall on my router, so I really didn't need it running on my host machine.  Duh.  Truth be told, I'd set it up so long ago I'd completely forgotten it was there.  

Thanks for all of your help.

---

