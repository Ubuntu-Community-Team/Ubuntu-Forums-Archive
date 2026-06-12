---
title: "Can you network Vista and Ubuntu 8.10 together or should I just give up on Ubuntu?"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by cabbiinc on 2009-01-05
I've been trying to figure out how to do this for weeks now. I can't seem to do it. Vista on one computer, Ubuntu 8.10 on another, both linked via ethernet. Vista lets Ubuntu use the internet via this same ethernet crossover cable. It works. But I can't share files.

I think the main thing I am stuck with is how to set up Ubuntu's 'Connect to Server'. I know I want to connect to Windows Shares but the fields are confusing. What do I put where?

Feel free to copy and paste a link to the obvious. I want to share files, and possibly a scanner/printer.

---

### Post by Iowan on 2009-01-05
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://samba.netfirms.com/]("http://samba.netfirms.com/")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by cabbiinc on 2009-01-09
I'm just really confused. All of those links refer to XP and I have Vista. Enough has changed between the two operating systems that I can't make heads or tails of it.

Here's what I've tried so far:

Click Places > Connect to Server:
Select Windows share

Under server I've put the name I put on the Vista machine, my user name, Vista itself, mshome, workgroup, mswoekgroup...

Under share I put the folder that I want shared from Vista, I've left it blank, I've put in random stuff.

Under folder I've left it blank, I've put the folder I want shared in Vista, I've put random stuff in like Vista, desktop, the name of the Vista computer (Pink Floyd),

User name I put my Vista user name

Domain name I've tried everything I tried under server.

This is all greek to me, I'm not getting anywhere. Has anyone actually done this with Vista? I've searched through the forums for solved cases and I usually come up empty.

On a side note I networked Vista to XP through a router with firewalls on each in about 3 minutes. This has been plaguing me for over a month.


HELP!!!!!!

---

### Post by cabbiinc on 2009-01-09
The output of my smb.cnf file is

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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
[CODE]
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

### Post by frankelr on 2009-01-09
There is at least one bug Nautilus ..Samba...Gnome  which makes this hard, its being worked on since February 2008.  What you can do is  what you started:
Places, Connect to Server, service Type Windows Share, Server = host nane for your vista pc, share = name of top level folder you set up to share on vista, folder is actual folder you have on vista machine, username = your vista login name, domain name = your workgroup on vista typically "workgroup".

If you did vista sharing correctly and samba is setup correctly then this shoud work.. if it does do it again and create a bookmark.

If you set up both vista and samba share to work with no login name and passwords... this may become much easier.  I didn't try this. You might also read up on smbclient and apt-get install the smb4k gui.  Not sure
any of this was worth the three for four days I put into this problem

Hope this helps

Bob

---

### Post by cabbiinc on 2009-01-09
> **frankelr said:**
> There is at least one bug Nautilus ..Samba...Gnome  which makes this hard, its being worked on since February 2008.  What you can do is  what you started:
Places, Connect to Server, service Type Windows Share, Server = host nane for your vista pc, share = name of top level folder you set up to share on vista, folder is actual folder you have on vista machine, username = your vista login name, domain name = your workgroup on vista typically "workgroup".

If you did vista sharing correctly and samba is setup correctly then this shoud work.. if it does do it again and create a bookmark.

If you set up both vista and samba share to work with no login name and passwords... this may become much easier.  I didn't try this. You might also read up on smbclient and apt-get install the smb4k gui.  Not sure
any of this was worth the three for four days I put into this problem

Hope this helps

Bob

](*,) Do I need \ or / anywhere. I am still getting the "failed to mount windows share" error.

If I do an ipconfig /all on the Vista computer I get this:

Microsoft Windows [Version 6.0.6001]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\Dan>ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : pinkfloyd
   Primary Dns Suffix  . . . . . . . : Vista
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : Vista
                                       domain.actdsltmp

Ethernet adapter Network Bridge:

   Connection-specific DNS Suffix  . : domain.actdsltmp
   Description . . . . . . . . . . . : MAC Bridge Miniport
   Physical Address. . . . . . . . . : 02-19-D1-40-10-74
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 192.168.0.6(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Monday, December 29, 2008 8:45:42 AM
   Lease Expires . . . . . . . . . . : Tuesday, December 30, 2008 8:45:45 AM
   Default Gateway . . . . . . . . . : 192.168.0.2
   DHCP Server . . . . . . . . . . . : 192.168.0.2
   DNS Servers . . . . . . . . . . . : 192.168.0.2
                                       205.171.3.25
   NetBIOS over Tcpip. . . . . . . . : Enabled

---

### Post by frankelr on 2009-01-09
Sorry it didn't work for you, I just checked what I did and none / or \ are required.  I suggest you try smbclient the howto is at
[http://learnlinux.tsf.org.za/courese/build](http://learnlinux.tsf.org.za/courese/build).....

What you are trying to do here is determine whether the vista sharing is correct

the smbclient string is smbclient \\\\yourvistpcname\\asharenameonvista

this should tell you that the network is basically working. If not recheck your vista setup.   PS: this time the slashes are very important.

if you prefer you can download smb4k you should see the vista machine listed even if you can mount a share


Bob

---

### Post by cabbiinc on 2009-01-09
> **frankelr said:**
> Sorry it didn't work for you, I just checked what I did and none / or \ are required.  I suggest you try smbclient the howto is at
[http://learnlinux.tsf.org.za/courese/build](http://learnlinux.tsf.org.za/courese/build).....

What you are trying to do here is determine whether the vista sharing is correct

the smbclient string is smbclient \\\\yourvistpcname\\asharenameonvista

this should tell you that the network is basically working. If not recheck your vista setup.   PS: this time the slashes are very important.

if you prefer you can download smb4k you should see the vista machine listed even if you can mount a share

Bob

Your link doesn't go anywhere.
I looked in synaptec and smbclient is installed.
I downloaded smb4k and I'm at the same spot. Still can't mount anything.

Dan

---

### Post by Ahadiel on 2009-01-09
Have you tried specifying only the IP/hostname of your vista box in "Connect to server"?

---

### Post by cabbiinc on 2009-01-09
> **Ahadiel said:**
> Have you tried specifying only the IP/hostname of your vista box in "Connect to server"?

Just putting in the IP address returns the error pretty quickly as if it doesn't even try.

---

### Post by cwbar_1 on 2009-01-09
Try this.
[http://ubuntuforums.org/showthread.php?t=511327](http://ubuntuforums.org/showthread.php?t=511327)
Worked for me.

---

### Post by jonandrews on 2009-01-10
This thread makes it look incredibly complex to achieve, which has not been my experience..

Have a look at my step-by-step Networking guides..

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by cabbiinc on 2009-01-10
> **jonandrews said:**
> This thread makes it look incredibly complex to achieve, which has not been my experience..

Have a look at my step-by-step Networking guides..

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

I have yet to do a single task in Ubuntu aside from playing the games that comes with the distro without having to come to the forums to ask how/why/what did I do wrong/is there a bug/did I type that right/what the heck does that mean.

In my experience all versions of Windows that I have used have been exceedingly easier. Dos 3.0, 3.1, win 95, win 98 &98se, XP, NT4, and Vista home basic. They have all just worked out of the box. The only reason why I am trying Ubuntu is that my 98se is no longer supported and the world is moving further along. I can't get programs for it anymore and I don't want a pirated copy of anything. I do appreciate the forums and the people that help others without being asked or compensated. I'm sure I'm in the minority in the problems department and I am not trying to dis Ubuntu nor it's users, but nothing I've done here has been easy.

EDIT ----

I just want to make it clear that I am not blaming Ubuntu for this particular problem. I suspect Vista for this problem equally as much as Ubuntu, if not more. To get the internet to Ubuntu through Vista I had to do a manual update of an unsigned driver for my network bridge, Ubuntu then didn't have any problems connecting to the internet. I just now want to share files as I see other people come to the forums and solve this problem rather easily.

---

### Post by cabbiinc on 2009-01-15
I'm just not seeing any progress. Windows won't acknowledge Ubuntu and Ubuntu won't acknowledge Vista. Period.

I'm begging to think this will never happen.

---

### Post by HermanAB on 2009-01-15
See this: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by cabbiinc on 2009-01-15
](*,) ](*,) ](*,)

---

### Post by jobo1313 on 2009-01-17
Have you installed the windows file share service?

---

### Post by afotey on 2009-01-19
Well i think you should try to out this link. it worked for me [http://ubuntuforums.org/showthread.php?t=985415](http://ubuntuforums.org/showthread.php?t=985415)

---

### Post by cabbiinc on 2009-01-20
> **jobo1313 said:**
> Have you installed the windows file share service?

I don't know, I installed Samba and have that going but with everything else I might have to uninstall and reinstall it to make it work. That's what I had to do to Pidgin and FireFox.

I've looked at so many solutions and "Hey, look at this thread" kind of stuff that's a thread with a link to a thread to a link to a thread that I can't remember what I've tried and what I haven't.

---

### Post by cariboo on 2009-01-20
Vista Home can be a real pain to get to network. Make sure you have shares setup properly on your VIsta computer in order for the Ubuntu computer see them. Make sure they are both in the same work group. Windows Home versions usually use MSHOME, and Ubuntu defaults to WORKGROUP. To change the workgroup in Ubuntu press Alt-F2 and type:

```
gksu gconf-editor
```

got to System-->smb right click workgroup in the right pane and select Edit Key, enter MSHOME, or whatever your workgroup is, as long as it is the same as your VIsta computer. Click File-->Quit.

Make sure both computers are on the same netblock, your Vista computers ip address is 192.168.0.6 so the Ubuntu computers ip address should be in the range of 192.168.0.1 to 192.168.0.254 excluding 192.168.0.6.

Once you have made sure of all of the above you should be able to go to Places-->Network and you should see a Windows Network Icon, double click the icon and you should see your workgroup name, double click the workgroup icon and you should see your Vista computer, from there its up to you.

Jim

---

### Post by cabbiinc on 2009-01-21
> **cariboo907 said:**
> Vista Home can be a real pain to get to network. Make sure you have shares setup properly on your VIsta computer in order for the Ubuntu computer see them. Make sure they are both in the same work group. Windows Home versions usually use MSHOME, and Ubuntu defaults to WORKGROUP. To change the workgroup in Ubuntu press Alt-F2 and type:

```
gksu gconf-editor
```

got to System-->smb right click workgroup in the right pane and select Edit Key, enter MSHOME, or whatever your workgroup is, as long as it is the same as your VIsta computer. Click File-->Quit.

Make sure both computers are on the same netblock, your Vista computers ip address is 192.168.0.6 so the Ubuntu computers ip address should be in the range of 192.168.0.1 to 192.168.0.254 excluding 192.168.0.6.

Once you have made sure of all of the above you should be able to go to Places-->Network and you should see a Windows Network Icon, double click the icon and you should see your workgroup name, double click the workgroup icon and you should see your Vista computer, from there its up to you.

Jim

Yep, I've done all that. In fact, Ubuntu gets its internet through Vista, but neither Vista nor Ubuntu will even acknowledge the other exists. They can't see each other at all. Workgroups are the same, IP ranges are the same, but neither will even say that there is a computer at the other end of the Cat5 cable at all.

---

### Post by sasakitomiya on 2009-01-21
If you are sharing a Vista folder and want to see it in Ubuntu Steps are simple as:

(Assuming you have Samba Client running in Ubuntu)
Open Places->Network
Select Windows Network
Select your domain or workgroup
Select PC.  It will prompt you for the info.
To auto map the drive then you will have to edit your fstab that is another thing

open a share in Vista from Ubuntu
Same as above just need to config and add a valid Samba user.

Hope this helps.

---

### Post by cabbiinc on 2009-01-21
> **sasakitomiya said:**
> If you are sharing a Vista folder and want to see it in Ubuntu Steps are simple as:

(Assuming you have Samba Client running in Ubuntu)
Open Places->Network
Select Windows Network
Select your domain or workgroup
Select PC.  It will prompt you for the info.
To auto map the drive then you will have to edit your fstab that is another thing

open a share in Vista from Ubuntu
Same as above just need to config and add a valid Samba user.

Hope this helps.

I get too the Windows Network and everything's blank. Same goes for viewing Network Places in Vista. Both have sharing enabled.

---

### Post by Faither on 2009-01-23
Ubuntu can network with Windows - Vista however is a different story ^^

There's too many 'safty features' build into Vista that make it a pain in the **** to set it up.

You have to check that:
Sharing files/printers is enabled
Network settings **are _NOT_ set to public Network** for your network bridge
Windows Firewall does NOT block your network (aparently the only thing it's good for)
And Vista is looking for and transmitting a network id (which by default it does not)
Oh... and you have to have folders shared.

While under Ubuntu you could pretty much start and work with the default setup of smb.

So my advice would be to connect from Vista to Ubuntu.

To do so you don't use the default Windows Network Environment search but type in the IP of your Ubuntu machine directly in the explorer address line:

```
\\<Ubuntu ipv4 address here>
```
which would look like something like this:
```
Example:
\\192.168.1.102
```

This should work without having to touch anything on the Vista machine, as long as samba is running on Ubuntu.

---

### Post by cabbiinc on 2009-01-28
I give up, it can't be done.

The Vista gurus point fingers at Ubuntu, the Ubuntu people point fingers at Vista. It's already consumed more of my life trying to get it to work than any networking should ever take.

Vista and Ubuntu are just too incompatible. So don't try to tell me that Vista is just XP with a different start button. I wish it were cause then I would get it to work.

Enough from me
I appreciate your efforts
Regards

---

