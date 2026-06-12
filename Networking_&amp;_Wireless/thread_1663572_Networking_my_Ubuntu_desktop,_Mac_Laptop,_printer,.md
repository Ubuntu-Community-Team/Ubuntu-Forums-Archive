---
title: "Networking my Ubuntu desktop, Mac Laptop, printer, and external HD"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by lucaskolson on 2011-01-09
I'm a newb Linux user; I just installed it on my desktop. I love it so far, but I'm having trouble setting up a network in my apartment. I have the desktop directly plugged into my router and a mac laptop linked wirelessly to the router. I also have a printer and an external hard drive plugged into the desktop. The goal is to be able to access the external hard drive and use the printer from my mac laptop, as well as access the mac laptop from the desktop.

Right now, I can access the mac from the desktop with ubuntu on it. Under "Places" and then "Network," I can mount the folders I want and then access the contents.

I can also print and access my external hard drive from the ubuntu desktop.

However, on the mac laptop in the Finder under "Network" there is nothing. I can ping the desktop from the mac and get a response, but I can't for the life of me figure out how to get beyond this. In System Preferences I have "File Sharing" and "Printer Sharing" both checked.

What else do I need to do?

---

### Post by PatchesTheCaveman on 2011-01-10
You need to share a folder!

Right-click on the folder you want to share and click *Sharing options*.  Check Share this folder and set the options you want.  Then click *Create Share*.  You will be prompted to download and install some software.  Make sure you do that.

Once you've done that, you'll have all the software you need installed to be able to share your printer.  If your printer is not already set up, go to System > Administration > Printing to do so.  Your printer should be shared by default.  To make sure, right-click on it in the Printer administration utility.  If *Shared* is not checked, check it.

---

### Post by lucaskolson on 2011-01-12
Thanks for the tip. I think I probably should have been able to figure that one out... :/

However, all is not good. After changing the sharing settings, I could view the files from either computer. But I could still not print. After printing, the job would simply disappear. It did not print or show up on either computer's printing queue. On my mac under "System Preferences" and "Print and Fax" it shows that I'm connected to the printer and shows it as "Idle." However, on clicking "Options and Supplies" and then going to "Utility" it says that it is unable to connect to the printer.

I also couldn't view the external hard drive. When I tried to change the folder settings inside it to share it, it said:

'net usershare' returned error 255: net usershare add: cannot share path /media/Time Machine Backups/Home Movies as we are restricted to only sharing directories we own.
    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this.

Trying to figure out how to do this myself, I went into "help" and through following some instructions about file sharing from there, ended up going into the Terminal and typing in "shares-admin." Under "Shared Folders" I added the external hard drive. It still didn't work. I didn't change any other settings, and problem is, now I can't connect the mac to the desktop anymore!! I go into the Finder, and it just says "connection failed." I tried adding various paths in the "Shared Folder" window to get it to work again, even though I really don't think there was anything at all under "Shared Folders" when I first opened it up. But somehow, it seems I've screwed myself...

Help?

---

### Post by PatchesTheCaveman on 2011-01-13
Try installing the system-config-samba package from the Software Center, Synaptic, or by clicking this URL on the Linux machine:  [apt://system-config-samba](apt://system-config-samba)

Then run *shares-admin* and delete all your file shares.  Now, go to System > Administration > Samba and reconfigure them using that program.  That should work better.

Can you send a screenshot of your printer configuration on the Mac?

---

### Post by lucaskolson on 2011-01-13
Still unable to connect to the linux.

I've attached three screen shots. Two from the mac of both the failed connection and the printer configuration (or what i think you mean by that). The third picture is of the samba server configuration: the printer driver is on there, the external hard drive, and the file contents on the desktop.

Advice?

---

### Post by PatchesTheCaveman on 2011-01-13
Please run this command and copy/paste the output:
```
cat /etc/samba/smb.conf
```

Also, try disabling the firewall and try a connection from the Mac again:
```
sudo ufw disable
```

And finally, is the printer connected the the Linux machine or the Mac?

---

### Post by lucaskolson on 2011-01-13
lucas@lucas-desktop:~$ cat /etc/samba/smb.conf
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

;    wins support = no
;    wins support = no
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





;    browseable = yes
;    browseable = yes

[lucas]
    path = /home/lucas
    writeable = yes
;    browseable = yes
    valid users = lucas, nobody

[Time Machine Backups]
    path = /media/Time Machine Backups
    writeable = yes
;    browseable = yes
    valid users = lucas, nobody

---

### Post by lucaskolson on 2011-01-13
Also, I disabled the firewall using the command you gave me. Still no luck. And the printer is linked to the desktop. It prints fine from that computer, just not from the laptop.

Btw, thanks for all the help. Very much appreciated!

~Lucas

---

### Post by PatchesTheCaveman on 2011-01-14
Does the Mac ask for a username and password when connecting to the file share?

As for the printer, try this:
Open Print & Fax in System Preferences.
Click the + to add a new printer.
Choose the *IP* tab from the top.
Change the *protocol* to *Internet Printing Protocol - IPP*
Change the *address* to your Linux computers name followed by a colon and the number 631.  Based on your output from above, that should be [i]lucas-desktop:631[/code]
Change the *queue* to *printers/* and the name of your printer as it appears in System > Administration > Printing.  For instance, if it's called *PSC-1500* you would type in *printers/PSC-1500*
Make sure *Print Using* is set to *Generic PostScript Driver*.
Click *Add*.

Now give it a shot using the one you just created.

---

### Post by lucaskolson on 2011-01-15
Sigh, still not working...

For the Mac, it does not ask for a password. In the Finder, I click on Network, then lucas-desktop, then it says Connection Failed. There is a Connect As button, but pressing it only gives a message to check if the computer is connected.

For the printer, I followed your instructions. I assumed you did not mean for me to put the [i] and [/code] in the name. So the name is just lucas-desktop:631. I used the name of the printer based on what the desktop said which was "PSC-1500-series." After adding the printer and printing, the printer automatically pauses. When I unpause it, it just pauses again. If I put the print job on hold, then I can unpause the printer, but when I resume the print job, the printer immediately pauses again. Further, on the desktop, the printer queue doesn't show anything.

I alternatively tried including the [i] and [/code] in the name, using "PSC-1500" as the name, and a thread suggesting using another protocol besides IPP. None of these things helped. I also tried alternatively clicking the Share Printer button because it was not be default checked. Didn't work either way.

Any other suggestions?

---

### Post by lucaskolson on 2011-01-15
Still not working...

For the Mac, it does not ask for a  password. In the Finder, I click on Network, then lucas-desktop, then it  says Connection Failed. There is a Connect As button, but pressing it  only gives a message to check if the computer is connected.

For  the printer, I followed your instructions. I assumed you did not mean  for me to put the [i] and [/code] in the name. So the name is just  lucas-desktop:631. I used the name of the printer based on what the  desktop said which was "PSC-1500-series." After adding the printer and  printing, the printer automatically pauses. When I unpause it, it just  pauses again. If I put the print job on hold, then I can unpause the  printer, but when I resume the print job, the printer immediately pauses  again. Further, on the desktop, the printer queue doesn't show  anything.

I alternatively tried including the [i] and [/code] in  the name, using "PSC-1500" as the name, and a thread suggesting using  another protocol besides IPP. None of these things helped. I also tried  alternatively clicking the Share Printer button because it was not be  default checked. Didn't work either way.

Any other suggestions?

---

### Post by lucaskolson on 2011-01-15
Still not working...

For the Mac, it does not ask for a  password. In the Finder, I click on Network, then lucas-desktop, then it  says Connection Failed. There is a Connect As button, but pressing it  only gives a message to check if the computer is connected.

For  the printer, I followed your instructions. I assumed you did not mean  for me to put the [i] and [/code] in the name. So the name is just  lucas-desktop:631. I used the name of the printer based on what the  desktop said which was "PSC-1500-series." After adding the printer and  printing, the printer automatically pauses. When I unpause it, it just  pauses again. If I put the print job on hold, then I can unpause the  printer, but when I resume the print job, the printer immediately pauses  again. Further, on the desktop, the printer queue doesn't show  anything.

I alternatively tried including the [i] and [/code] in  the name, using "PSC-1500" as the name, and a thread suggesting using  another protocol besides IPP. None of these things helped. I also tried  alternatively clicking the Share Printer button because it was not be  default checked. Didn't work either way.

Any other suggestions?

---

### Post by lucaskolson on 2011-01-15
Sigh, still not working...

For the Mac, it does not ask for a  password. In the Finder, I click on Network, then lucas-desktop, then it  says Connection Failed. There is a Connect As button, but pressing it  only gives a message to check if the computer is connected.

For  the printer, I followed your instructions. I assumed you did not mean  for me to put the [i] and [/code] in the name. So the name is just  lucas-desktop:631. I used the name of the printer based on what the  desktop said which was "PSC-1500-series." After adding the printer and  printing, the printer automatically pauses. When I unpause it, it just  pauses again. If I put the print job on hold, then I can unpause the  printer, but when I resume the print job, the printer immediately pauses  again. Further, on the desktop, the printer queue doesn't show  anything.

I alternatively tried including the [i] and [/code] in  the name, using "PSC-1500" as the name, and a thread suggesting using  another protocol besides IPP. None of these things helped. I also tried  alternatively clicking the Share Printer button because it was not be  default checked. Didn't work either way.

Any other suggestions?

---

