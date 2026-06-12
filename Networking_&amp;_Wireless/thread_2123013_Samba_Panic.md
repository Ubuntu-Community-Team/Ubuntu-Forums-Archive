---
title: "Samba Panic"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by Hellfire51 on 2013-03-06
I am configuring a Ubuntu 12.04LTS x64 server to use as a home file server. For storage, I created a RAID5 array with mdadm. I then created several folders within the array that are shared via Samba since the rest of my home is Windows 7. 

The problem is that these network shares appear randomly drop off the network and then will reappear after a few seconds. Any in progress network writes, reads etc to or from the share when this happens fail. I don't think it is an underlying networking issue since I am using SSH to configure the server and my session isn't disconnected and I can even run commands while the shares are missing. I thought it might be the array, but I am able to do directory listings and other file activities on the array while this issue occurs.

I am using ufw, but have created a rule 'sudo ufw allow 192.168.0.0/16 to any app Samba' to open Samba access -- regardless, the issue appears to persist whether the firewall is enabled or not.

As part of my configuration, I installed logwatch and started getting the following emails:

```

The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for PID 8606 (/usr/sbin/smbd).

This means there was a problem with the program, such as a segfault.
Below is a backtrace for this process generated with gdb, which shows
the state of the program at the time the error occurred.  The Samba log
files may contain additional information about the problem.

If the problem persists, you are encouraged to first install the
samba-dbg package, which contains the debugging symbols for the Samba
binaries.  Then submit the provided information as a bug report to
Ubuntu by visiting this link:
[https://launchpad.net/ubuntu/+source/samba/+filebug](https://launchpad.net/ubuntu/+source/samba/+filebug)

[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
0x00007f514751843e in waitpid () from /lib/x86_64-linux-gnu/libc.so.6
#0  0x00007f514751843e in waitpid () from /lib/x86_64-linux-gnu/libc.so.6
#1  0x00007f514749e29e in ?? () from /lib/x86_64-linux-gnu/libc.so.6
#2  0x00007f514a8f0bec in smb_panic (why=<optimized out>) at lib/util.c:1123
#3  0x00007f514a63bbe6 in set_unix_security_ctx (uid=1000, gid=1000, ngroups=9, groups=0x7f514c88b900) at smbd/sec_ctx.c:250
#4  0x00007f514a63bf0f in set_sec_ctx (uid=1000, gid=1000, ngroups=9, groups=0x7f514c88b900, token=0x7f514c8798c0) at smbd/sec_ctx.c:320
#5  0x00007f514a62adb5 in change_to_user_internal (conn=0x7f514c895240, session_info=<optimized out>, vuid=100) at smbd/uid.c:304
#6  0x00007f514a652e2b in make_connection_snum (sconn=0x7f514c8765e0, conn=0x7f514c895240, snum=2, vuser=<optimized out>, password=..., pdev=0x7fff0a9b2c20 "?????", pstatus=0x7fff0a9b2dc0) at smbd/service.c:960
#7  0x00007f514a65376e in make_connection_smb1 (sconn=0x7f514c8765e0, snum=2, vuser=0x7f514c87b1b0, password=..., pdev=0x7fff0a9b2c20 "?????", pstatus=0x7fff0a9b2dc0) at smbd/service.c:1127
#8  0x00007f514a653aea in make_connection (sconn=0x7f514c8765e0, service_in=<optimized out>, password=..., pdev=<optimized out>, vuid=<optimized out>, status=0x7fff0a9b2dc0) at smbd/service.c:1323
#9  0x00007f514a60482c in reply_tcon_and_X (req=0x7f514c89c4e0) at smbd/reply.c:796
#10 0x00007f514a64efa4 in switch_message (type=117 'u', req=0x7f514c89c4e0, size=108) at smbd/process.c:1574
#11 0x00007f514a64f3bb in construct_reply (deferred_pcd=0x0, encrypted=false, seqnum=<optimized out>, unread_bytes=0, size=108, inbuf=0x0, sconn=0x7f514c8765e0) at smbd/process.c:1610
#12 process_smb (sconn=0x7f514c8765e0, inbuf=<optimized out>, nread=108, unread_bytes=0, seqnum=<optimized out>, encrypted=false, deferred_pcd=0x0) at smbd/process.c:1688
#13 0x00007f514a64f7d3 in smbd_server_connection_read_handler (conn=0x7f514c8765e0, fd=8) at smbd/process.c:2317
#14 0x00007f514a9008ae in run_events_poll (num_pfds=2, pfds=0x7f514c8803c0, pollrtn=<optimized out>, ev=0x7f514c876520) at lib/events.c:286
#15 run_events_poll (ev=0x7f514c876520, pollrtn=<optimized out>, pfds=0x7f514c8803c0, num_pfds=2) at lib/events.c:184
#16 0x00007f514a650f42 in smbd_server_connection_loop_once (conn=0x7f514c8765e0) at smbd/process.c:1017
#17 smbd_process (sconn=0x7f514c8765e0) at smbd/process.c:3158
#18 0x00007f514ab5e66f in smbd_accept_connection (ev=<optimized out>, fde=<optimized out>, flags=<optimized out>, private_data=<optimized out>) at smbd/server.c:511
#19 0x00007f514a9008ae in run_events_poll (num_pfds=5, pfds=0x7f514c892610, pollrtn=<optimized out>, ev=0x7f514c876520) at lib/events.c:286
#20 run_events_poll (ev=0x7f514c876520, pollrtn=<optimized out>, pfds=0x7f514c892610, num_pfds=5) at lib/events.c:184
#21 0x00007f514a900a4a in s3_event_loop_once (ev=0x7f514c876520, location=<optimized out>) at lib/events.c:349
#22 0x00007f514a9015d0 in _tevent_loop_once (ev=0x7f514c876520, location=0x7f514ad632d7 "smbd/server.c:844") at ../lib/tevent/tevent.c:494
#23 0x00007f514a5cf030 in smbd_parent_loop (parent=<optimized out>) at smbd/server.c:844
#24 main (argc=<optimized out>, argv=<optimized out>) at smbd/server.c:1326
A debugging session is active.

        Inferior 1 [process 8606] will be detached.

```

And finally, below is my smb.conf:
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
   wins support = yes

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
   usershare allow guests = yes

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
   browseable = yes
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
[Videos]
	comment = Videos
	path = /mnt/raid1/videos
	read only = no
	guest ok = yes
	create mask = 755
[Music]
	comment = Music
	path = /mnt/raid1/music
	read only = no
	guest ok = yes
	create mask = 755
[Pictures]
	comment = Pictures & Images
	path = /mnt/raid1/pictures
	read only = no
	guest ok = yes
	create mask = 755
[Documents]
	comment = Documents
	path = /mnt/raid1/documents
	read only = no
	guest ok = yes
	create mask = 755
[Downloads]
	comment = Downloads
	path = /mnt/raid1/downloads
	read only = no
	guest ok = yes
	create mask = 755
[Podcasts]
	comment = Podcasts
	path = /mnt/raid1/podcasts
	read only = no
	guest ok = yes
	create mask = 755
[Backups]
	comment = Backups
	path = /mnt/raid1/backups
	read only = no
	guest ok = yes
	create mask = 755

```

---

### Post by Hellfire51 on 2013-03-06
I think I am answering my own question.

I did some more digging (found the samba logs in /var/log/samba) and found a bunch of errors similar to this:

```

[2013/03/06 18:17:11.304645,  0] lib/util.c:1117(smb_panic)
  PANIC (pid 8704): sys_setgroups failed
[2013/03/06 18:17:11.308707,  0] lib/util.c:1221(log_stack_trace)
  BACKTRACE: 21 stack frames:
   #0 smbd(log_stack_trace+0x1a) [0x7f514a8f0aea]
   #1 smbd(smb_panic+0x25) [0x7f514a8f0bc5]
   #2 smbd(+0x163be6) [0x7f514a63bbe6]
   #3 smbd(set_sec_ctx+0x8f) [0x7f514a63bf0f]
   #4 smbd(+0x152db5) [0x7f514a62adb5]
   #5 smbd(+0x17ae2b) [0x7f514a652e2b]
   #6 smbd(+0x17b76e) [0x7f514a65376e]
   #7 smbd(make_connection+0x1ea) [0x7f514a653aea]
   #8 smbd(reply_tcon_and_X+0x1dc) [0x7f514a60482c]
   #9 smbd(+0x176fa4) [0x7f514a64efa4]
   #10 smbd(+0x1773bb) [0x7f514a64f3bb]
   #11 smbd(+0x1777d3) [0x7f514a64f7d3]
   #12 smbd(run_events_poll+0x34e) [0x7f514a9008ae]
   #13 smbd(smbd_process+0x812) [0x7f514a650f42]
   #14 smbd(+0x68666f) [0x7f514ab5e66f]
   #15 smbd(run_events_poll+0x34e) [0x7f514a9008ae]
   #16 smbd(+0x428a4a) [0x7f514a900a4a]
   #17 smbd(_tevent_loop_once+0x90) [0x7f514a9015d0]
   #18 smbd(main+0xed0) [0x7f514a5cf030]
   #19 /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7f514747a76d]
   #20 smbd(+0xf7515) [0x7f514a5cf515]
[2013/03/06 18:17:11.309005,  0] lib/util.c:1122(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 8704]
[2013/03/06 18:17:11.741966,  0] lib/util.c:1130(smb_panic)
  smb_panic(): action returned status 0
[2013/03/06 18:17:11.742019,  0] lib/fault.c:372(dump_core)
  dumping core in /var/log/samba/cores/smbd

```

Which lead me to this launchpad bug:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1016895](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1016895)

So it sounds like its a known bug that exists in 12.04 and just hasn't had the patch released yet.

---

