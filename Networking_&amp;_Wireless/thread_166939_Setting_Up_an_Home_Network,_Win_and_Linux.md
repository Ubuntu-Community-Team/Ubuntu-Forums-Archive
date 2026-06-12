---
title: "Setting Up an Home Network, Win and Linux"
date: 2006-04-27
forum: Networking &amp; Wireless
---

### Post by Prism on 2006-04-27
Hi there,

I have two computers, running Ubuntu Dapper and Windows XP. The ubuntu machine is connected to the internet via a modem and the Windows machine is connected to the Ubuntu machine by a cable.

I've managed to configure the internet share, so the Windows machine will have internet, but I can't configure them to have file and printer sharing.

What can I do in order to do it?

Thanks.

---

### Post by Iowan on 2006-04-27
Samba comes to mind - dunno if you have it installed yet, or what kind of file sharing you intend.

---

### Post by Prism on 2006-04-27
Yeah, I installed Samba, tried to configure it to my network but when I type "smb://" in the location field in Nautilus I don't see any computers.

---

### Post by FredSambo on 2006-04-27
[QUOTE=Prism]Yeah, I installed Samba, tried to configure it to my network but when I type "smb://" in the location field in Nautilus I don't see any computers.[/QUOTE]

paste your /etc/samba/smb.conf file here so we can look at it.

---

### Post by Aramil on 2006-04-27
I have almost the same problem.I have an Ubuntu 5.10 machine and a win98.Today I connected the win98 PC on my router but i don't know how to go any further...for e.x share my ADSL connection.Can anybody help me?

---

### Post by FredSambo on 2006-04-27
[QUOTE=Aramil]I have almost the same problem.I have an Ubuntu 5.10 machine and a win98.Today I connected the win98 PC on my router but i don't know how to go any further...for e.x share my ADSL connection.Can anybody help me?[/QUOTE]

yes.

---

### Post by FredSambo on 2006-04-27
first, do you have samba installed on you ubuntu machine?

---

### Post by FredSambo on 2006-04-27
i have been messing with a samba network all day actually.  i still can't get DNS to work properly in dapper, although it works fine in breezy.  i can still browse any samba share via IP though, so it is no big thing.  i finally got my print server set up today as well, that took a couple weeks and there are still a few bugs, but i feel pretty good about it.

so i think i may be able to help.  we will see.

---

### Post by FredSambo on 2006-04-27
from the first post:
> the Windows machine is connected to the Ubuntu machine by a cable.

is there a switch or hub in there somewhere?

---

### Post by Aramil on 2006-04-27
I have installed Samba yes

---

### Post by FredSambo on 2006-04-27
so go get your samba configuration file at:

sudo gedit /etc/samba/smb.conf

and post it.

on the windows machine: have you run the network set-up wizard? if so, what did you name your workgroup.  if you didn't run the wizard, it defaulted to MSHOME, which is the default samba configuration, so you *should* be able to see your ubuntu computer in your network neighborhood (my network places).  can you?

---

### Post by FredSambo on 2006-04-27
if you haven't run the wizard, go ahead, but choose the "my computer connects to the internet through a network hub or gateway" option.  windows will probably warn you that that type of connection is unsafe but ignore that propaganda and move on.

---

### Post by Aramil on 2006-04-27
Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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


I will tell you if I see it in a couple of minutes...

---

### Post by Aramil on 2006-04-27
Where is the network setup wizard in windows 98?

---

### Post by FredSambo on 2006-04-27
ok try this:

Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not many any basic syntactic
# errors.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = MSHOME

# server string is the equivalent of the NT Description field
server string = ubuntu

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
; wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
; wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
; name resolve order = lmhosts host wins bcast


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
; syslog only = no

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
 security = shared

# You may wish to use password encryption. See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
passdb backend = tdbsam guest

obey pam restrictions = yes

; guest account = nobody
invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
; unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
; pam password change = no


########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
; load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
; printing = bsd
; printcap name = /etc/printcap

# CUPS printing. See also the cupsaddsmb( manpage in the
# cupsys-client package.
; printing = cups
; printcap name = cups

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
; printer admin = @ntadmin


######## File sharing ########

# Name mangling options
; preserve case = yes
; short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
; include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
# SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
; message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
; domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
; idmap uid = 10000-20000
; idmap gid = 10000-20000
; template shell = /bin/bash

#======================= Share Definitions =======================

[homes]
comment = Home Directories
browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
; comment = Network Logon Service
; path = /home/samba/netlogon
; guest ok = yes
; writable = no
; share modes = no

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
; write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
; comment = Samba server's CD-ROM
; writable = no
; locking = no
; path = /cdrom
; public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
# cdrom share is accesed. For this to work /etc/fstab must contain
# an entry like this:
#
# /dev/scd0 /cdrom iso9660 defaults,noauto,ro,user 0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
# is mounted on /cdrom
#
; preexec = /bin/mount /cdrom
; postexec = /bin/umount /cdrom

***

remember that you are opening up your home directory to file sharing, which could be considered insecure.

---

### Post by FredSambo on 2006-04-27
> Where is the network setup wizard in windows 98?

christ, i can't remember.  LOL

maybe it is the internet connection wizard.  probably in the control panel.  try that.

---

### Post by FredSambo on 2006-04-27
ok so once you edit your config file you should add a user:
sudo smbpasswd -a yourname

then restart your samba daemons:

sudo /etc/init.d/samba restart

---

### Post by FredSambo on 2006-04-27
i am probably taking you the long way around the bend here.  hehe

---

### Post by Aramil on 2006-04-27
Do I have to restart my computer in order to use the current settings you gave me?

---

### Post by FredSambo on 2006-04-27
no, just the samba daemons.  i'll post slower since you aren't on broadband.  :)

sudo /etc/init.d/samba restart

---

### Post by Aramil on 2006-04-27
I m really sry if I post slowly,i am on broadband, but i have to run bck and forth in the house to configure the PCs....

---

### Post by FredSambo on 2006-04-27
[QUOTE=FredSambo]ok so once you edit your config file you should add a user:
sudo smbpasswd -a yourname

then restart your samba daemons:

sudo /etc/init.d/samba restart[/QUOTE]

...

---

### Post by FredSambo on 2006-04-27
oh, i see.  it's no big thing.

forgive me if i am rusty on my win98 info.

---

### Post by FredSambo on 2006-04-27
so if you go to "places" on the ubuntu machine and select "network servers" do you see MSHOME there?

---

### Post by FredSambo on 2006-04-27
you are running ubuntu breezy right?

---

### Post by Aramil on 2006-04-27
No....Although i see an MSHOME in the Win98 PC with only the win98 PC inside...

---

### Post by FredSambo on 2006-04-27
well that's a start!  LOL

did you do smbpasswd?

---

### Post by FredSambo on 2006-04-27
on the windows computer go to start -> run and type: \\ followed by the ubuntu machine's IP.  if that doesn't work do start-> run command (or cmd) and type: ping followed by the ubuntu IP. is the ping successful?

get the ubuntu machine's IP via

ifconfig

---

### Post by FredSambo on 2006-04-27
oh yeah, you may also want to install winbind.

sudo apt-get install winbind

and then restart samba.  i always forget about winbind.

---

### Post by FredSambo on 2006-04-27
i want to pause for a moment to say that helping people is not easy.

i am a persistant computer person, so my methods are pretty convoluted, or so it seems.

---

### Post by Aramil on 2006-04-27
I t cannot be seen.Where do I use this SMB password?

---

### Post by FredSambo on 2006-04-27
[QUOTE=Aramil]I t cannot be seen.Where do I use this SMB password?[/QUOTE]

in the terminal on the ubuntu machine.

sudo smbpasswd -a yourname

---

### Post by FredSambo on 2006-04-27
can you ping your windows machine from ubuntu?  can you ping your ubuntu machine from windows?  do both machines have an IP address?  is there basic connectivity?

---

### Post by Aramil on 2006-04-27
My router has assigned IP adresses to both PCs.And from my router I can see the windows Machine name.But the win98 PC has no Internet....I assigned the SMB password.Where do I use it..?

---

### Post by FredSambo on 2006-04-27
did you run the internet connection wizard in windows 98?

---

### Post by FredSambo on 2006-04-27
we can do this, we just have to go one step at a time.

---

### Post by Aramil on 2006-04-27
Yes but it is crap...Nothing happens....

---

### Post by FredSambo on 2006-04-27
can you ping?

---

### Post by Aramil on 2006-04-27
Really sorry but i Had to turn one PC off cause it's in my sisters room.We all go to sleep now.We will continue tommorow if u want!Goodnight!

---

### Post by FredSambo on 2006-04-27
OK guy.

---

### Post by Iowan on 2006-04-27
[QUOTE=Prism]Yeah, I installed Samba, tried to configure it to my network but when I type "smb://" in the location field in Nautilus I don't see any computers.[/QUOTE]


Didja get any further on _your_ problem?
Is the Windows box set up to share files? If I click Places>Network servers, I see all machines in my workgroup that have files to share. 
Next, are all machines set to the same workgroup?

---

### Post by Aramil on 2006-04-28
Our news...I can ping the router and the Ubuntu machine from my 98 box (i type the 192.168.0.1 and so on adresses,right?).I get response but still the one PC can't see each other...

---

### Post by FredSambo on 2006-04-28
well now that we know you have connectivity, we can work on that.

can you browse the ubuntu box from the run command in windows?  (see below)

> Yeah, I installed Samba, tried to configure it to my network but when I type "smb://" in the location field in Nautilus I don't see any computers.

also, did you try typing in smb:// and then the IP address of the machine you are trying to browse?

on the windows computer, if you can't see anything in "my network places." try going to start -> run and type \\ and then the IP of the ubuntu computer you are trying to browse.  what happens then?

---

