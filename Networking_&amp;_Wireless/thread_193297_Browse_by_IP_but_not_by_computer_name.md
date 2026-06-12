---
title: "Browse by IP but not by computer name"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by epohs on 2006-06-09
I have two ubuntu machines, and I can browse both by IP address, but neither of the machine names are appearing in the network browsing of Nautilus.  My workgroup appears, but I get a "*Sorry, couldn't display all the contents of "windows Network: homegroup*" error when I select it.

However, [COLOR="SeaGreen"]smbtree[/COLOR]  sees both machines and their shares.

```
HOMEGROUP
        \\LINUX-UPSTAIRS                linux-upstairs server (Samba, Ubuntu)
                \\LINUX-UPSTAIRS\ADMIN$                 IPC Service (linux-upstairs server (Samba, Ubuntu))
                \\LINUX-UPSTAIRS\IPC$                   IPC Service (linux-upstairs server (Samba, Ubuntu))
                \\LINUX-UPSTAIRS\SharedDocs             Shared Windows Documents
                \\LINUX-UPSTAIRS\Public                 Shared Files
                \\LINUX-UPSTAIRS\print$                 Printer Drivers
        \\LINUX-DOWNSTAIRS              linux-downstairs server (Samba, Ubuntu)
                \\LINUX-DOWNSTAIRS\ADMIN$               IPC Service (linux-downstairs server (Samba, Ubuntu))
                \\LINUX-DOWNSTAIRS\IPC$                 IPC Service (linux-downstairs server (Samba, Ubuntu))
                \\LINUX-DOWNSTAIRS\Public               Shared linux files
                \\LINUX-DOWNSTAIRS\print$               Printer Drivers

```


Can anyone help?  Thanks very much, guys.

---

### Post by epohs on 2006-06-09
Here's my smb.conf as well:

```
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
# "testparm" to check that you have not made any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = HOMEGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# I dunno why, but I think this helps me
   host allow = 192.168.1.101/105

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = yes

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
;   bind interfaces only = true



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
# /usr/share/doc/samba-doc/htmldocs/Samba-HOWTO-Collection/ServerType.html
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
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no

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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @lpadmin


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

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
;   valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
;   writable = no

# File creation mask is set to 0600 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0664.
;   create mask = 0600

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
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


[Public]
path = /home/public
comment = Shared Files
available = yes
guest ok = yes
browseable = yes
public = yes
read only = no
writable = yes


[SharedDocs]
path = /media/sdb1/Documents
comment = Shared Windows Documents
wins support = yes
available = yes
guest ok = yes
browseable = yes
public = yes
read only = yes
writable = no

```

---

### Post by epohs on 2006-06-10
The machines used to show up when browsing the network in Breezy.  However, when I made the upgrade to Dapper I renamed them using **Sytem > Administration > Networking > *General Tab***.

I've looked around the forums, but not come across a solution that worked yet.

Any help, even a point to another thread would be appreciated.

---

### Post by epohs on 2006-06-10
I just noticed that I can also SSH into either machine from the other by IP, but not by machine name.

Also, when I boot my computer upstairs into XP, the machine name (LINUX-DOWNSTAIRS) shows up in HOMEGROUP, but if I try to select it, it tells me that it is "not accessible" ... "parameter incorrect".

---

### Post by drdnl on 2006-06-11
Same problem here, hopefully there will be a sloution here

(I can only reach them via IP)

---

### Post by CronoDekar on 2006-06-11
Hopping aboard the help train, I'm having this issue too.  Oddly I can resolve the NetBIOs name of my Xubuntu box when I haven't messed with it, yet even when I restore smb.conf to the original I can't get the NetBIOS name of my Ubuntu box.

---

### Post by epohs on 2006-06-19
Bumping because I haven't found a solution yet.  :( 

Anyone got any ideas?  Is there a package i need to install or something?  I don't really know where to begin.

---

### Post by epohs on 2006-08-28
Still having trouble with this, but also [COLOR="SeaGreen"]smbtree[/COLOR] is returning an error:

```
read_socket_with_timeout: timeout read. read error = Connection reset by peer.
failed tcon_X with NT_STATUS_INVALID_NETWORK_RESPONSE
read_socket_with_timeout: timeout read. read error = Connection reset by peer.
failed tcon_X with NT_STATUS_INVALID_NETWORK_RESPONSE
```


:confused: :(

---

### Post by dannyboy79 on 2006-08-30
Here is a line from the link that I have attached, "Note, the execution of the smbclient command results in the most errors, most noteably a NT_STATUS_LOGON FAILURE error. A few things you can do to fix this:
1. Check that the smb.conf file has you in the correct workgroup
2. Check your samba passwords and which password file it uses."

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/54415-fileserver-samba-printserver-cups-howto.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/54415-fileserver-samba-printserver-cups-howto.html)
Also, have you looked at your hosts file which will basically tell different machines what there name is equal to there ip? It contains really only the amount of lines that equal the amount of boxes you have on your network, something like this, 
192.168.0.20 linux-upstairs-server
192.168.0.21 linux-downstairs-server 
Check out the website, it's how I got Xubuntu on Laptop, Ubuntu on Desktop and WinXP on Desktop all Networked together.

---

### Post by epohs on 2006-08-30
thank you so much for your reply, dannyboy.


things still aren't working exactly right, although i am able to see the machine as "linux-downstairs" in both XP machines when i view the network... but, i still have to map it by IP.


changing ```
host allow = 192.168.1.101/105
``` to ```
host allow = all
``` fixed that, I believe, although I don't really like leaving things that open.


also, another thing i noticed is that smbtree is simply not returning a thing now.  no errors, no network design.  it just asks for a password, then returns to the prompt.

---

### Post by dannyboy79 on 2006-08-31
I didn't suggest changing host allow = all, I meant for you to change a file called hosts or host and add a line within it like I stated in the last thread. Also, you haven't really said if you went to that website I provided you. If you went there and have done everything exactly as it stated than you should have no problem! Do you have WinXP Pro or Home? I turned off simple file sharing on my WinXP Pro box. Also within my networking dialog box, I added MSHOME to the area that says Domains to search, something like that? Also, is your DNS server your Router's ip? 
This is straight from Microsofts website (i know I know, how dare I say that word here. SORRY everyone)
I Can Ping a Resource by Its IP Address, but I Cannot "Ping" It by Name
If you can contact a resource by using its IP address but a PING message to its host name does not work, the problem may be caused by a name resolution failure, instead of by network connectivity. Make sure that the computer is configured with the correct DNS or WINS entries, and that the DNS or WINS servers are available.
So it appears that you need to verify that your DNS ip addrress are entered correctly in the dialog I was mentioning or add to that hosts or host file your ip and it's equivalent name like I said I did which worked for me.

---

### Post by epohs on 2006-08-31
I'm sorry, I didn't mean to imply that you had suggested changing '*host allow*'.  It is just something that I tried independently that did have a positive effect on my situation.

I did visit the page you linked, and I did follow its suggestions. Also, I made sure all machines were part of the "HOMEGROUP" workgroup, and I added all IP/hostname pairs to my /etc/hosts file.  None of that seemed to work for me.

The windows machines are all XP boxes.

..hmm, i believe my DNS settings are currently configured according to my ISPs settings.  This sounds like it could be the culprit.  I will look when I get home.

---

### Post by dannyboy79 on 2006-09-01
Have you added the following to your global section of your smb.conf?

hostname lookups = yes
hosts equiv = /etc/hosts

Per the website I pointed out they mean:
hostname lookups: This field just asks whether the server should perform lookups based on the hostname of the client computers. If you set this field, you beed a hosts equiv field to tell the server the equivalent ip's of the other computers.

hosts equiv: This field just tells the server the loacation of the file which translates a IP address to a hostname.

---

### Post by dannyboy79 on 2006-09-01
Alright, If the above doesn't work than take a look at this, one guy says it worked for him. [http://www.ubuntuforums.org/showthread.php?t=247030&highlight=ping+ip](http://www.ubuntuforums.org/showthread.php?t=247030&highlight=ping+ip)

---

### Post by anindya_m on 2006-09-01
Can you try adding ip and hostname entries for all the machines in the /etc/hosts files?

---

