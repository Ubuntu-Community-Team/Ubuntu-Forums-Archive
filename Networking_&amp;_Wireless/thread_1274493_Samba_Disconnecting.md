---
title: "Samba Disconnecting"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by Groover20 on 2009-09-24
I seem to have a weird trouble...I have a Vista Laptop and a Ubuntu server for my music, movies, pictures, etc.

I'm in the process of finalizing the transfer of the files from the laptop to the server.  For most of the files, I used an external drive, as the server wasn't online yet.

So, I tried to move pictures from my laptop to the pictures folder on the server.  It works for about 30 seconds, and then, I get an error message stating that the server exist, but the path to the folder is incorrect.  If I back out, and then try to go back to the same folder, it works.

I'm a bit confused as I was able to watch a movie on my laptop last night, from the server, and did the samething with music this morning.

Did any of you ever encounter such problem?  Or have any ideas as where to start to find the solution?

Thanks in advance,
Groover20

---

### Post by Groover20 on 2009-09-24
I don't know if it's important or not, but the server has a wired connection to the router, and the laptop is wireless.

I also tried to get it from the laptop by the server, but it hung forever...

I'm really puzzled!!

---

### Post by cariboo on 2009-09-24
What does /etc/samba/smb.conf look like?

---

### Post by Groover20 on 2009-09-24
Here you go:

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
    log file = /var/log/samba/log.%m
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    socket options = TCP_NODELAY
    obey pam restrictions = yes
    map to guest = bad user
    encrypt passwords = true
    passwd program = /usr/bin/passwd %u
    passdb backend = tdbsam
    dns proxy = no
    server string = %h server (Samba, Ubuntu)
    path = /home
    unix password sync = yes
    workgroup = WORKGROUP
    syslog = 0
    panic action = /usr/share/samba/panic-action %d
    usershare allow guests = yes
    max log size = 1000
    pam password change = yes

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
    guest ok = no
    comment = Printer Drivers
    writable = no
    delete readonly = yes
    path = /var/lib/samba/printers
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


[Pictures]
    guest account = simon
    writeable = yes
    public = yes
    path = /dev/sdc1
    write list = simon,server,@samba,@server

[Multimedia]
    writeable = yes
    path = /dev/sda1
    write list = @samba,@samba

[homes]
    writeable = yes
    write list = @samba

[Backup]
    writeable = yes
    path = /dev/sdd1
    write list = @samba

---

### Post by redmk2 on 2009-09-24
> path = /dev/sdc1

This is not a correct path.  This is a partition.  I believe it needs to be a path.

Here is a share on one of my servers.
```
[Share]
        comment = Public Share
        path = /smb/share
        browseable = yes

        guest ok = yes
        writeable = yes

```

I created a directory (mount point) at / called smb.

---

### Post by Groover20 on 2009-09-24
Ok, so I changed my path from a /dev/sb1 type to a /media/multimedia type.

I tried to copy some pictures (46 or so) from the laptop to the server.  It still gives me an error, asking me to verify if I'm connected to the network.  I click retry, and it goes works.

I thought it could be the wireless connection, but I'm sitting within 2 feet of my router, and the little icon show that the connection is perfect.  I cannot try to wire the laptop to the router, as I don't have spare cable.

---

### Post by redmk2 on 2009-09-24
I'm glad you got the Samba part taken care of.  I have no ideas on your need to verify the connection.  It sure sounds like the wireless  is trying to verify the connection.  Wireless on Ubuntu presents its stumbling blocks.  Distance is not the only factor.  I would not rely on any NM icon to be accurate either.

---

### Post by Groover20 on 2009-09-24
The laptop is currently running Vista, until I can complete the transfer over my server.  I will then run it under Ubuntu.

The laptop is a Gateway M-7315U if someone know of any problems related to the wireless on this computer.

---

### Post by Groover20 on 2009-09-25
OK, I went out this morning and bought a network cable.  I plugged it and it went faster, but I lost the connection.

So I tried from the server to grab the files.  At one point, I got an error message stating that the stream ended.

I did a search on the forum, and turned off the Windows firewall.  The How-to [here]("http://ubuntuforums.org/showthread.php?t=1169149&highlight=list+folders+files&page=2") suggested to make sure that Samba was allowed, but I didn't find out how to do it, so I turned it off. 

I'm currently moving the files.  I used the server to grab them, and it's a lot faster than previously.  It hasn't froze or anything yet, so I hope it will work for now.

---

### Post by Groover20 on 2009-09-25
As I wrote the last line, I got an error message saying that there was an error opening the file, as the permission was denied...I'm really confused!!

---

### Post by Groover20 on 2009-09-25
OK, so I rebooted the laptop.  It did a Vista update, and then I tried once again to copy the files over to the server.

Surprise, surprise, it worked!  I was able to move 31gb of movies to the server without a single crash.

So I went to copy the remaining audio files, and I now get an error message!

I really don't get what can go wrong, as I use a wired connection and it worked fine for about an hour.  The only thing was that while I the files were transfering, I worked on the server, and it stopped.

---

### Post by redmk2 on 2009-09-25
> **Groover20 said:**
> OK, so I rebooted the laptop.  It did a Vista update, and then I tried once again to copy the files over to the server.

Surprise, surprise, it worked!  I was able to move 31gb of movies to the server without a single crash.

So I went to copy the remaining audio files, and I now get an error message!

It would be nice if you provided the error message.> 

I really don't get what can go wrong, as I use a wired connection and it worked fine for about an hour.  The only thing was that while I the files were transfering, I worked on the server, and it stopped.

Plenty can go wrong, and apparently something did!  What were you doing to the server? I assume you mean the host and not the smbd (Samba) server.

The best thing you can do is to learn how the system works.  This also means understanding what the errors mean or at least noting them for others to decipher in the beginning.

Have you read any of the documentation available on the web?  See [**_here_**]("http://us3.samba.org/samba/docs/") for a good start.  I particularly like [**_this_**]("http://us3.samba.org/samba/docs/man/Samba-Guide/") tutorial.  A good overview of Samba can be seen [**_here_**]("http://www.oregontechsupport.com/articles/samba.php").

There will be sections that you might not fully grasp the first time around.  Ask questions.  Plenty of folk here love to elucidate on the subject.  Have a healthy skepticism of answers that don't really explain WHY you should do something.

---

### Post by Groover20 on 2009-09-25
I went to The Unofficial Samba HOWTO,  and typed in the following on my Vista Laptop:

C:\> net view \\192.168.1.1
Shared resources at \\192.168.1.1
Share name Type Used as Comment
———————————————————–
pub 		Disk
private	Disk
The command completed successfully.

C:\> net use j: \\192.168.1.1\pub

The 1st command ran fine, but the second one states that " system error 64 has occured. the specified network is no longer available"

Is it possible that one part of my problem is permission related?

---

### Post by redmk2 on 2009-09-25
> **Groover20 said:**
> I went to The Unofficial Samba HOWTO,  and typed in the following on my Vista Laptop:

C:\> net view \\192.168.1.1
Shared resources at \\192.168.1.1
Share name Type Used as Comment
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;
pub 		Disk
private	Disk
The command completed successfully.

C:\> net use j: \\192.168.1.1\pub

The 1st command ran fine, but the second one states that " system error 64 has occured. the specified network is no longer available"

Is it possible that one part of my problem is permission related?

Not quite that way you think it is.  The client (Vista) can't see the shares from the server (Samba).

A quick guess would be the authentication from Vista is NTLMv3 and the Samba server is not setup to understand it.  You can set it up or back Vista's authentication routine down to NTLMv2.

See [**_here_**]("http://www.chicagotech.net/netforums/viewtopic.php?p=2195&sid=2f1a7d53eafea73bf925f12b8e5be3c2").

This DOES NOT mean that this is the answer, just a quick guess.  I won't be back to help until tomorrow afternoon so I thought I would at least give you some idea to Google on

BTW - I don't have a Vista host in my network.  Therefore YMMV.

---

### Post by Groover20 on 2009-09-26
I made the c:\ net use... worked.  I had mistyped a few things.  I will continue to go through with the Unofficial HOWto and I'll keep posting my questions here.

---

### Post by Groover20 on 2009-09-27
Yesterday afternoon, while out for a drive, I got thinking that the laptop had been acting a bit werid lately regarding Internet.  I sometimes was unable to connect to certain pages within a site, as if the connection was lost.  So, when I got home, I did some research, and found out that Vista was difficult regarding wireless card.  It seems like it's a fairly common problem. Actually, as I was searching on the net, I noticed that my connection was "identifying"...I knew I was on the right track then.

I booted the laptop with Ubuntu , mounted the C: and D: drives, and tried to transfer files over to the server.  It worked fine.  I moved 27.1Gb, at 1.9Mb/s in average.  The transfer rate under Vista was rarely over 1.1Mb/s.

I will then be able to install Ubuntu propely on my laptop.  The only issue will be the wireless connection not working after the laptop gets off sleep mode...But that's another story.

In short, the problem was not with Samba or my configuration, but Vista and it's handling of wireless cards.  But I must say that I learnt quite a bit about Samba throughout the process.  Thanks to all that provided me with advices.

---

