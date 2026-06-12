---
title: "Unable to mount location: Failed to retrieve share list from server"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by briangoldberg on 2010-12-19
Hi all,

This is my first post and I know this has been posted before. I'm at my wits end and thus will attempt to post and get an answer. Believe me I would much rather read the posts then post my own.

I installed samba on my ubuntu 10.10. I can now see the files on my windows computer that the ubuntu computer has shared out. One minor thing about that almost every single advice post says to do the following

 sudo /etc/init.d/samba stop  

Which ubuntu says there is no command. That is because there is nothing in /etc/init.d called samba.

Now for the real problem. I can't get ubuntu to see my windows files. This command 

sudo findsmb 

returns nothing even remotely useful

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------


As you can see this rather simple question is turning into a longer post. I can see my windows printer no problem on a different windows computer. That computer is called cpu. The other is called goldberg-pc. Goldberg-pc can see the samba shared files on the ubuntu computer. It was even able to edit those files, which as a tangent to this discussion are actually windows files stored in /host because the ubuntu computer can dual boot to windows xp. The machine called cpu with the printer is windows xp. The computer called goldberg-pc is windows vista.

The following commands also produce some results and some errors. They are included for completeness.

 smbclient -L goldberg-pc
Enter shoshana's password: 
Connection to goldberg-pc failed (Error NT_STATUS_CONNECTION_REFUSED)
shoshana@ubuntu:~$ smbclient -L cpu
Enter shoshana's password: 
Domain=[CPU] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_OK
Domain=[CPU] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------

I also changed my shared folders from public pictures to publicpictures since I'm not sure it is worth the trouble to make ubuntu deal with spaces. Ok that is it. Hit me up with the questions. While I'm at it. I updated /etc/hosts with the ip address of goldberg-pc. And I'm attaching smb.conf on the next post. I have to help my wife in the kitchen now.

---

### Post by Morbius1 on 2010-12-19
> One minor thing about that almost every single advice post says to do the following

 sudo /etc/init.d/samba stop  

Which ubuntu says there is no command.The samba service no longer exists in Ubuntu but has been replaced by it's constituent daemons - smbd and nmbd. So to restart samba today you need to run the following commands:
```
sudo service smbd restart
sudo service nmbd restart
```> Goldberg-pc can see the samba shared files on the ubuntu computer. It  was even able to edit those files, which as a tangent to this discussion  are actually windows files stored in /host because the ubuntu computer  can dual boot to windows xp.So you have a Wubi install - you installed Ubuntu within WinXP. That's not a true dual boot and I have no experience with a Wubi install but I'm going to guess that it shouldn't affect samba or networking in general. But I don't know that for sure.
> I installed samba on my ubuntu 10.10. I can now see the files on my windows computer that the ubuntu computer has shared out. I don't know what that means. You installed Samba and now you can see Windows shares that some other Ubuntu machine has shared? Is the other Ubuntu machine the Wubi install in WinXP?
> And I'm attaching smb.conf on the next post.Since there are two different methods of using Samba to share folders It would be helpful if you also posted the output of this command:
```
sudo net usershare info --long
```

---

### Post by briangoldberg on 2010-12-19
```
shoshana@ubuntu:~$ sudo service smbd restart
smbd start/running, process 18527
shoshana@ubuntu:~$ sudo service smbd restart
smbd start/running, process 18535
shoshana@ubuntu:~$ sudo net usershare info
shoshana@ubuntu:~$ 
```

> Here is what I meant  			 				I installed samba on my ubuntu 10.10. I can now see the files on my  windows computer that the ubuntu computer has shared out.

My computer called goldberg-pc is a windows vista os. Goldberg-pc has shared folders. The computer called ubuntu can't see the goldberg-pc shared folders. 

Now going the other direction, I use samba to share files in ubuntu. Goldberg-pc can see the files on the computer called ubuntu.

---

### Post by briangoldberg on 2010-12-19
Since so many people follow up on their problems I thought I would too. I didn't realize that I wasn't restarting my samba all this time until the post below. So here is some new information.
```
shoshana@ubuntu:~$ sudo net usershare info
shoshana@ubuntu:~$ smbclient -L goldberg-pc
Enter shoshana's password: 
Connection to goldberg-pc failed (Error NT_STATUS_CONNECTION_REFUSED)
shoshana@ubuntu:~$ smbclient -L cpu
Enter shoshana's password: 
session setup failed: NT_STATUS_REQUEST_NOT_ACCEPTED
shoshana@ubuntu:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.66    UBUNTU         [WORKGROUP] [Unix] [Samba 3.5.4]
```So some progress and some minor drama. I couldn't see the ubuntu files with the interfaces line and the line below. I recommented them out and restarted. Now I can see the ubuntu files while on Windows again, yeah back to where I was 24 hours ago. 

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
    netbios name = ubuntu

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
;    interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;    bind interfaces only = yes



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
    encrypt passwords = yes

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
[homes]
   comment = Home Directories
   browseable = no

#My share drive
[Myshare]
    comment = Myshare
    path = /host/Documents and Settings/karol danowitz/My Documents/My Pictures
    read only = no
    guest ok = yes
[Myshare2]
    comment = Myshare2
    path = /host/Documents and Settings/karol danowitz/My Documents/My Videos
    read only = no
    guest ok = yes
# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.

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
```Attached is a screenshot of network. Now I can see the workgroups of both windows computers but that is it. Can't see the shared files, yet.

---

### Post by capscrew on 2010-12-19
> **briangoldberg said:**
> ...

Now I can see the workgroups of both windows computers but that is it. Can't see the shared files, yet.

So at this point let's try to see what is really going on.  We can up the Samba debugging and see what shares are available with this command from the CLI. ```
smbtree -d6
```

Please post your results.

---

### Post by briangoldberg on 2010-12-20
Thanks Morbius1 and capscrew. 
 
When I get home I'll try this command and post the results.
 
smbtree -d6
 
What is a CLI? 
 
In other news, on the network window in ubunutu I tried open as folder with success but thats it. So I'll post that screen shot as well. 
 
I'm doing this in hopes to help someone else. Good luck McMichael. I found by taking the time to post, I've solved some of my problem. 
 
Restarting samba made a big difference. As a mattter of fact, since I added ubuntu to /etc/hosts, my goldberg-pc which is windows vista can see ubuntu as a machine in my network as well as the windows xp machine called cpu. It is possible that adding the netbios name to the /etc/samba/smb.conf is what did it. I'll never know for sure. I can only do so many experiments.
 
My guess is I'm really close and need some kind of mount at smbclient -i cfis command. But I'm out of patience so hoping for some help here.

---

### Post by capscrew on 2010-12-20
> **briangoldberg said:**
> Thanks Morbius1 and capscrew. 
 
When I get home I'll try this command and post the results.
 
smbtree -d6
 
What is a CLI? 
 
In other news, on the network window in ubunutu I tried open as folder with success but thats it. So I'll post that screen shot as well. 
 
I'm doing this in hopes to help someone else. Good luck McMichael. I found by taking the time to post, I've solved some of my problem. 
 
Restarting samba made a big difference. As a mattter of fact, since I added ubuntu to /etc/hosts, my goldberg-pc which is windows vista can see ubuntu as a machine in my network as well as the windows xp machine called cpu. It is possible that adding the netbios name to the /etc/samba/smb.conf is what did it. I'll never know for sure. I can only do so many experiments.
 
My guess is I'm really close and need some kind of mount at smbclient -i cfis command. But I'm out of patience so hoping for some help here.

Glad to see you have sort of solved your immediate problem.  The method of adding the hostname to the /etc/hosts file works as long as the IP address stays the same.  If it changes then the mapping between the IP address and hostname is lost and your right back to where you were before.  Are you using static or reserved (via DHCP) IP addressing?

Indeed your problem was one of finding the NetBIOS name.  No you can't add a NetBIOS name to the /etc/hosts file.  Samba will use the hostname as the NetBIOS name if you don't declare the NETBIOS name at all.

It is best to do one change and then test at a time.  That way you will know what fixed the problem.  Sometimes that is hard to do.  :D

---

### Post by briangoldberg on 2010-12-20
>  
So at this point let's try to see what is really going on. We can up the Samba debugging and see what shares are available with this command from the CLI. 
 
What is the CLI? 
 
I added ubuntu to the /etc/hosts file and to the /etc/samba/smb.conf files. Are you saying if I take both of those out goldberg-pc will still recognize the machine name in windows vista under network places? I'll send in a windows screen shot too, when I get back to my computers. And as you suggested try one experiment at a time.
 
However, I still can't see the goldberg-pc files on the ubuntu computer. And there is nothing you can do to help until I post the smbtree. So bye for now.

---

### Post by capscrew on 2010-12-20
> **briangoldberg said:**
> What is the CLI? 

CLI = Command Line Interface (e.g. The terminal)> 
 
I added ubuntu to the /etc/hosts file and to the /etc/samba/smb.conf files. 

Hmmm, both eh?  The /etc/hosts file maps hostnames to IP addresses.  I assume you... nope, I should not assume.  How did you add "ubuntu" to the smb.conf file?

You can declare the NetBIOS name in the **global** section of the smb.conf file using the  following. ```
netbios name = <MACHINE_NAME>
```
> 

Are you saying if I take both of those out goldberg-pc will still recognize the machine name in windows vista under network places? 

All Windows (i.e. XP, Vista, Win7) hosts broadcast their NetBIOS names on the LAN.  A Samba Server can also do this.  Samba does it a little differently but the result is the same (e.g. all NetBIOS names will be b'cast).  Without getting to technical this is the list (Master Browse List) that Samba grumps about when it can't retrieve it.  You can't visually browse the shares without there being a Master Browser and the Master Browse List.> 

I'll send in a windows screen shot too, when I get back to my computers. And as you suggested try one experiment at a time.

Believe it or not the pictures don't help me in the diagnoses.  The output from the debug is more enlightening to me.  But if it makes you feel better and/or it helps our audience then do it.  :-) > 
 
However, I still can't see the goldberg-pc files on the ubuntu computer. And there is nothing you can do to help until I post the smbtree. So bye for now.

One thing that would help is to place the debug output between the *code (#)* brackets rather than a text file.  See ya later.

---

### Post by briangoldberg on 2010-12-20
```
shoshana@ubuntu:~$ cat /etc/hosts
192.168.1.254   goldberg-pc
192.168.1.66    ubuntu    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    ubuntu    localhost6.localdomain6    localhost6
127.0.1.1    ubuntu.ubuntu-domain    ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
shoshana@ubuntu:~$ cat /etc/samba/smb.conf | grep ubuntu
    netbios name = ubuntu
shoshana@ubuntu:~$ smbtree -d6 > debug_out.txt
Enter shoshana's password: 
shoshana@ubuntu:~$ 
```I made a mistake. I put goldberg-pc in the /etc/hosts file ubuntu was placed in there all by itself. 

How do I determine if

> .  Are you using static or reserved (via DHCP) IP addressing?below is the contents of the smbtree -d6

```
INFO: Current debug levels:
  all: True/6
  tdb: False/0
  printdrivers: False/0
  lanman: False/0
  smb: False/0
  rpc_parse: False/0
  rpc_srv: False/0
  rpc_cli: False/0
  passdb: False/0
  sam: False/0
  auth: False/0
  winbind: False/0
  vfs: False/0
  idmap: False/0
  quota: False/0
  acls: False/0
  locking: False/0
  msdfs: False/0
  dmapi: False/0
  registry: False/0
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = workgroup
doing parameter netbios name = ubuntu
handle_netbios_name: set global_myname to: UBUNTU
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter security = share
doing parameter encrypt passwords = yes
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
Attempting to register new charset UCS-2LE
Registered charset UCS-2LE
Attempting to register new charset UTF-16LE
Registered charset UTF-16LE
Attempting to register new charset UCS-2BE
Registered charset UCS-2BE
Attempting to register new charset UTF-16BE
Registered charset UTF-16BE
Attempting to register new charset UTF8
Registered charset UTF8
Attempting to register new charset UTF-8
Registered charset UTF-8
Attempting to register new charset ASCII
Registered charset ASCII
Attempting to register new charset 646
Registered charset 646
Attempting to register new charset ISO-8859-1
Registered charset ISO-8859-1
Attempting to register new charset UCS2-HEX
Registered charset UCS2-HEX
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
added interface eth1 ip=fe80::219:7dff:fe28:8723%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.66 bcast=192.168.1.255 netmask=255.255.255.0
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/run/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
no entry for WORKGROUP#1D found.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_hosts: not appropriate for name type <0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 114688
    SO_RCVBUF = 114688
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
Sending a packet of len 50 to (192.168.1.255) on port 137
Received a packet of len 62 from (192.168.1.67) port 137
nmb packet from 192.168.1.67(137) header: id=9805 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....C   hex 0000C0A80143
Got a positive name query response from 192.168.1.67 ( 192.168.1.67 )
namecache_store: storing 1 address for WORKGROUP#1d: 192.168.1.67
Connecting to host=192.168.1.67
Connecting to 192.168.1.67 at port 445
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 0
    SO_BROADCAST = 0
    TCP_NODELAY = 1
    TCP_KEEPCNT = 9
    TCP_KEEPIDLE = 7200
    TCP_KEEPINTVL = 75
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 16384
    SO_RCVBUF = 87380
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Doing spnego session setup (blob length=46)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
write_socket(4,166)
write_socket(4,166) wrote 166
size=440
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=  440 (0x1B8)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  229 (0xE5)
smb_bcc=397
size=440
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=  440 (0x1B8)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  229 (0xE5)
smb_bcc=397
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP challenge set by NTLM2
challenge is: 
[0000] E3 C7 E1 65 71 13 C6 B7                            ...eq... 
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
write_socket(4,272)
write_socket(4,272) wrote 272
size=35
smb_com=0x73
smb_rcls=109
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=3
smt_wct=0
smb_bcc=0
size=35
smb_com=0x73
smb_rcls=109
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=3
smt_wct=0
smb_bcc=0
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 114688
    SO_RCVBUF = 114688
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
Sending a packet of len 50 to (192.168.1.255) on port 137
Received a packet of len 62 from (192.168.1.67) port 137
nmb packet from 192.168.1.67(137) header: id=621 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....C   hex 8000C0A80143
Got a positive name query response from 192.168.1.67 ( 192.168.1.67 )
Received a packet of len 62 from (192.168.1.65) port 137
nmb packet from 192.168.1.65(137) header: id=621 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....A   hex 8000C0A80141
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
namecache_status_fetch: no entry for NBT/*#00.1D.192.168.1.67 found.
Sending a packet of len 50 to (192.168.1.67) on port 137
Received a packet of len 211 from (192.168.1.67) port 137
nmb packet from 192.168.1.67(137) header: id=23557 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .GOLDBERG-PC       hex 06474F4C44424552472D504320202020
    answers  10 char ...WORKGROUP       hex 000400574F524B47524F555020202020
    answers  20 char   ...WORKGROUP     hex 2020008400574F524B47524F55502020
    answers  30 char     ...GOLDBERG-   hex 202020201E8400474F4C44424552472D
    answers  40 char PC     ..WORKGRO   hex 504320202020200400574F524B47524F
    answers  50 char UP      .....__M   hex 55502020202020201D040001025F5F4D
    answers  60 char SBROWSE__......s   hex 5342524F5753455F5F02018400001A73
    answers  70 char ................   hex 15C5D700000000000000000000000000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ...........   hex 0000000000000000000000
namecache_status_store: entry NBT/*#00.1D.192.168.1.67 store failed.
no entry for WORKGROUP#1D found.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_hosts: not appropriate for name type <0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 114688
    SO_RCVBUF = 114688
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
Sending a packet of len 50 to (192.168.1.255) on port 137
Received a packet of len 62 from (192.168.1.67) port 137
nmb packet from 192.168.1.67(137) header: id=15693 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....C   hex 0000C0A80143
Got a positive name query response from 192.168.1.67 ( 192.168.1.67 )
namecache_store: storing 1 address for WORKGROUP#1d: 192.168.1.67
found master browser WORKGROUP, 192.168.1.67
Connecting to host=192.168.1.67
Connecting to 192.168.1.67 at port 445
Connecting to 192.168.1.67 at port 139
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 0
    SO_BROADCAST = 0
    TCP_NODELAY = 1
    TCP_KEEPCNT = 9
    TCP_KEEPIDLE = 7200
    TCP_KEEPINTVL = 75
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 16384
    SO_RCVBUF = 87380
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
Doing spnego session setup (blob length=46)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
write_socket(8,166)
write_socket(8,166) wrote 166
size=440
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=  440 (0x1B8)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  229 (0xE5)
smb_bcc=397
size=440
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=  440 (0x1B8)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  229 (0xE5)
smb_bcc=397
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP challenge set by NTLM2
challenge is: 
[0000] D5 C6 54 6E 6A 7D 7C 72                            ..Tnj}|r 
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
write_socket(8,272)
write_socket(8,272) wrote 272
size=35
smb_com=0x73
smb_rcls=109
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=3
smt_wct=0
smb_bcc=0
size=35
smb_com=0x73
smb_rcls=109
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=3
smt_wct=0
smb_bcc=0
SPNEGO login failed: Logon failure
size=126
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=8
smb_flg2=51201
smb_tid=2048
smb_pid=1998
smb_uid=2049
smb_mid=6
smt_wct=14
smb_vwv[ 0]=   36 (0x24)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    8 (0x8)
smb_vwv[ 3]=65535 (0xFFFF)
smb_vwv[ 4]=    0 (0x0)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=    0 (0x0)
smb_vwv[ 7]=    0 (0x0)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=   36 (0x24)
smb_vwv[10]=   90 (0x5A)
smb_vwv[11]=    0 (0x0)
smb_vwv[12]=  126 (0x7E)
smb_vwv[13]=    0 (0x0)
smb_bcc=63
write_socket(8,130)
write_socket(8,130) wrote 130
size=132
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=1998
smb_uid=2049
smb_mid=6
smt_wct=10
smb_vwv[ 0]=    8 (0x8)
smb_vwv[ 1]=   68 (0x44)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    8 (0x8)
smb_vwv[ 4]=   56 (0x38)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=   68 (0x44)
smb_vwv[ 7]=   64 (0x40)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=    0 (0x0)
smb_bcc=77
size=132
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=1998
smb_uid=2049
smb_mid=6
smt_wct=10
smb_vwv[ 0]=    8 (0x8)
smb_vwv[ 1]=   68 (0x44)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    8 (0x8)
smb_vwv[ 4]=   56 (0x38)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=   68 (0x44)
smb_vwv[ 7]=   64 (0x40)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=    0 (0x0)
smb_bcc=77
WORKGROUP
no entry for WORKGROUP#1D found.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_hosts: not appropriate for name type <0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 114688
    SO_RCVBUF = 114688
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
Sending a packet of len 50 to (192.168.1.255) on port 137
Received a packet of len 62 from (192.168.1.67) port 137
nmb packet from 192.168.1.67(137) header: id=10577 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....C   hex 0000C0A80143
Got a positive name query response from 192.168.1.67 ( 192.168.1.67 )
namecache_store: storing 1 address for WORKGROUP#1d: 192.168.1.67
Connecting to host=192.168.1.67
Connecting to 192.168.1.67 at port 445
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 0
    SO_BROADCAST = 0
    TCP_NODELAY = 1
    TCP_KEEPCNT = 9
    TCP_KEEPIDLE = 7200
    TCP_KEEPINTVL = 75
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 16384
    SO_RCVBUF = 87380
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
Doing spnego session setup (blob length=46)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=<null>
write_socket(9,166)
write_socket(9,166) wrote 166
size=440
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=  440 (0x1B8)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  229 (0xE5)
smb_bcc=397
size=440
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=  440 (0x1B8)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  229 (0xE5)
smb_bcc=397
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP challenge set by NTLM2
challenge is: 
[0000] E5 8B 29 81 7A 1E 23 FC                            ..).z.#. 
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
write_socket(9,272)
write_socket(9,272) wrote 272
size=35
smb_com=0x73
smb_rcls=109
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=3
smt_wct=0
smb_bcc=0
size=35
smb_com=0x73
smb_rcls=109
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=2048
smb_mid=3
smt_wct=0
smb_bcc=0
SPNEGO login failed: Logon failure
size=126
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=8
smb_flg2=51201
smb_tid=2048
smb_pid=1998
smb_uid=2049
smb_mid=6
smt_wct=14
smb_vwv[ 0]=   36 (0x24)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    8 (0x8)
smb_vwv[ 3]=65535 (0xFFFF)
smb_vwv[ 4]=    0 (0x0)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=    0 (0x0)
smb_vwv[ 7]=    0 (0x0)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=   36 (0x24)
smb_vwv[10]=   90 (0x5A)
smb_vwv[11]=    0 (0x0)
smb_vwv[12]=  126 (0x7E)
smb_vwv[13]=    0 (0x0)
smb_bcc=63
write_socket(9,130)
write_socket(9,130) wrote 130
size=147
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=1998
smb_uid=2049
smb_mid=6
smt_wct=10
smb_vwv[ 0]=    8 (0x8)
smb_vwv[ 1]=   83 (0x53)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    8 (0x8)
smb_vwv[ 4]=   56 (0x38)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=   83 (0x53)
smb_vwv[ 7]=   64 (0x40)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=    0 (0x0)
smb_bcc=92
size=147
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=1998
smb_uid=2049
smb_mid=6
smt_wct=10
smb_vwv[ 0]=    8 (0x8)
smb_vwv[ 1]=   83 (0x53)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    8 (0x8)
smb_vwv[ 4]=   56 (0x38)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=   83 (0x53)
smb_vwv[ 7]=   64 (0x40)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=    0 (0x0)
smb_bcc=92
    \\UBUNTU                 
Connecting to host=UBUNTU
sitename_fetch: No stored sitename for 
no entry for UBUNTU#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name UBUNTU<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name UBUNTU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name UBUNTU<0x20>
namecache_store: storing 3 addresses for UBUNTU#20: 127.0.0.1,127.0.1.1,192.168.1.66
Connecting to 127.0.0.1 at port 445
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 0
    SO_BROADCAST = 0
    TCP_NODELAY = 1
    TCP_KEEPCNT = 9
    TCP_KEEPIDLE = 7200
    TCP_KEEPINTVL = 75
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 50724
    SO_RCVBUF = 87552
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
write_socket(10,140)
write_socket(10,140) wrote 140
size=96
smb_com=0x73
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=49155
smb_tid=0
smb_pid=1998
smb_uid=0
smb_mid=2
smt_wct=3
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    1 (0x1)
smb_bcc=55
size=96
smb_com=0x73
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=49155
smb_tid=0
smb_pid=1998
smb_uid=0
smb_mid=2
smt_wct=3
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    1 (0x1)
smb_bcc=55
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
    \\GOLDBERG-PC            
Connecting to host=GOLDBERG-PC
sitename_fetch: No stored sitename for 
no entry for GOLDBERG-PC#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name GOLDBERG-PC<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name GOLDBERG-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name GOLDBERG-PC<0x20>
namecache_store: storing 1 address for GOLDBERG-PC#20: 192.168.1.254
Connecting to 192.168.1.254 at port 445
Connecting to 192.168.1.254 at port 139
Error connecting to 192.168.1.254 (Connection refused)
cli_start_connection: failed to connect to GOLDBERG-PC<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
MSHOME
no entry for MSHOME#1D found.
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_hosts: not appropriate for name type <0x1d>
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 114688
    SO_RCVBUF = 114688
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
Sending a packet of len 50 to (192.168.1.255) on port 137
Received a packet of len 62 from (192.168.1.65) port 137
nmb packet from 192.168.1.65(137) header: id=11892 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=MSHOME<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....A   hex 0000C0A80141
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
namecache_store: storing 1 address for MSHOME#1d: 192.168.1.65
Connecting to host=192.168.1.65
Connecting to 192.168.1.65 at port 445
Connecting to 192.168.1.65 at port 139
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 0
    SO_BROADCAST = 0
    TCP_NODELAY = 1
    TCP_KEEPCNT = 9
    TCP_KEEPIDLE = 7200
    TCP_KEEPINTVL = 75
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 16384
    SO_RCVBUF = 87380
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
write_socket(10,166)
write_socket(10,166) wrote 166
size=260
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=16387
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=  260 (0x104)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  143 (0x8F)
smb_bcc=217
size=260
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=16387
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=  260 (0x104)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  143 (0x8F)
smb_bcc=217
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP challenge set by NTLM2
challenge is: 
[0000] D3 06 BB 47 E5 B9 A8 EC                            ...G.... 
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
write_socket(10,272)
write_socket(10,272) wrote 272
size=35
smb_com=0x73
smb_rcls=208
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=16387
smb_mid=3
smt_wct=0
smb_bcc=0
size=35
smb_com=0x73
smb_rcls=208
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=16387
smb_mid=3
smt_wct=0
smb_bcc=0
SPNEGO login failed: NT_STATUS_REQUEST_NOT_ACCEPTED
size=123
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=8
smb_flg2=51201
smb_tid=8196
smb_pid=1998
smb_uid=18433
smb_mid=6
smt_wct=14
smb_vwv[ 0]=   33 (0x21)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    8 (0x8)
smb_vwv[ 3]=65535 (0xFFFF)
smb_vwv[ 4]=    0 (0x0)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=    0 (0x0)
smb_vwv[ 7]=    0 (0x0)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=   33 (0x21)
smb_vwv[10]=   90 (0x5A)
smb_vwv[11]=    0 (0x0)
smb_vwv[12]=  123 (0x7B)
smb_vwv[13]=    0 (0x0)
smb_bcc=60
write_socket(10,127)
write_socket(10,127) wrote 127
size=104
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=8196
smb_pid=1998
smb_uid=18433
smb_mid=6
smt_wct=10
smb_vwv[ 0]=    8 (0x8)
smb_vwv[ 1]=   40 (0x28)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    8 (0x8)
smb_vwv[ 4]=   56 (0x38)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=   40 (0x28)
smb_vwv[ 7]=   64 (0x40)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=    0 (0x0)
smb_bcc=49
size=104
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=8196
smb_pid=1998
smb_uid=18433
smb_mid=6
smt_wct=10
smb_vwv[ 0]=    8 (0x8)
smb_vwv[ 1]=   40 (0x28)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    8 (0x8)
smb_vwv[ 4]=   56 (0x38)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=   40 (0x28)
smb_vwv[ 7]=   64 (0x40)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=    0 (0x0)
smb_bcc=49
    \\CPU                    Downstairs PC
Connecting to host=CPU
sitename_fetch: No stored sitename for 
no entry for CPU#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name CPU<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name CPU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name CPU<0x20>
namecache_store: storing 1 address for CPU#20: 192.168.1.65
Connecting to 192.168.1.65 at port 445
Connecting to 192.168.1.65 at port 139
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 0
    SO_BROADCAST = 0
    TCP_NODELAY = 1
    TCP_KEEPCNT = 9
    TCP_KEEPIDLE = 7200
    TCP_KEEPINTVL = 75
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 16384
    SO_RCVBUF = 87380
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
write_socket(11,166)
write_socket(11,166) wrote 166
size=260
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=16386
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=  260 (0x104)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  143 (0x8F)
smb_bcc=217
size=260
smb_com=0x73
smb_rcls=22
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=16386
smb_mid=2
smt_wct=4
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=  260 (0x104)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=  143 (0x8F)
smb_bcc=217
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP challenge set by NTLM2
challenge is: 
[0000] B5 7A B8 27 BC A1 7A 8A                            .z.'..z. 
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
write_socket(11,272)
write_socket(11,272) wrote 272
size=35
smb_com=0x73
smb_rcls=208
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=16386
smb_mid=3
smt_wct=0
smb_bcc=0
size=35
smb_com=0x73
smb_rcls=208
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=0
smb_pid=1998
smb_uid=16386
smb_mid=3
smt_wct=0
smb_bcc=0
SPNEGO login failed: NT_STATUS_REQUEST_NOT_ACCEPTED
size=109
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=8
smb_flg2=51201
smb_tid=8196
smb_pid=1998
smb_uid=16387
smb_mid=7
smt_wct=14
smb_vwv[ 0]=   19 (0x13)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]= 1024 (0x400)
smb_vwv[ 3]=65504 (0xFFE0)
smb_vwv[ 4]=    0 (0x0)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=    0 (0x0)
smb_vwv[ 7]=    0 (0x0)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=   19 (0x13)
smb_vwv[10]=   90 (0x5A)
smb_vwv[11]=    0 (0x0)
smb_vwv[12]=  109 (0x6D)
smb_vwv[13]=    0 (0x0)
smb_bcc=46
write_socket(11,113)
write_socket(11,113) wrote 113
size=35
smb_com=0x25
smb_rcls=34
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=8196
smb_pid=1998
smb_uid=16387
smb_mid=7
smt_wct=0
smb_bcc=0
size=35
smb_com=0x25
smb_rcls=34
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=8196
smb_pid=1998
smb_uid=16387
smb_mid=7
smt_wct=0
smb_bcc=0
NetShareEnum failed
```

---

### Post by capscrew on 2010-12-20
How did you configure the IP addresses of the various hosts.  On the Linux hosts you can use the command:```
ifconfig -a
```

On the Windows hosts you can issue this command from the command line (Start>>Run>>CMD):```
ipconfig /all
```

I would say that if you don't know then most likely you are using the router as a DHCP server for you LAN.

Edit:  It appears that the host CPU is not in the same workgroup as the others (MSHOME) and the command smbtree fails with this ```
NetShareEnum failed
```

The others are working fine.  Maybe if you add CPU to the /etc/hosts file for now.

---

### Post by briangoldberg on 2010-12-21
All I can do right now is agree CPU is on a different workgroup. Below are the results of the command. Thanks for helping me so far.
```
eth0      Link encap:Ethernet  HWaddr 00:19:b9:4c:8d:c5  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:19:7d:28:87:23  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7dff:fe28:8723/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:130176 errors:0 dropped:0 overruns:0 frame:92900
          TX packets:142048 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59765768 (59.7 MB)  TX bytes:131728163 (131.7 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13149 (13.1 KB)  TX bytes:13149 (13.1 KB)

```

---

### Post by capscrew on 2010-12-21
> **briangoldberg said:**
> All I can do right now is agree CPU is on a different workgroup.

If you are happy with the setup then I am too.  If not, I have three observations:

[LIST=1]
[*]The host CPU can be in a different work group. At this point it is just a neatness thing.

[*]The *"NetShareEnum failed" * is a fatal error as far as **smbtree **is concerned.

[*]We still have the IP address configuration method to check out.
[/LIST]

I noticed that you have set *security = share *in the smb.conf file.  This disables the user security.  Did you do this to overcome user login problems?

Are you using Network manager to configure your network connections?

---

### Post by briangoldberg on 2010-12-21
Below is the results of ipconfig /all from the cpu computer
```
  
Windows IP Configuration  
  
        Host Name . . . . . . . . . . . . : CPU  
        Primary Dns Suffix  . . . . . . . :   
        Node Type . . . . . . . . . . . . : Broadcast  
        IP Routing Enabled. . . . . . . . : No  
        WINS Proxy Enabled. . . . . . . . : No  
        DNS Suffix Search List. . . . . . : gateway.2wire.net  
  
Ethernet adapter Local Area Connection:  
  
        Media State . . . . . . . . . . . : Media disconnected  
        Description . . . . . . . . . . . : SiS 900-Based PCI Fast Ethernet Adapter  
        Physical Address. . . . . . . . . : 00-0A-E6-07-75-2E  
  
Ethernet adapter Local Area Connection 5:  
  
        Connection-specific DNS Suffix  . : gateway.2wire.net  
        Description . . . . . . . . . . . : 2Wire Gateway USB #3  
        Physical Address. . . . . . . . . : 00-1E-C7-3B-EF-DA  
        Dhcp Enabled. . . . . . . . . . . : Yes  
        Autoconfiguration Enabled . . . . : Yes  
        IP Address. . . . . . . . . . . . : 192.168.1.65  
        Subnet Mask . . . . . . . . . . . : 255.255.255.0  
        Default Gateway . . . . . . . . . : 192.168.1.254  
        DHCP Server . . . . . . . . . . . : 192.168.1.254  
        DNS Servers . . . . . . . . . . . : 192.168.1.254  
        Lease Obtained. . . . . . . . . . : Tuesday, December 21, 2010 3:27:02 PM  
        Lease Expires . . . . . . . . . . : Wednesday, December 22, 2010 3:27:02 PM 
```

---

### Post by briangoldberg on 2010-12-21
I still have to do an ipconfig /all on the other computer

> If you are happy with the setup then I am too.  If not, I have three observations:

I'll be happy when I can see windows files on my ubuntu.
> The host CPU can be in a different work group. At this point it is just a neatness thing.
The *"NetShareEnum failed" * is a fatal error as far as **smbtree **is concerned.
How do I fix this?

> I noticed that you have set *security = share *in the smb.conf file.  This disables the user security.  Did you do this to overcome user login problems?

No clue

> Are you using Network manager to configure your network connections?

No clue

---

### Post by briangoldberg on 2010-12-21
this is the last thing I can post until you ask me any more questions. Below is the ipconfig /all from the goldberg-pc.
 
Not to ask too many windows questions, but the computer called cpu is windows xp and it can't see the computer called goldberg-pc that is windows vista. Both windows computers can see the ubuntu computer
```
 

Windows IP Configuration
   Host Name . . . . . . . . . . . . : Goldberg-PC
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Broadcast
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : gateway.2wire.net
Ethernet adapter Local Area Connection* 14:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Check Point Virtual Network Adapter For SecureClient
   Physical Address. . . . . . . . . : 54-39-63-55-5E-0F
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Wireless LAN adapter Wireless Network Connection:
   Connection-specific DNS Suffix  . : gateway.2wire.net
   Description . . . . . . . . . . . : Broadcom 802.11b/g WLAN
   Physical Address. . . . . . . . . : 00-1A-73-15-C5-D7
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::3c04:6ef1:f14e:264c%9(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.1.67(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Tuesday, December 21, 2010 8:01:40 PM
   Lease Expires . . . . . . . . . . : Wednesday, December 22, 2010 8:01:40 PM
   Default Gateway . . . . . . . . . : 192.168.1.254
   DHCP Server . . . . . . . . . . . : 192.168.1.254
   DNS Servers . . . . . . . . . . . : 192.168.1.254
   NetBIOS over Tcpip. . . . . . . . : Enabled
Ethernet adapter Local Area Connection:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
   Physical Address. . . . . . . . . : 00-16-D4-B9-A2-BC
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Local Area Connection* 7:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : isatap.comcast.net
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Local Area Connection* 9:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


```

---

### Post by capscrew on 2010-12-21
> **briangoldberg said:**
> this is the last thing I can post until you ask me any more questions. Below is the ipconfig /all from the goldberg-pc.

How about the output from the Linux (Ubuntu) hosts ```
cat /etc/network/interfaces
```> 
 
Not to ask too many windows questions, but the computer called cpu is windows xp and it can't see the computer called goldberg-pc that is windows vista. Both windows computers can see the ubuntu computer

Probably the authentication problem I spoke of earlier.  > 

```
 

Windows IP Configuration
   Host Name . . . . . . . . . . . . : Goldberg-PC
 ...
 [COLOR="Red"][B]  DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
[/B][/COLOR]
...

[COLOR="red"]**   DHCP Server . . . . . . . . . . . : 192.168.1.254**[/COLOR]
   DNS Servers . . . . . . . . . . . : 192.168.1.254
   NetBIOS over Tcpip. . . . . . . . : Enabled
Ethernet adapter Local Area Connection:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
   Physical Address. . . . . . . . . : 00-16-D4-B9-A2-BC
[COLOR="Red"]**   DHCP Enabled. . . . . . . . . . . : Yes**[/COLOR]
   Autoconfiguration Enabled . . . . : Yes
...

```

This Windows host uses DHCP to configure the IP address (see red above).  This means you can loose the IP to name mapping in the /etc/hosts files.

---

### Post by briangoldberg on 2010-12-21
here is the results of cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

```

---

### Post by capscrew on 2010-12-22
> **briangoldberg said:**
> here is the results of cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

```

This shows me that the LAN interface for this host is managed by Network Manager or WICD.  Either way, it appears that your network IP addressing is handled by DHCP.  

Therefore you can't entirely rely on using the /etc/hosts mapping of hostnames to IP addressing due to the fact that DHCP can swap the IP addressing around.

You have said it is working right now.  I will leave it to you to decide what you want to do at this point.

---

### Post by briangoldberg on 2010-12-22
I'm still getting "**Unable to mount location: Failed to retrieve share list from server" error.**
 
**I can't see the windows files while logged into ubuntu. When I click on network, then workgroup,  the message appears above. So, capscrew if you can help that would be great.**
 
**The only thing working is that samba allows windows to see the ubuntu files, but not the other way around.**
 
**Ubuntu can't see the windows files.**

---

### Post by capscrew on 2010-12-22
> **briangoldberg said:**
> I'm still getting "**Unable to mount location: Failed to retrieve share list from server" error.**
 
**I can't see the windows files while logged into ubuntu. When I click on network, then workgroup,  the message appears above. So, capscrew if you can help that would be great.**
 
**The only thing working is that samba allows windows to see the ubuntu files, but not the other way around.**
 
**Ubuntu can't see the windows files.**

Except for the title of this thread we have not seen any output that displays **"Unable to mount location: Failed to retrieve share list from server" ** error.  What command are you using to get this reply?

From the host ubuntu please post again the output of ```
smbtree -d6
```  And the output from *both * Windows hosts using ```
smbclient -L <Windows_COMPUTER_Name>
```

---

### Post by stevebag on 2010-12-22
I was having a similar problem accessing the network, could see the other computers but got the same error message, this tutorial worked for me

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

My issue was solved by following the directions in that post, specifically problem 3.

---

### Post by capscrew on 2010-12-22
> **stevebag said:**
> I was having a similar problem accessing the network, could see the other computers but got the same error message, this tutorial worked for me

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

My issue was solved by following the directions in that post, specifically problem 3.

The cure you are recommending is technically incorrect.  Modifying the nsswitch.conf file and adding winbind is **not ** the best way to handle the situation.  It can cause huge delays in DNS resolution if the host is used as a Desktop to browse the web.

---

### Post by briangoldberg on 2010-12-22
> From the host ubuntu please post again the output of      
   ```
   smbtree -d6 
```  And the output from *both * Windows hosts using      Code:
 ```
    smbclient -L <Windows_COMPUTER_Name> 
``````
shoshana@ubuntu:~$ smbclient -L goldberg-pc
Enter shoshana's password: 
Connection to goldberg-pc failed (Error NT_STATUS_CONNECTION_REFUSED)
shoshana@ubuntu:~$ smbclient -L cpu
Enter shoshana's password: 
Domain=[CPU] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Sharename       Type      Comment
    ---------       ----      -------
Error returning browse list: NT_STATUS_OK
Domain=[CPU] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------
shoshana@ubuntu:~$ smbtree -d6 > smtree_output.txt
Enter shoshana's password: 
shoshana@ubuntu:~$ 
```Here is the contents of the smbtree -d6 command
```
INFO: Current debug levels:
  all: True/6
  tdb: False/0
  printdrivers: False/0
  lanman: False/0
  smb: False/0
  rpc_parse: False/0
  rpc_srv: False/0
  rpc_cli: False/0
  passdb: False/0
  sam: False/0
  auth: False/0
  winbind: False/0
  vfs: False/0
  idmap: False/0
  quota: False/0
  acls: False/0
  locking: False/0
  msdfs: False/0
  dmapi: False/0
  registry: False/0
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = workgroup
doing parameter netbios name = ubuntu
handle_netbios_name: set global_myname to: UBUNTU
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter security = share
doing parameter encrypt passwords = yes
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
Attempting to register new charset UCS-2LE
Registered charset UCS-2LE
Attempting to register new charset UTF-16LE
Registered charset UTF-16LE
Attempting to register new charset UCS-2BE
Registered charset UCS-2BE
Attempting to register new charset UTF-16BE
Registered charset UTF-16BE
Attempting to register new charset UTF8
Registered charset UTF8
Attempting to register new charset UTF-8
Registered charset UTF-8
Attempting to register new charset ASCII
Registered charset ASCII
Attempting to register new charset 646
Registered charset 646
Attempting to register new charset ISO-8859-1
Registered charset ISO-8859-1
Attempting to register new charset UCS2-HEX
Registered charset UCS2-HEX
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
added interface eth1 ip=fe80::219:7dff:fe28:8723%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.66 bcast=192.168.1.255 netmask=255.255.255.0
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/run/samba/gencache.tdb read-only.
Opening cache file at /var/run/samba/gencache_notrans.tdb
no entry for WORKGROUP#1D found.
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_hosts: not appropriate for name type <0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 1
    SO_BROADCAST = 1
    Could not test socket option TCP_NODELAY.
    Could not test socket option TCP_KEEPCNT.
    Could not test socket option TCP_KEEPIDLE.
    Could not test socket option TCP_KEEPINTVL.
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 114688
    SO_RCVBUF = 114688
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    Could not test socket option TCP_QUICKACK.
Sending a packet of len 50 to (192.168.1.255) on port 137
Received a packet of len 62 from (192.168.1.66) port 137
nmb packet from 192.168.1.66(137) header: id=13275 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....B   hex 0000C0A80142
Got a positive name query response from 192.168.1.66 ( 192.168.1.66 )
namecache_store: storing 1 address for WORKGROUP#1d: 192.168.1.66
Connecting to host=192.168.1.66
Connecting to 192.168.1.66 at port 445
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 0
    SO_BROADCAST = 0
    TCP_NODELAY = 1
    TCP_KEEPCNT = 9
    TCP_KEEPIDLE = 7200
    TCP_KEEPINTVL = 75
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 50724
    SO_RCVBUF = 87552
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
write_socket(4,140)
write_socket(4,140) wrote 140
size=96
smb_com=0x73
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=49155
smb_tid=0
smb_pid=8823
smb_uid=0
smb_mid=2
smt_wct=3
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    1 (0x1)
smb_bcc=55
size=96
smb_com=0x73
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=49155
smb_tid=0
smb_pid=8823
smb_uid=0
smb_mid=2
smt_wct=3
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    1 (0x1)
smb_bcc=55
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
namecache_status_fetch: no entry for NBT/*#00.00.192.168.1.66 found.
Sending a packet of len 50 to (192.168.1.66) on port 137
Received a packet of len 229 from (192.168.1.66) port 137
nmb packet from 192.168.1.66(137) header: id=11522 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .UBUNTU            hex 075542554E5455202020202020202020
    answers  10 char ...UBUNTU          hex 0004005542554E545520202020202020
    answers  20 char   ...UBUNTU        hex 20200304005542554E54552020202020
    answers  30 char      ....__MSBRO   hex 2020202020040001025F5F4D5342524F
    answers  40 char WSE__....WORKGRO   hex 5753455F5F02018400574F524B47524F
    answers  50 char UP      ...WORKG   hex 55502020202020201D0400574F524B47
    answers  60 char ROUP      ...WOR   hex 524F55502020202020201E8400574F52
    answers  70 char KGROUP      ....   hex 4B47524F555020202020202000840000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ................   hex 00000000000000000000000000000000
    answers  a0 char .............   hex 00000000000000000000000000
namecache_status_store: entry NBT/*#00.00.192.168.1.66 store failed.
Connecting to host=UBUNTU
Connecting to 192.168.1.66 at port 445
Socket options:
    SO_KEEPALIVE = 0
    SO_REUSEADDR = 0
    SO_BROADCAST = 0
    TCP_NODELAY = 1
    TCP_KEEPCNT = 9
    TCP_KEEPIDLE = 7200
    TCP_KEEPINTVL = 75
    IPTOS_LOWDELAY = 0
    IPTOS_THROUGHPUT = 0
    SO_SNDBUF = 50724
    SO_RCVBUF = 87552
    SO_SNDLOWAT = 1
    SO_RCVLOWAT = 1
    SO_SNDTIMEO = 0
    SO_RCVTIMEO = 0
    TCP_QUICKACK = 1
write_socket(4,140)
write_socket(4,140) wrote 140
size=96
smb_com=0x73
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=49155
smb_tid=0
smb_pid=8823
smb_uid=0
smb_mid=2
smt_wct=3
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    1 (0x1)
smb_bcc=55
size=96
smb_com=0x73
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=49155
smb_tid=0
smb_pid=8823
smb_uid=0
smb_mid=2
smt_wct=3
smb_vwv[ 0]=  255 (0xFF)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    1 (0x1)
smb_bcc=55
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
```> Except for the title of this thread we have not seen any output that displays **"Unable to mount location: Failed to retrieve share list from server" ** error.  What command are you using to get this reply?
Hey capscrew, sorry if you feel I haven't provided enough information.
When I click on places - network - windows network - workgroup

I get the error message unable to mount location: failed to retrieve share list from server see screen shot attached.

---

### Post by capscrew on 2010-12-22
> **briangoldberg said:**
> ```
 ...

[COLOR="Red"]Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled[/COLOR]
failed tcon_X with NT_STATUS_ACCESS_DENIED
```

Hey capscrew, sorry if you feel I haven't provided enough information...

Brian,

Don't worry.  It's just my ADHD kicking in.  Plus I'm easily confused.  :D

I think the part in red is due to the /etc/samba/smb.conf having this line: ```
 security = [COLOR="DarkRed"]**share **[/COLOR]
```

Please edit the /etc/samba/smb.conf file to change the line to: ```
security = [COLOR="Blue"]**user**[/COLOR]
```

Restart the Samba services (smbd and nmbd).  Then post the output of ```
smbtree -d[COLOR="Green"]**4**[/COLOR]

```

I have lowered the debug level to remove some of the useless noise.

---

### Post by briangoldberg on 2010-12-23
```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = workgroup
doing parameter netbios name = ubuntu
handle_netbios_name: set global_myname to: UBUNTU
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter security = user
doing parameter encrypt passwords = yes
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
added interface eth1 ip=fe80::219:7dff:fe28:8723%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.66 bcast=192.168.1.255 netmask=255.255.255.0
Enter shoshana's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
Unable to find master browser for workgroup WORKGROUP, falling back to broadcast
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
nmb packet from 192.168.1.66(137) header: id=15234 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....B   hex 8000C0A80142
Got a positive name query response from 192.168.1.66 ( 192.168.1.66 )
nmb packet from 192.168.1.65(137) header: id=15234 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....A   hex 8000C0A80141
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
nmb packet from 192.168.1.66(137) header: id=27914 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .UBUNTU            hex 065542554E5455202020202020202020
    answers  10 char ...UBUNTU          hex 0004005542554E545520202020202020
    answers  20 char   ...UBUNTU        hex 20200304005542554E54552020202020
    answers  30 char      ....__MSBRO   hex 2020202020040001025F5F4D5342524F
    answers  40 char WSE__....WORKGRO   hex 5753455F5F02018400574F524B47524F
    answers  50 char UP      ...WORKG   hex 55502020202020201E8400574F524B47
    answers  60 char ROUP      ......   hex 524F5550202020202020008400000000
    answers  70 char ................   hex 00000000000000000000000000000000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ...........   hex 0000000000000000000000
nmb packet from 192.168.1.66(137) header: id=1771 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=33 rr_class=1 ttl=0
    answers   0 char .UBUNTU            hex 065542554E5455202020202020202020
    answers  10 char ...UBUNTU          hex 0004005542554E545520202020202020
    answers  20 char   ...UBUNTU        hex 20200304005542554E54552020202020
    answers  30 char      ....__MSBRO   hex 2020202020040001025F5F4D5342524F
    answers  40 char WSE__....WORKGRO   hex 5753455F5F02018400574F524B47524F
    answers  50 char UP      ...WORKG   hex 55502020202020201E8400574F524B47
    answers  60 char ROUP      ......   hex 524F5550202020202020008400000000
    answers  70 char ................   hex 00000000000000000000000000000000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ...........   hex 0000000000000000000000
nmb packet from 192.168.1.65(137) header: id=26498 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .CPU               hex 06435055202020202020202020202020
    answers  10 char ...MSHOME          hex 0004004D53484F4D4520202020202020
    answers  20 char   ...CPU           hex 20200084004350552020202020202020
    answers  30 char      ..MSHOME      hex 202020202004004D53484F4D45202020
    answers  40 char       ...MSHOME    hex 2020202020201E84004D53484F4D4520
    answers  50 char         .....__M   hex 20202020202020201D040001025F5F4D
    answers  60 char SBROWSE__.......   hex 5342524F5753455F5F02018400001EC7
    answers  70 char ;...............   hex 3BEFDA00000000000000000000000000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ...........   hex 0000000000000000000000
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
nmb packet from 192.168.1.65(137) header: id=27017 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=MSHOME<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....A   hex 0000C0A80141
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
found master browser MSHOME, 192.168.1.65
Connecting to host=192.168.1.65
Connecting to 192.168.1.65 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1b>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name WORKGROUP<0x1b>
resolve_wins: WINS server resolution selected and no WINS servers listed.
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1b>
Cannot find master browser for workgroup WORKGROUP
MSHOME
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
nmb packet from 192.168.1.65(137) header: id=26317 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=MSHOME<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....A   hex 0000C0A80141
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
Connecting to host=192.168.1.65
Connecting to 192.168.1.65 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
    \\CPU                    Downstairs PC
Connecting to host=CPU
resolve_lmhosts: Attempting lmhosts lookup for name CPU<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name CPU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name CPU<0x20>
Connecting to 192.168.1.65 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NetShareEnum res=5

```

---

### Post by capscrew on 2010-12-23
I'm a bit perplexed.  The term spnego is an NTLM authentication protocol.  At this point I'm guessing that CPU has some extra authentication needs.  I think this is why we are getting the following:

```
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
```

Do you have Windows Live Sign-In assistant working on either of the Windows hosts?

Is the host CPU using Windows 7 or either a Win2003 or Win2008 server?

The authentication problem does not appear to be from the Samba  *Server *setup, but rather from the Samba *Client *interaction with the Windows SMB/CIFS server built into every Windows OS.  The authentication schemes have changed recently.

I must admit I do not run Win7 and have no Windows Servers close by.  It is hard for me to test out corrective measures past Windows Vista implementations.

I think if we turn off the host CPU and wait 15 minutes to run *smbtree -d4 *we can at least have a successful listing of the shares that are left.  It is important to wait 15 minutes while the Master Browse list is recreated without CPU in it.

---

### Post by briangoldberg on 2010-12-24
> **capscrew said:**
> I'm a bit perplexed.  The term spnego is an NTLM authentication protocol.  At this point I'm guessing that CPU has some extra authentication needs.  I think this is why we are getting the following:

```
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
```Do you have Windows Live Sign-In assistant working on either of the Windows hosts?

Is the host CPU using Windows 7 or either a Win2003 or Win2008 server?

The authentication problem does not appear to be from the Samba  *Server *setup, but rather from the Samba *Client *interaction with the Windows SMB/CIFS server built into every Windows OS.  The authentication schemes have changed recently.

I must admit I do not run Win7 and have no Windows Servers close by.  It is hard for me to test out corrective measures past Windows Vista implementations.

I think if we turn off the host CPU and wait 15 minutes to run *smbtree -d4 *we can at least have a successful listing of the shares that are left.  It is important to wait 15 minutes while the Master Browse list is recreated without CPU in it.
```
shoshana@ubuntu:~$ smbtree -d4
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = workgroup
doing parameter netbios name = ubuntu
handle_netbios_name: set global_myname to: UBUNTU
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter security = user
doing parameter encrypt passwords = yes
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
added interface eth1 ip=fe80::219:7dff:fe28:8723%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.66 bcast=192.168.1.255 netmask=255.255.255.0
Enter shoshana's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.1.66(137) header: id=21788 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....B   hex 0000C0A80142
Got a positive name query response from 192.168.1.66 ( 192.168.1.66 )
Connecting to host=192.168.1.66
Connecting to 192.168.1.66 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
nmb packet from 192.168.1.66(137) header: id=624 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....B   hex 8000C0A80142
Got a positive name query response from 192.168.1.66 ( 192.168.1.66 )
nmb packet from 192.168.1.66(137) header: id=14364 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .UBUNTU            hex 075542554E5455202020202020202020
    answers  10 char ...UBUNTU          hex 0004005542554E545520202020202020
    answers  20 char   ...UBUNTU        hex 20200304005542554E54552020202020
    answers  30 char      ....__MSBRO   hex 2020202020040001025F5F4D5342524F
    answers  40 char WSE__....WORKGRO   hex 5753455F5F02018400574F524B47524F
    answers  50 char UP      ...WORKG   hex 55502020202020201D0400574F524B47
    answers  60 char ROUP      ...WOR   hex 524F55502020202020201E8400574F52
    answers  70 char KGROUP      ....   hex 4B47524F555020202020202000840000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ................   hex 00000000000000000000000000000000
    answers  a0 char .............   hex 00000000000000000000000000
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.1.66(137) header: id=32645 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....B   hex 0000C0A80142
Got a positive name query response from 192.168.1.66 ( 192.168.1.66 )
found master browser WORKGROUP, 192.168.1.66
Connecting to host=192.168.1.66
Connecting to 192.168.1.66 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.1.66(137) header: id=23724 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....B   hex 0000C0A80142
Got a positive name query response from 192.168.1.66 ( 192.168.1.66 )
Connecting to host=192.168.1.66
Connecting to 192.168.1.66 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
    \\UBUNTU                 ubuntu server (Samba, Ubuntu)
Connecting to host=UBUNTU
resolve_lmhosts: Attempting lmhosts lookup for name UBUNTU<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name UBUNTU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name UBUNTU<0x20>
Connecting to 127.0.0.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
SPNEGO login failed: Logon failure
        \\UBUNTU\HP-LaserJet-1200    HP LaserJet 1200
        \\UBUNTU\IPC$               IPC Service (ubuntu server (Samba, Ubuntu))
        \\UBUNTU\print$             Printer Drivers
        \\UBUNTU\Myshare2           Myshare2
        \\UBUNTU\Myshare            Myshare
    \\GOLDBERG-PC            
Connecting to host=GOLDBERG-PC
resolve_lmhosts: Attempting lmhosts lookup for name GOLDBERG-PC<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
resolve_wins: Attempting wins lookup for name GOLDBERG-PC<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name GOLDBERG-PC<0x20>
Connecting to 192.168.1.254 at port 445
Connecting to 192.168.1.254 at port 139
Error connecting to 192.168.1.254 (Connection refused)
cli_start_connection: failed to connect to GOLDBERG-PC<20> (0.0.0.0). Error NT_STATUS_CONNECTION_REFUSED
shoshana@ubuntu:~$ 

```

---

### Post by briangoldberg on 2010-12-24
> **capscrew said:**
> I'm a bit perplexed.  Me too> The term spnegowhat does it stand for?>  is an NTLM what does it stand for?> authentication protocol.  At this point I'm guessing that CPU has some extra authentication needs.  I think this is why we are getting the following:

```
Doing spnego session setup (blob length=16)blob is this Oracle?> 
server didn't supply a full spnego negprotwhat does it stand for?> 
```Do you have Windows Live Sign-In assistant working on either of the Windows hosts?CPU pc No, Goldberg-pc no> 

Is the host CPU using Windows 7 No> or either a Win2003  No> or Win2008 server? No.
CPU is Windows XP Home Edition, not a server.
Goldberg-PC is Windows Vista, compaq laptop, not a server> 

The authentication problem does not appear to be from the Samba  *Server *setup, but rather from the Samba *Client *interaction with the Windows SMB/CIFS  What does it stand for?> server built into every Windows OS.  The authentication schemes have changed recently.

I must admit I do not run Win7 and have no Windows Servers close by.  It is hard for me to test out corrective measures past Windows Vista implementations.

I think if we turn off the host CPU and wait 15 minutes to run *smbtree -d4 *we can at least have a successful listing of the shares that are left.  It is important to wait 15 minutes while the Master Browse list is recreated without CPU in it.

Done in the last post. I sent the results of smbtree -d4. I let the CPU stay off for 15 minutes. Now I can't print from any computer in the house, a small sacrifice to UBUNTU.

No worries Capscrew, no servers here, no Windows 7 here.

---

### Post by capscrew on 2010-12-27
> **briangoldberg said:**
> ...what does it  [SPNEGO and NTLM] stand  for?

The term SPNEGO is described [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://en.wikipedia.org/wiki/SPNEGO") and the term NTLM is described [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://en.wikipedia.org/wiki/NTLM").
> blob is this Oracle?
Oracle?  No nothing to do with Oracle (the data base).  Do you have components of an Oracle data base installed?

> server didn't supply a full spnego negprot

It appears this means a correct password (or internal token) was  *not supplied* when needed.


> What does it stand for [SMB/CIFS]

SMB/CIFS is the protocol that Microsoft and Samba use for file sharing.

Your first problem seems to be the inability to authenticate the user of the shares.  This is what is causing your original complaint of:  "Unable to mount location: Failed to retrieve share list from server".    

When you first installed Samba did you add Samba users?  What do you do when you are prompted with this request?
```
Enter shoshana's password: 
```

---

### Post by briangoldberg on 2010-12-27
Hi Capscrew,
Long time no post. Yes it looks like an authentication problem. Please help me to fix it. I haven't set up any samba users. How can I tell if I have. The goldberg-pc has a user named Goldberg that needs to be used to get to the shared files public/publicpictures and public/publicvideos. I type the sudo password when prompted for Shoshana's password.

---

### Post by capscrew on 2010-12-27
> **briangoldberg said:**
> Hi Capscrew,
Long time no post. 
Holidays with my family.> 

Yes it looks like an authentication problem. Please help me to fix it. I haven't set up any samba users. How can I tell if I have.

From the terminal you can list all the Samba users with this```
sudo pdbedit -Lv
```
>  

The goldberg-pc has a user named Goldberg that needs to be used to get to the shared files public/publicpictures and public/publicvideos. 
This sounds like you have password protected your Windows shares.  Is this correct?  If so why do you need to do that?> 

I type the sudo password when prompted for Shoshana's password.

Why would you use your root password (with sudo) when Samba is asking for Shoshana's password?  Sudo is inappropriate here.  Did you try Shoshana's password?

So, how do you get out of this mess.  First of all simplify.  Have a consistent policy for authentication across all OS's and shares.

All of my users, be they Linux, Windows or Samba users are the same from host to host.  This means my login is the same on my Windows Vista, Windows XP, Ubuntu Desktop or Ubuntu Server.   The Samba user should also be the same.

My suggestion is for you to read the [**_[COLOR="DarkSlateGray"]Samba3 by Example Guide[/COLOR]_**]("http://www.samba.org/samba/docs/man/Samba-Guide/").  This is an excellent guide to basic samba configuration.  All of the official documentation is located **_[COLOR="DarkSlateGray"]here[/COLOR]_**.  

In the long run it is best for you to learn this stuff.  Everyone starts where you are.  I'm more than willing to help with answering questions, but you need to understand how the system works.  Read the guide. Then ask questions.

---

### Post by briangoldberg on 2010-12-27
Thanks for your help. The sudo password and the shoshana password are the same. Shoshana is the only user on the whole ubuntu. A simple world is ideal. I'm sure there is a way to have different users on different systems too.

---

### Post by capscrew on 2010-12-27
> **briangoldberg said:**
> Thanks for your help. The sudo password and the shoshana password are the same. Shoshana is the only user on the whole ubuntu. A simple world is ideal. I'm sure there is a way to have different users on different systems too.

You have to have **every **user that will interact with Samba in the Samba database.  To add the user to the Samba database you need for that user to be a Ubuntu user first.  That's just how Samba works.  The guest account must be configured for anonymous use.  Note that some command line tools will not work.  

Of course if the user shoshana is the only user (e.g. the first user) then that user is in the sudoers file.  But sudo itself is inappropriate for Samba authentication.

Can you have multiple users on multiple hosts?  Sure you can.  It is a needless complexity to have a user on one host as **brian ** and that same user on another host as **bgoldberg** and the samba user to be **shoshana**.  If these are all the same user then they should have the same login and password.  If that is not a possibility, then you need to map one user to another for samba to work.

If you have multiple users then each user should have a consistent login/pass across all hosts.  This is why a central authentication database is used in large networks.

Of course you can do it however you want.  It is, after all, your system.

---

### Post by briangoldberg on 2010-12-27
I added Goldberg as a user. I made that user have the same password as on the Windows Vista box. To be honest with you Capscrew this is going no where fast
```
shoshana@ubuntu:~$ sudo pdbedit -Lv
---------------
Unix username:        nobody
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-2134597465-2665759534-3918734670-501
Primary Group SID:    S-1-5-21-2134597465-2665759534-3918734670-513
Full Name:            nobody
Home Directory:       
HomeDir Drive:        (null)
Logon Script:         
Profile Path:         
Domain:               UBUNTU
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          never
Kickoff time:         never
Password last set:    0
Password can change:  0
Password must change: 0
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
---------------
Unix username:        Goldberg
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-2134597465-2665759534-3918734670-1000
Primary Group SID:    S-1-5-21-2134597465-2665759534-3918734670-513
Full Name:            
Home Directory:       \\ubuntu\goldberg
HomeDir Drive:        
Logon Script:         
Profile Path:         \\ubuntu\goldberg\profile
Domain:               UBUNTU
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          never
Kickoff time:         never
Password last set:    Mon, 27 Dec 2010 23:40:56 EST
Password can change:  Mon, 27 Dec 2010 23:40:56 EST
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
---------------
Unix username:        shoshana
NT username:          
Account Flags:        [U          ]
User SID:             S-1-5-21-2134597465-2665759534-3918734670-3000
Primary Group SID:    S-1-5-21-2134597465-2665759534-3918734670-513
Full Name:            karol danowitz
Home Directory:       \\ubuntu\shoshana
HomeDir Drive:        
Logon Script:         
Profile Path:         \\ubuntu\shoshana\profile
Domain:               UBUNTU
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:          never
Kickoff time:         never
Password last set:    Sat, 18 Dec 2010 22:56:34 EST
Password can change:  Sat, 18 Dec 2010 22:56:34 EST
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
shoshana@ubuntu:~$ 

```

---

### Post by capscrew on 2010-12-28
> **briangoldberg said:**
> I added Goldberg as a user. I made that user have the same password as on the Windows Vista box. To be honest with you Capscrew this is going no where fast
...

So you added a user; great!  What happened when you did that?

Nowhere fast?  What's that supposed to mean?.

---

### Post by briangoldberg on 2010-12-28
Capscrew, below is a screen capture of all the code entered. I think you're sending me on a wild goose chase, that is going nowhere -- fast. I've been posting back and forth for over a week now. Since all this time I've been able to see the CPU printer's that been windows shared before I even installed samba and the computer that the printer is on has a user name and a password. ```
shoshana@ubuntu:~$ sudo login Goldberg
[sudo] password for shoshana: 
Password: 
Last login: Mon Dec 27 23:41:50 EST 2010 on pts/0
Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

203 packages can be updated.
57 updates are security updates.


The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

No directory, logging in with HOME=/
$ smbtree -d4
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = workgroup
doing parameter netbios name = ubuntu
handle_netbios_name: set global_myname to: UBUNTU
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter security = user
doing parameter encrypt passwords = yes
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
added interface eth1 ip=fe80::219:7dff:fe28:8723%eth1 bcast=fe80::ffff:ffff:ffff:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth1 ip=192.168.1.66 bcast=192.168.1.255 netmask=255.255.255.0
Enter Goldberg's password: 
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
getlmhostsent: lmhost entry: 192.168.1.65 cpu 
getlmhostsent: lmhost entry: 192.168.1.254 goldberg-pc 
getlmhostsent: lmhost entry: 127.0.0.1 localhost 
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.1.66(137) header: id=30355 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....B   hex 0000C0A80142
Got a positive name query response from 192.168.1.66 ( 192.168.1.66 )
Connecting to host=192.168.1.66
Connecting to 192.168.1.66 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
nmb packet from 192.168.1.66(137) header: id=31040 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....B   hex 8000C0A80142
Got a positive name query response from 192.168.1.66 ( 192.168.1.66 )
nmb packet from 192.168.1.65(137) header: id=31040 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=__MSBROWSE__<01> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....A   hex 8000C0A80141
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
nmb packet from 192.168.1.66(137) header: id=14687 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=No trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=*<00> rr_type=33 rr_class=1 ttl=0
    answers   0 char .UBUNTU            hex 075542554E5455202020202020202020
    answers  10 char ...UBUNTU          hex 0004005542554E545520202020202020
    answers  20 char   ...UBUNTU        hex 20200304005542554E54552020202020
    answers  30 char      ....__MSBRO   hex 2020202020040001025F5F4D5342524F
    answers  40 char WSE__....WORKGRO   hex 5753455F5F02018400574F524B47524F
    answers  50 char UP      ...WORKG   hex 55502020202020201D0400574F524B47
    answers  60 char ROUP      ...WOR   hex 524F55502020202020201E8400574F52
    answers  70 char KGROUP      ....   hex 4B47524F555020202020202000840000
    answers  80 char ................   hex 00000000000000000000000000000000
    answers  90 char ................   hex 00000000000000000000000000000000
    answers  a0 char .............   hex 00000000000000000000000000
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
getlmhostsent: lmhost entry: 192.168.1.65 cpu 
getlmhostsent: lmhost entry: 192.168.1.254 goldberg-pc 
getlmhostsent: lmhost entry: 127.0.0.1 localhost 
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.1.66(137) header: id=31515 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....B   hex 0000C0A80142
Got a positive name query response from 192.168.1.66 ( 192.168.1.66 )
found master browser WORKGROUP, 192.168.1.66
Connecting to host=192.168.1.66
Connecting to 192.168.1.66 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
getlmhostsent: lmhost entry: 192.168.1.65 cpu 
getlmhostsent: lmhost entry: 192.168.1.254 goldberg-pc 
getlmhostsent: lmhost entry: 127.0.0.1 localhost 
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
nmb packet from 192.168.1.66(137) header: id=12091 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=Yes rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=WORKGROUP<1d> rr_type=32 rr_class=1 ttl=259200
    answers   0 char .....B   hex 0000C0A80142
Got a positive name query response from 192.168.1.66 ( 192.168.1.66 )
Connecting to host=192.168.1.66
Connecting to 192.168.1.66 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
    \\UBUNTU                 ubuntu server (Samba, Ubuntu)
Connecting to host=UBUNTU
resolve_lmhosts: Attempting lmhosts lookup for name UBUNTU<0x20>
getlmhostsent: lmhost entry: 192.168.1.65 cpu 
getlmhostsent: lmhost entry: 192.168.1.254 goldberg-pc 
getlmhostsent: lmhost entry: 127.0.0.1 localhost 
resolve_wins: Attempting wins lookup for name UBUNTU<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name UBUNTU<0x20>
Connecting to 127.0.0.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
        \\UBUNTU\Goldberg           Home Directories
        \\UBUNTU\HP-LaserJet-1200    HP LaserJet 1200
        \\UBUNTU\IPC$               IPC Service (ubuntu server (Samba, Ubuntu))
        \\UBUNTU\print$             Printer Drivers
        \\UBUNTU\Myshare2           Myshare2
        \\UBUNTU\Myshare            Myshare
MSHOME
resolve_lmhosts: Attempting lmhosts lookup for name MSHOME<0x1d>
getlmhostsent: lmhost entry: 192.168.1.65 cpu 
getlmhostsent: lmhost entry: 192.168.1.254 goldberg-pc 
getlmhostsent: lmhost entry: 127.0.0.1 localhost 
name_resolve_bcast: Attempting broadcast lookup for name MSHOME<0x1d>
nmb packet from 192.168.1.65(137) header: id=15284 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=MSHOME<1d> rr_type=32 rr_class=1 ttl=300000
    answers   0 char .....A   hex 0000C0A80141
Got a positive name query response from 192.168.1.65 ( 192.168.1.65 )
Connecting to host=192.168.1.65
Connecting to 192.168.1.65 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
    \\CPU                    Downstairs PC
Connecting to host=CPU
resolve_lmhosts: Attempting lmhosts lookup for name CPU<0x20>
getlmhostsent: lmhost entry: 192.168.1.65 cpu 
Connecting to 192.168.1.65 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a8215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_TARGET_INFO
  NTLMSSP_NEGOTIATE_VERSION
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
  NTLMSSP_NEGOTIATE_UNICODE
  NTLMSSP_REQUEST_TARGET
  NTLMSSP_NEGOTIATE_SIGN
  NTLMSSP_NEGOTIATE_NTLM
  NTLMSSP_NEGOTIATE_ALWAYS_SIGN
  NTLMSSP_NEGOTIATE_NTLM2
  NTLMSSP_NEGOTIATE_128
  NTLMSSP_NEGOTIATE_KEY_EXCH
NetShareEnum res=5
$ 

```

---

