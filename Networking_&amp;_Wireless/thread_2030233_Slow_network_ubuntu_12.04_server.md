---
title: "Slow network ubuntu 12.04 server"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by samuelW on 2012-07-20
Hello all,

I recently upgraded to ubuntu 12.04. Everything went fine except for one thing....

I use ubuntu 12.04 as server. I have a samba server configured (which worked fine on previous ubuntu versions).  Now it was very very slow.


I did some pings on the server and occasionally the ping requests time out, about 5 to 10 %. I think this is what causing the slow transfers between my server and network.

I use a wired connection and already installed the latest updates, tried to switch cables, etc.

I don't see why... Could you all give me some clue? Suffered from the same problem and found a solution?

Thanks in advance,

Samuel

---

### Post by The Foz on 2012-08-08
I have also started to have problems with performance in the last 2 weeks. I am starting to suspect it is at least partly a Samba problem (I think there may have been a Samba update recently).

I have a server running Ubuntu 10.04. I run a number of services on it: NFS shares for an Ubuntu client, a web server (HTTP & HTTPS), LDAP, FTP, and  Samba for file shares and printing for a Windows 7 client. All these services run fine, at high speed, except Samba, which suddenly started running very slowly recently (around 1.5Mbps - too slow for playing video media).

I have 1Gbps Ethernet, plus a 54Mbps wireless network. The problem occurs whichever network I am using.

I just ran a test using a Windows-XP client in a Virtual Machine (running on the server), and performance is fine, so maybe I am wrong and the problem is on the Windows 7 client.

Here is my smb.conf file:

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

wins support = yes
[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   create mask = 0700
   security = share
   use client driver = yes
   guest ok = yes
   public = yes
   writable = yes

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

```

---

### Post by albandy on 2012-08-08
Can you upload your smb.conf file?

---

### Post by The Foz on 2012-08-08
I have also been looking at [this]("http://ubuntuforums.org/showthread.php?p=12157380#post12157380") thread. The feeling seems to be that it is a problem with the network card driver (makes sense, as I don't get a problem accessing the Samba shares from a VM, thus bypassing the network card).

---

### Post by albandy on 2012-08-08
Try enabling:
socket options = TCP_NODELAY

Do not enable SO_RCVBUF=8192 SO_SNDBUF=8192

---

### Post by The Foz on 2012-08-08
I tried 'socket options = TCP_NODELAY' as suggested (tried both with and without 'SO_RCVBUF=8192 SO_SNDBUF=8192'). I restarted the smbd after each change to the smb.conf file).

There was no noticeable change in performance.

---

### Post by albandy on 2012-08-08
> **The Foz said:**
> I tried 'socket options = TCP_NODELAY' as suggested (tried both with and without 'SO_RCVBUF=8192 SO_SNDBUF=8192'). I restarted the smbd after each change to the smb.conf file).

There was no noticeable change in performance.

please do lspci in the terminal and post the result.

---

### Post by The Foz on 2012-08-08
Here is the output from the 'lspci' command:

```
00:00.0 Host bridge: Intel Corporation 5000V Chipset Memory Controller Hub (rev 92)
00:02.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 2 (rev 92)
00:03.0 PCI bridge: Intel Corporation 5000 Series Chipset PCI Express x4 Port 3 (rev 92)
00:08.0 System peripheral: Intel Corporation 5000 Series Chipset DMA Engine (rev 92)
00:10.0 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 92)
00:10.1 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 92)
00:10.2 Host bridge: Intel Corporation 5000 Series Chipset FSB Registers (rev 92)
00:11.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 92)
00:13.0 Host bridge: Intel Corporation 5000 Series Chipset Reserved Registers (rev 92)
00:15.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 92)
00:16.0 Host bridge: Intel Corporation 5000 Series Chipset FBD Registers (rev 92)
00:1c.0 PCI bridge: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 (rev 09)
00:1d.0 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 (rev 09)
00:1d.1 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 (rev 09)
00:1d.2 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 (rev 09)
00:1d.3 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #4 (rev 09)
00:1d.7 USB Controller: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller (rev 09)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d9)
00:1f.0 ISA bridge: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller (rev 09)
00:1f.1 IDE interface: Intel Corporation 631xESB/632xESB IDE Controller (rev 09)
00:1f.2 IDE interface: Intel Corporation 631xESB/632xESB/3100 Chipset SATA IDE Controller (rev 09)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 21)
02:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port (rev 01)
02:00.3 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge (rev 01)
03:00.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 (rev 01)
03:01.0 PCI bridge: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E2 (rev 01)
07:00.0 VGA compatible controller: ATI Technologies Inc RV620 LE [Radeon HD 3450]
07:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:02.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```

---

### Post by albandy on 2012-08-08
> **The Foz said:**
> Here is the output from the 'lspci' command:

```

[...]
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 21)
[...]

```

As said before, it could be your network card driver.

type this command:

sudo mii-tool

and post the result.

---

### Post by The Foz on 2012-08-08
sudo mii-tool outputs: 
    eth0: negotiated 1000baseT-HD flow-control, link ok

---

### Post by albandy on 2012-08-08
> **The Foz said:**
> sudo mii-tool outputs: 
    eth0: negotiated 1000baseT-HD flow-control, link ok

Its working at half duplex. This is a negotiation problem. Maybe a bug in the driver.

Force it to full duplex with mii-tool:

sudo mii-tool -F 1000baseTx-FD eth0

---

### Post by The Foz on 2012-08-09
I tried your suggestion to set the connection to Full Duplex, but wasn't able to.

'sudo mii-tool -F 1000baseTx-FD eth0 ' gives the error "Invalid media specification '1000baseTx-FD'."

I also tried 'sudo mii-tool -F 1000baseT-FD eth0 ', which gives no error but doesn't change the connection (the command is just ignored). I tried restarting the networking interface, in case the change was pending.

The man page for mii-tool shows the following:
   -F media, --force=media
       Disable  autonegotiation,  and  force the MII to either 
       100baseTx-FD, 100baseTx-HD, 10baseT-FD, or 10baseT-HD 
       operation.

Searching the web, I have found plenty of pages describing the 1000baseTx-FD option, but it seems not to be supported on my system (Ubuntu 10.04).

---

### Post by albandy on 2012-08-09
> **The Foz said:**
> I tried your suggestion to set the connection to Full Duplex, but wasn't able to.

'sudo mii-tool -F 1000baseTx-FD eth0 ' gives the error "Invalid media specification '1000baseTx-FD'."

I also tried 'sudo mii-tool -F 1000baseT-FD eth0 ', which gives no error but doesn't change the connection (the command is just ignored). I tried restarting the networking interface, in case the change was pending.

The man page for mii-tool shows the following:
   -F media, --force=media
       Disable  autonegotiation,  and  force the MII to either 
       100baseTx-FD, 100baseTx-HD, 10baseT-FD, or 10baseT-HD 
       operation.

Searching the web, I have found plenty of pages describing the 1000baseTx-FD option, but it seems not to be supported on my system (Ubuntu 10.04).

Try it at 100baseTx-FD

sudo mii-tool -F 100baseTx-FD eth0

and make some tests.

---

### Post by The Foz on 2012-08-09
I tried 'sudo mii-tool -F 100baseTx-FD eth0'. The first time I got the message "eth0: no link", which seems not good. Further attempts seemed OK,but whatever I tryy to set the connection to, when I check, it is still always "eth0: negotiated 1000baseT-HD flow-control, link ok".

I was wondering whether this problem with mii-tool is a side-effect of me have a bridge (br0, which I use for network access for my virtual machines).

This is the output from 'ifconfig -a':
```
br0       Link encap:Ethernet  HWaddr 00:19:b9:15:73:b5  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe15:73b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72774306 (72.7 MB)  TX bytes:3476197 (3.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:19:b9:15:73:b5  
          inet6 addr: fe80::219:b9ff:fe15:73b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73733931 (73.7 MB)  TX bytes:3876556 (3.8 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16120978 (16.1 MB)  TX bytes:16120978 (16.1 MB)

pan0      Link encap:Ethernet  HWaddr 4e:cc:30:81:62:33  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap0      Link encap:Ethernet  HWaddr 5e:01:d0:75:d5:86  
          inet6 addr: fe80::5c01:d0ff:fe75:d586/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:17617135 (17.6 MB)  TX bytes:48620096 (48.6 MB)


```

---

### Post by albandy on 2012-08-09
> **The Foz said:**
> I tried 'sudo mii-tool -F 100baseTx-FD eth0'. The first time I got the message "eth0: no link", which seems not good. Further attempts seemed OK,but whatever I tryy to set the connection to, when I check, it is still always "eth0: negotiated 1000baseT-HD flow-control, link ok".

I was wondering whether this problem with mii-tool is a side-effect of me have a bridge (br0, which I use for network access for my virtual machines).

This is the output from 'ifconfig -a':
```
br0       Link encap:Ethernet  HWaddr 00:19:b9:15:73:b5  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe15:73b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52535 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72774306 (72.7 MB)  TX bytes:3476197 (3.4 MB)

eth0      Link encap:Ethernet  HWaddr 00:19:b9:15:73:b5  
          inet6 addr: fe80::219:b9ff:fe15:73b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73733931 (73.7 MB)  TX bytes:3876556 (3.8 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:186674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16120978 (16.1 MB)  TX bytes:16120978 (16.1 MB)

pan0      Link encap:Ethernet  HWaddr 4e:cc:30:81:62:33  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap0      Link encap:Ethernet  HWaddr 5e:01:d0:75:d5:86  
          inet6 addr: fe80::5c01:d0ff:fe75:d586/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:17617135 (17.6 MB)  TX bytes:48620096 (48.6 MB)


```

I'm using KVM and VirtualBox in some servers in bridge mode and in bonding mode and have no problems.

Can you try connecting your network card to a 100Mbit switch? 
also can you boot with a previous kernel version?

---

### Post by The Foz on 2012-08-25
As suggested, I tried connecting the server (eth0) to a 100Mbps Ethernet switch (took me a while to find it).

The result is that mii-tool shows: 
eth0: negotiated 100baseTx-FD flow-control, link ok
So the network connection is now running in Full Duplex.

Accessing files via Samba is still slow (too slow for video media); no noticeable difference from the 1000baseT-HD setting).

To be honest, I am not convinced that Half-Duplex versus Full-Duplex should really make much difference when trying to achieve more that 1.5Mbps on a 1Gbps network.

I also noticed that (using 1Gbps) that there are actually problems when accessing files via NFS (not nearly as bad, but video playback keeps pausing for anywhere between 5 and 30 seconds).

Now I will try booting older versions of the Kernel until I find which version introduced the problem.

---

### Post by The Foz on 2012-08-25
I have been doing some tests with older kernel versions (from the GRUB menu).

I found that all older versions have no problems at all with NFS performance, but there seems to be no version that is OK with Samba.

I am working on a workaround which may solve my issues, and may work for some others too. Will report on my success.

---

### Post by The Foz on 2012-08-28
Now I feel a bit embarrassed. I found and fixed my problem: not a software issue at all, but a problem with one of my Ethernet switches (gradually degrading performance, showing up first on Samba services, but then starting to affect other services).

Regarding the work-arounds that I mentioned, because they may be useful for people having real problems with their Saamba service, I tried 2.

1. Add a new Samba service on a VM.

I added a new Virtual Machine using KVM. I suggest that you use an OS version that used to work before getting messed up by updates.

I set up the VM to access the file systems from the host using NFS. During installation, I made sure that I selected not to install updates during installation. Then I shared the necessary file systems using Samba, and mounted them on the Windows client. 

Performance was good. It was easy to set up. Of course, if your host/server is underpowered, performance may not be adequate.

2. Use Streaming.

Pretty much the only files large enough to cause issues for me if Samba is slow are video files. 

I played around with Streaming using VLC until I got something that worked (using RTP streaming). I was able to play videos this way (but it uses LOTS of bandwidth - it may be possible to reduce this by selecting a more optimal transcoding option, but with no transcoding, and also with transcoding to MPEG-2, the network traffic was peaking at 450Mbps).

The main inconvenience is that the player is on the server, so if you want to pause or go back to replay a section, you need to access the server. The easiest solution is to run the server (Streaming source) media player remotely (from the client desktop) using X11 (if playing on a Linux client, this is standard functionality, but with a Windows client you will need to install an X-Server - there are a number of these available, which generally work well).

I hope some of this is useful to some of you.

---

### Post by The Foz on 2013-01-15
Having been forced (by a disc crash) to upgrade my server to 12.04, I now have the slow performance problems that this thread is actually about.

The problem is mostly with Samba services, but even NFS is slow (much faster than Samba, but still not OK for video files).

The issue seems to be that the transfer speed is highly variable changing second by second from acceptable speeds to almost zero.

Has anyone had any success in solving this problem?

---

### Post by droberts on 2013-05-30
I have this too. Upgraded to 12.04 and Samba is essentially non-functional.

---

