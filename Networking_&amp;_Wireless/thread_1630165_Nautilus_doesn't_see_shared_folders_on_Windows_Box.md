---
title: "Nautilus doesn't see shared folders on Windows Box"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2010-11-24
I have a home network consisting of a Desktop running Windows 7 Ultimate and a laptop running Ubuntu 10.10. Nautilus won't allow me to open Windows shared folders from the browser by just clicking on the icons. That is to say, clicking on Network in the bookmark pane and opening Workgroup doesn't do anything. Sometimes I get a "can not mount: failed to retrieve share list from server" error, sometimes my Windows box just isn't visible at all. All my shared folders on the laptop are visible and rw accessible from the Windows desktop.

I should add that if I hit ctrl-L in Nautilus and manually enter "smb://<server-name>/share/" in the address bar, it mounts and opens the specified folder just fine. I have some of the folders already manually mounted to various locations in fstab.

I've found the issue with Games for Windows Live, and uninstalled that from the Windows computer. I'm not using firewalls on either computer for now to eliminate that as a possibility. Since the Ubuntu Laptop seems to be the one with the problem, I'll focus on that for now.
```
$ nc -zv 192.168.1.100 445
Connection to 192.168.1.100 445 port [tcp/microsoft-ds] succeeded!
$ nc -zv 192.168.1.100 139
Connection to 192.168.1.100 139 port [tcp/netbios-ssn] succeeded!
```
I can ping either computer from either computer.  
```
$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_req=1 ttl=128 time=0.762 ms
64 bytes from 192.168.1.100: icmp_req=2 ttl=128 time=0.693 ms
64 bytes from 192.168.1.100: icmp_req=3 ttl=128 time=0.814 ms
64 bytes from 192.168.1.100: icmp_req=4 ttl=128 time=0.793 ms
64 bytes from 192.168.1.100: icmp_req=5 ttl=128 time=0.787 ms
^C
--- 192.168.1.100 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.693/0.769/0.814/0.054 ms

```
If I try smbtree from the Ubuntu box, I get a list of shared folders on the Ubuntu laptop, but not those for the Desktop running windows```

$ smbtree
Enter princess's password: 
WORKGROUP
    \\ZERO-DESKTOP           
    \\PRINCESS-LAPTOP        princess-laptop server (Samba, LinuxMint)
        \\PRINCESS-LAPTOP\desktop            
        \\PRINCESS-LAPTOP\videos             
        \\PRINCESS-LAPTOP\downloads          
        \\PRINCESS-LAPTOP\documents          
        \\PRINCESS-LAPTOP\pictures           
        \\PRINCESS-LAPTOP\Print_to_PDF       Print to a PDF File
        \\PRINCESS-LAPTOP\IPC$               IPC Service (princess-laptop server (Samba, LinuxMint))
        \\PRINCESS-LAPTOP\print$             Printer Drivers

```
If I do a simple *smbclient -L* without specifying a username and entering a password, I get the following error
```
$ smbclient -L //192.168.1.100/
Enter princess's password: 
Domain=[ZERO-DESKTOP] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_NOT_SUPPORTED
session request to 192.168.1.100 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```
however, if I do specify a user and enter the pass when prompted, I get a full list of the available shares
```
$ smbclient -L //192.168.1.100/ -U zero
Enter zero's password: 
Domain=[ZERO-DESKTOP] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
    Desktop         Disk      
    Documents       Disk      
    IPC$            IPC       Remote IPC
    J               Disk      
    L               Disk      
    Music           Disk      
    Pictures        Disk      
    print$          Disk      Printer Drivers
    PSC1200         Printer   hp psc 1200 series
    TV              Disk      
    Users           Disk      
    Videos          Disk      
    zero            Disk      
session request to 192.168.1.100 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available
```
I find that strange, since I've disabled password requirements on the Windows computer, and have enabled read/write access for both Guest and Everyone user accounts. UAC is also disabled.

Since manually entering the address/share in both the Nautilus address bar and the terminal works without the username/password, why should I need it to get a list of shares using the smbclient -L command? Why does Nautilus not see my Windows box at all? Or, if it does, does it either tell me that it can't retrieve the share list, or prompts me endlessly for a username/password combo that shouldn't even be required to access the shares?

Below is a copy of my smb.conf file. Have I missed something there?

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
    workgroup = workgroup

# server string is the equivalent of the NT Description field
    server string = %h server (Samba, LinuxMint)

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
    name resolve order = lmhosts wins bcast host

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
    security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;    encrypt passwords = yes

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
;    guest ok = no
;    guest account = nobody

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
;    guest ok = no
;    read only = yes
    create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
;    browseable = yes
    writeable = yes
    guest ok = yes
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

### Post by capscrew on 2010-11-24
I have no experience with Win7 but the following is of concern```
[COLOR="Red"][B]session request to 192.168.1.100 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available[/B][/COLOR]
```

Generally this means you need to turn on "Windows sharing".  In addition Win7 has added security extra authentication measures that need to be addressed.  Here is a[**_Google search_**]("http://www.google.com/search?q=win7+authentication+with+samba&btnG=Go!")on the topic.

Here is what I get when I use smbclient. All naming is by NetBIOS names.  Note the red below shows the master browser name (kona).  This indicates that NetBIOS over TCP is working.  
```
smbclient -L //rincon
Password:
Domain=[RINCON] OS=[Unix] Server=[Samba 3.0.28a]

        Sharename       Type      Comment
        ---------       ----      -------
        Archive         Disk      Archived Data
        Pictures        Disk      Public Share
        Share           Disk      Public Share
        Backup          Disk      Beachbees Backups
        IPC$            IPC       IPC Service (Storage)
        bruce           Disk      Home Directories
Domain=[RINCON] OS=[Unix] Server=[Samba 3.0.28a]
[COLOR="red"]
        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        BEACHBEES            KONA[/COLOR]

```

---

### Post by detroit/zero on 2010-11-24
Yeah, that's usually what that means. Allow me to reassure you that File & Printer sharing is indeed turned on in the Windows computer.

In fact, if I boot into Windows on the Ubuntu Laptop, file and folder sharing works flawlessly (as would be expected). I should also state that this laptop has been running Jaunty Jackalope for a year, and up until today (after installing the new 10.10), the same shared folders always worked fine.

The fact that I can mount everything manually and in fstab says that file & printer sharing is working. It's clearly a config problem somewhere in Samba or maybe GVFS.

**_EDIT:_ **Just for clarification, it's the Ubuntu Samba Client that can't access the shared folders on the Windows host. I checked out a number of links with that search you provided, and they all seem to be about problems with Windows clients connecting to Samba servers (as one would probably see more of in a corporate or commercial environment) - my problem is the exact opposite.

---

### Post by capscrew on 2010-11-25
There is one thing that seems odd.  Can you explain why you have configured it in a non-deault manner?  

It is 
```
    security = [COLOR="red"]share[/COLOR]
```

This security is no security at all.  Samba leaves it to the underlying OS permissions to authorize use.  There is no authentication of the user. 

I'm not saying you can't do that, I'm just curious as to any situation you are trying to overcome.

 

Let's see what is really going on.  The following should generate lot's of debug information.
```
smbtree -d6
```

You can also do the same for smbclient.
```
smbclient -L //192.168.1.100 -d6

or 

smbclient -L //ZERO-DESKTOP -d6
```

The latter will check netbios configuration.  Both windows and Samba are capable of resolving netbios names.

We can try this [**_Google Search_**]("http://www.google.com/search?q=win7+authentication+with+samba&btnG=Go!#hl=en&expIds=25657,27642,27820&sugexp=ldymls&xhr=t&q=smbclient+with+win7+&cp=20&qe=c21iY2xpZW50IHdpdGggd2luNyA&qesig=FwtNs1wRmOcCAotkZl475w&pkc=AFgZ2tmHxswdSyQslkt4zSlbN9ZJPr62chgzsh-omsxFWRYxmSktK-J2l3QrsJzBaKlnE_HjQv_jmOikZfj8gA8M30QGaGL43g&pf=p&sclient=psy&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=94fb864a6b447b62"), which is more specifically "smbclient to Win7".

---

### Post by detroit/zero on 2010-11-25
> **capscrew said:**
> There is one thing that seems odd.  Can you explain why you have configured it in a non-deault manner?  

It is 
```
    security = [COLOR=red]share[/COLOR]
```This security is no security at all.  Samba leaves it to the underlying OS permissions to authorize use.  There is no authentication of the user. 

I'm not saying you can't do that, I'm just curious as to any situation you are trying to overcome.

 

Let's see what is really going on.  The following should generate lot's of debug information.
```
smbtree -d6
```You can also do the same for smbclient.
```
smbclient -L //192.168.1.100 -d6

or 

smbclient -L //ZERO-DESKTOP -d6
```The latter will check netbios configuration.  Both windows and Samba are capable of resolving netbios names.

We can try this [**_Google Search_**]("http://www.google.com/search?q=win7+authentication+with+samba&btnG=Go%21#hl=en&expIds=25657,27642,27820&sugexp=ldymls&xhr=t&q=smbclient+with+win7+&cp=20&qe=c21iY2xpZW50IHdpdGggd2luNyA&qesig=FwtNs1wRmOcCAotkZl475w&pkc=AFgZ2tmHxswdSyQslkt4zSlbN9ZJPr62chgzsh-omsxFWRYxmSktK-J2l3QrsJzBaKlnE_HjQv_jmOikZfj8gA8M30QGaGL43g&pf=p&sclient=psy&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=94fb864a6b447b62"), which is more specifically "smbclient to Win7".

I was following [Dmizer's Samba Fix tutorial]("http://ubuntuforums.org/showpost.php?p=7341124&postcount=1") when I changed the security setting in smb.conf. It's a recommended step somewhere along the line, and I'm not really that concerned with security.  The same goes for adding *wins* to the resolve order - it was a recommended step somewhere along the line, and it purported to solve something sounding like one of the problems I'm having.

I'll have to pry the wife off that computer for a minute so I can go run those commands and post back the output. In the meantime, I'll go sift through the google search you suggest and see if I can find something I've missed. (Why it doesn't just work right OOTB is something I won't go into).

---

