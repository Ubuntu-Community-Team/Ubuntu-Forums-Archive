---
title: "The dreaded networking and sharing issues."
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by politenessman on 2010-12-08
I am using ubuntu 10.10 (64bit) with Gnome 2.32 on an Acer 18101tz

My home network looks like this:

Netgear N600 wireless router with connected 1TB usb drive for sharing media.
This is its connection table:

1	192.168.1.5	IPHONE
2	192.168.1.3	ACER1810TZ
3	192.168.1.2	Sony Playstation
4	--	--	
5	192.168.1.4	IPAD
6	192.168.1.10	MAC

There are a number of other computers on the network but for a number of reasons they are currently not present or powered down.

I am having a couple of issues, that I would like help in resolving, and I also want to post about expectation:

My expectation is that opening Nautilus and selecting the network browser, I will be able to see what is connected to my network. I will be able to see the computers (including the router with its share) and the inevitable windows workgroup.

What I see are two icons, one for the Mac and windows workgroup. 
Clicking on the mac icon gives me its printer share so i think that works ok, but clicking on the workgroup icon gives me the dreaded error:

Unable to mount location
Failed to retrieve share list from server

My questions are:
1. What server is it trying to retrieve this list from?
2. Why do I only see the Mac? 
3. How do I fix this?

I have my ~/user/public folder shared (on the Acer), and that sharing is set both in the properties of the folder, and via Samba, and yet I see no sign of it.

Although I can't see the shared drive on the router, if I use places > connect to server and fill in the appropriate details I can connect to it, read and write to it with no issues (other than it wanting a password and I'm pretty sure I told it not to do that, but hey, it works)

I've dug through the various threads on this issue and none of them seem to provide me with a solution. I don't have a firewall running, no anti virus, and no windows machines on this network (at least not at this time - the Acer and another MAC are both dual boot with Win7 and WinXP)

One thing everyone always gets asked is the output of certain commands, so here they are:


tony@Acer1810TZ:~$ telnet 127.0.0.1
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
tony@Acer1810TZ:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.1     READYSHARE    +[	WORKGROUP     ]
192.168.1.3     ACER1810TZ     [WORKGROUP] [Unix] [Samba 3.5.4]
192.168.1.10    PIXIMAC        [	WORKGROUP     ]
tony@Acer1810TZ:~$ sudo iptables -L
[sudo] password for tony: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
tony@Acer1810TZ:~$ 

What I want to do is:
1 - browse the network, just to see who and what is on there
2 - have my public folder available to the rest of the network for data transfer
3 - have the shared drive visible to all the network users.

Does anyone have a solutions?

---

### Post by Fiddler_Wins on 2010-12-08
Are you sure iptables is turned off (/etc/init.d/iptables stop)

Can you ping between the two machines?
What does nmap show as open ports on each box?
What does /etc/samba/smb.conf show on the system you are sharing the files on? You want browseable = yes for the shared folder if you want it to show up in network browsing.

---

### Post by politenessman on 2010-12-08
tony@Acer1810TZ:~$ /etc/init.d/iptables stop
bash: /etc/init.d/iptables: No such file or directory


tony@Acer1810TZ:~$ ping 192.168.1.10
PING 192.168.1.10 (192.168.1.10) 56(84) bytes of data.
64 bytes from 192.168.1.10: icmp_req=1 ttl=64 time=1.20 ms
64 bytes from 192.168.1.10: icmp_req=2 ttl=64 time=4.90 ms
64 bytes from 192.168.1.10: icmp_req=3 ttl=64 time=1.39 ms
64 bytes from 192.168.1.10: icmp_req=4 ttl=64 time=2.57 ms
64 bytes from 192.168.1.10: icmp_req=5 ttl=64 time=3.44 ms
64 bytes from 192.168.1.10: icmp_req=6 ttl=64 time=1.44 ms
64 bytes from 192.168.1.10: icmp_req=7 ttl=64 time=1.85 ms

> What does nmap show as open ports on each box?
on each box? I'm not sure I understand the relevance of that? Can you explain?


> What does /etc/samba/smb.conf show on the system you are sharing the files on? You want browseable = yes for the shared folder if you want it to show up in network browsing. 
I am sharing files on at least two systems, one of which is the router.
However, the Acer (the machine I am using now and trying to get working) has the following:
> 
tony@Acer1810TZ:~$ cat /etc/samba/smb.conf
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
	workgroup = workgroup
        netbios name = Acer1810TZ

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
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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
;	printing = cups
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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	security = share
;	guest ok = no
;	guest account = nobody

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

[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
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
	path = /home/tony/Public
	writeable = yes
;	browseable = yes
	guest ok = yes
tony@Acer1810TZ:~$ 

---

### Post by politenessman on 2010-12-09
Bump!

Anyone? I am really stuck with this.

---

### Post by politenessman on 2010-12-16
Bump

Anyone know how to get Ubuntu networking to work?

---

### Post by dandnsmith on 2010-12-16
It has been years (literally) since I configured one of these.

One of the things to do is to look at the smb.conf file, find the bit about how to reduce the file to exclude the dross, and then look at the result.

I would expect to bind the interface in use (your 192.168.0./24)
and declare the server to be the domain master (unless you have another one which you are using).

I, purposely, don't use the name 'workgroup' for the samba domain, as it can obscure things - but then you might have good reason to leave it that way (eg a Windows XP machine).

I apologise for this not being a proper tutorial (such things do exist IIRC), but just a set of thoughts.

---

### Post by Morbius1 on 2010-12-16
Except for you using:
> security =SHAREwhich hasn't been used since Jimmy Carter was president ( a slight exaggeration perhaps ) instead of the default:
> security = USERit looks to be the stock Ubuntu default smb.conf file. Since you only have guest shares it's probably OK to leave it that way.

One thing interests me:
> and that sharing is set both in the properties of the folder, and via Samba, and yet I see no sign of it.There's two ways to use Samba to share folders and it sounds like you're using both. Probably not the source of the problem but you never know. Please post the output of the following command:
```
net usershare info --long
```You might want to find out if all the samba services are running:
```
sudo service smbd restart
``````
sudo service nmbd restart
```Since this is an entirely wireless network I do have a suggestion and that's to alter the name resolution order so that bcast is first not last:
Add a line to the global section of smb.conf:
```
name resolve order = bcast host lmhosts wins
```Then restart smbd again. If it does nothing you can always remove it.

---

### Post by politenessman on 2010-12-16
> **Morbius1 said:**
> Except for you using:
which hasn't been used since Jimmy Carter was president ( a slight exaggeration perhaps ) instead of the default:
it looks to be the stock Ubuntu default smb.conf file. Since you only have guest shares it's probably OK to leave it that way.


Funny - I didn't change it. My guess was it was installed that way.
I have manually edited it to USER


> One thing interests me:
There's two ways to use Samba to share folders and it sounds like you're using both. Probably not the source of the problem but you never know. Please post the output of the following command:
```
net usershare info --long
```

tony@Acer1810TZ:~$ net usershare info --long
[public]
path=/home/tony/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y


> You might want to find out if all the samba services are running:
```
sudo service smbd restart
``````
sudo service nmbd restart
```

tony@Acer1810TZ:~$ sudo service smbd restart
smbd start/running, process 2796

tony@Acer1810TZ:~$ sudo service nmbd restart
nmbd start/running, process 2806

> Since this is an entirely wireless network I do have a suggestion and that's to alter the name resolution order so that bcast is first not last:
Add a line to the global section of smb.conf:
```
name resolve order = bcast host lmhosts wins
```Then restart smbd again. If it does nothing you can always remove it.
So I found the line in the file, edited the order to your suggestion

.
.
..... drum roll please ......

.. And that fixed it! Thanks a whole bunch!

---

