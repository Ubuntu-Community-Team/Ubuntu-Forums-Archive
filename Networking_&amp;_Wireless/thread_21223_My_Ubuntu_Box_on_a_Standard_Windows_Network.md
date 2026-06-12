---
title: "My Ubuntu Box on a Standard Windows Network"
date: 2005-03-21
forum: Networking &amp; Wireless
---

### Post by kkathman on 2005-03-21
I have changed this post as the first was somewhat elementary.

I have installed Samba and configured the General Tab to have a hostname (Ubuntu), no domain name,  Description (%h (Samba, Ubuntu) and the Domain/Workgroup (WORKGROUP), and no WINS Server.

I can see all the windows machines on the network just fine. However, when I go to a Windows machine, it cannot find "Ubuntu" on the network, but can see the other windows boxes.

Obviously I may have missed some critical step. Could someone please point me toward what I need to do to get bidirectional viewing?

Thanks,
kork

---

### Post by kkathman on 2005-03-21
Removed by author

---

### Post by void on 2005-03-22
the option "Enable Windows networking" is deactivated on every boot

if this isn't your problem please post your /etc/samba/smb.conf

---

### Post by kkathman on 2005-03-22
Thanks very much for taking the time to help.

When I select Computer -> System Configuration -> Networking, under the general tab  the box that says "Enable Windows networking" is checked. Other fields on this tab:

Hostname:  Ubuntu
Domain name: <blank>
Description %h(Samba,Ubuntu)
Domain/Workgroup: WORKGROUP
WINS Server:  <blank>

The Linux box is hard cabled to a small 4 port hub, which in turn is hard cabled to a wireless router/NAT switch that is connected to a DSL modem.  My Gateway address is 192.168.248.30, the Linux box is 192.168.248.110, the main win box is 192.168.248.102.

Here is the /etc/samba/smb/conf contents:
> 
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
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
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h (Samba, Ubuntu)

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


From the Windows box I tried searching for the Linux box. Tried \\Ubuntu at the Run command line.  I tried pinging 192.168.248.110 all respond with nothing. Yet, On the Linux box itself I can see all the shared files, drives and directories I want.

Seems odd, but thank you for your help in advance.

Regards,
Kork

---

### Post by void on 2005-03-22
since youre linux box isnt responding to any ping i guess youre using a firewall
have you opened the ports for smb shares ?
the local ports opened for incoming traffic on your ubuntu should be 137 and 138 udp and 139 and 445 tcp

are the users you want to access ubuntu with, also present on ubuntu as samba users with the same passwords on the windoze pc ?

---

### Post by kkathman on 2005-03-22
Void, thank you very much for your continued support.

> 
since youre linux box isnt responding to any ping i guess youre using a firewall
have you opened the ports for smb shares ?
the local ports opened for incoming traffic on your ubuntu should be 137 and 138 udp and 139 and 445 tcp


I have a NAT switch at my home that is fed by the DSL Modem. The switch then is hard cabled to a small 4-port hub. The Linux box, and two windows boxes are on the same hub. Another windows box communicates via wireless usb to that same switch. Since they are all on the same subnet, I didnt think there would be router/firewall problems. If I open those ports, that will make 139 and others open to the outside too, which I dont think I want.

> 
are the users you want to access ubuntu with, also present on ubuntu as samba users with the same passwords on the windoze pc ?


I did set up an smbpasswd for myself on the system, then did a samba restart on the system.  When I do a smbtree the response shows the other boxes but also reports a failed negprot just before it reports them.  No one seems to know what this means.

However once I did the above, the linux box is now visible from the windows boxes, just that from there I cant see anything ON the linux box.

Thank you again for your help!

Regards,
Kork

---

### Post by gw90se on 2005-03-22
Go to the [How-to guide](http://ubuntuguide.org/) . Scroll way down to the Samba Server section. It will take you through several steps. I had the same problem last night and followed this guide. It worked!!

---

