---
title: "Samba over VPN"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by Derek Karpinski on 2011-08-05
I've finally got my OpenVPN working.  I can ping 10.8.0.1 over the VPN and it works, so the VPN is connected.
 
On my Windows laptop, I've mapped some samba shares to a network drive.  The name of the mapped drive in Windows is [\\HOME-PC\derek]("file://\\HOME-PC\derek").
 
At home, on the LAN, everything works great. The mapped drive shows up perfectly.
 
When I connect to the VPN from the windows 7 laptop, the Samba shares will not open, and the network drive is not mapped.
 
I have ssh access to the ubuntu server, so I can test things out.
 
Thanks in advance. :D

---

### Post by Derek Karpinski on 2011-08-05
Sorry, my share is [\\HOME-PC\homes]("file://\\HOME-PC\homes")
 
While on the VNC if I use an IP to the server, [\\10.8.0.1\homes]("file://\\10.8.0.1\homes"), it shows up.
 
The windows laptop can't resolve the server hostname.  What settings do I need to change? :)

---

### Post by Boondoklife on 2011-08-05
Well I can think of two solutions one easy one is a pain.

**Easy**
If the ip works, then just edit your hosts file (/etc/hosts) and put the computer name in there and point it to the ip
10.8.0.1 HOME-PC

**Pain**
You can forward all traffic through the VPN and this should fix it, but it will normally result in a slow connection.

---

### Post by Derek Karpinski on 2011-08-07
Thanks, but that did not work.

smb.conf
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
    dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
    name resolve order = lmhosts bcast host wins

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
    interfaces = 127.0.0.0/8 eth0 10.8.0.0/24

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;    bind interfaces only = yes

# Allow Symlinks
    follow symlinks = yes
    wide links = yes
    unix extensions = no

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
#    SO_RCVBUF=16384 SO_SNDBUF=16384
   socket options = TCP_NODELAY

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
[homes]
    comment = Home Directories
    browseable = no
    veto files = /*$RECYCLE.BIN/*desktop.ini/

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

```

---

### Post by Boondoklife on 2011-08-07
What did not work? If you have the drive mapped and can get to it via ip the the hosts file would work by allowing you to type the name instead of the ip. It would not allow you "browse" the shares as only traffic that is deemed routable is put through the vpn and most broadcast traffic is not seen as routable.

Did you try running all your traffic through the vpn and setting the vpn to hand out its own dns and wins info?

---

### Post by Derek Karpinski on 2011-08-08
What did not work was I cannot browse my samba shares on the Windows client using a hostname (\\HOME-PC\homes).  IP still works. What I've done, to make things a bit clearer is the following:

-Shared home directories from Ubuntu server.
-Mapped the shared folders to a network drive in windows.
-Changed the location of Windows 'Libraries' or My Documents to the mapped samba shares drive.

But, since I can't browse my samba shares by name over the VPN connection, the samba shares don't show up in 'Network Neighborhood' in windows, and consequently fail to map to the drive, and then I have no 'My Documents', Music, etc.

Now, this setup works great while at home on the LAN.  It's seamless, and my wife just saves to 'My Documents' on her Win 7 laptop, and when she logs into Ubuntu, everything is there.

I understand what you're saying about routing all traffic through the VPN, but the VPN is sooooooo sloooooooooow right now, it's not even managable, and I'm finding it impossible to connect to the VPN while on my LAN.

So, am I asking for the impossible?  I'm no pro at Ubuntu, networking or even VPN, but it looked like a solution.  I think throwing Samba in the mix makes it more difficult.

So, all that said.......can I use 'netbios name = home-pc' in my smb.conf file?  I guess I'm confused on WINS, and netbios.

Thanks:guitar:

---

### Post by Derek Karpinski on 2011-08-09
bump?

---

### Post by Boondoklife on 2011-08-09
Ok just to clarify something, there is not going to be a way to browse the samba network without redirecting your traffic.

As far as being able to access it by name, make an entry in the "laptops" hosts file and see if you can ping it by name instead of ip. The servers hosts file does not matter as you are not using it as a dns. Windows and Linux put the hosts files in different spots, but a google search should find it for you. If you can ping it by name while on the vpn (outside of the network), then you should be able to use \\hostname\share.

---

### Post by Derek Karpinski on 2011-08-10
Thanks,
 
I had changed the lmhosts file on the Windows laptop, and that screwed things up when I was on the LAN, due to different IP addresses of the server when on the LAN as opposed to the VPN.  It took a long time to boot, and then couldn't map the shared folder when on the LAN.
 
I changed the hosts file with the computer name of the server, and the IP of the server when on the VPN.  I saw no problems when on the LAN, but will need to go to Starbucks tonight to check the VPN, but I think that will work.
 
I assumed the lmhosts file was the one to change, but I was wrong.
 
thanks for your help! :)
 
I'll mark as solved when I connect to the VPN to test it.

---

### Post by Boondoklife on 2011-08-10
You could put together a vbscript to switch between the two hosts files when you run it. You might need to reboot for it to take effect but that is not a big deal.

This way you have one for LAN and one when you are not on the LAN.

---

### Post by Derek Karpinski on 2011-08-10
No need...........
 
the hosts file seems to be working over the VPN, but not screwing up over LAN.
 
the lmhosts file was working over the VPN, but screwing up over LAN.
 
the hosts file works...........at least so far.  like I said, I can't connect to the VPN at my house.  I need to check it at a coffee shop.
 
VPN still seems so awfully slow.  I'm not really happy about that, but I don't know what else to do.
 
Maybe if my wife is on a slow connection, like a coffee shop, just have her save her files locally, and then when she gets home, write a script to rsync to her server home folder?

---

### Post by Boondoklife on 2011-08-10
Yup, or there is the MS sync toy. It should do what you want, but beware  and keep a backup as syncing can go haywire sometimes (especially if  both sides get changed for some reason.)

What types of files are you trying to use with the VPN, if they are large files then maybe sftp would be a better option as ftp has less overhead and with encryption the vpn is not necessary.

---

### Post by Derek Karpinski on 2011-08-10
Any and all files.  If it were my laptop, I wouldn't be opposed to using sftp, or something else, but I need this as seamless as possible for my wife, while somewhat computer savvy, is impatient, and just wants it to work.  LOL.
 
Pictures, music, documents.........etc, should be available to her remotely, just like she was at home on the LAN.
 
Granted, I've only checked the speed of the VPN at Starbucks, who really seem to limit bandwidth.  But, it's really unusable from there.
 
I'm not hell-bent on a VPN, just a solution that will let me map the samba shares to a network drive in windows, so I can make her Win 7 'Libraries' point to the shares.  And do so as seamlessly as possible.

---

### Post by Derek Karpinski on 2011-08-10
Oh, the MS sync thing doesn't seem to work with my networked drive.

---

### Post by Boondoklife on 2011-08-10
Might take a look at this for mounting sftp, came on it through a quick google.

[http://superuser.com/questions/67551/mounting-ssh-sftp-shares-on-windows-7](http://superuser.com/questions/67551/mounting-ssh-sftp-shares-on-windows-7)

---

### Post by Derek Karpinski on 2011-08-10
Now that looks like something that could work.  I'll have to check into it.  Thanks!:D

---

### Post by Derek Karpinski on 2011-08-11
Marked as solved.
 
Editting the 'hosts' file in Windows fixed it.  The file simply contains:
 
```
10.8.0.1     HOME-PC
```
 
Now, the samba shares map when on the LAN, and when connected to the VPN. :D
 
As for the speed of the VPN, I found there is little overhead with the VPN.  It is really a function of the crappy Starbucks free wi-fi.  I downloaded a large file with their wi-fi, and off my VPN, and got 150KB/sec, and then connected my VPN, and copied a file from the Samba share to the Desktop, and got 135KB/sec.  So, about 10% overhead on speed with the VPN.  With a fast connection over wireless N, it should be very workable.
 
Thanks for all the help boon!:KS

---

