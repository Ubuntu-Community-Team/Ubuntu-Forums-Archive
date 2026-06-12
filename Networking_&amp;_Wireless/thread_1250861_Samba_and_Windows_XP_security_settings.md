---
title: "Samba and Windows XP security settings"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by derek71 on 2009-08-27
Hello, I am trying to set-up Samba 3 on a system running Ubuntu 8.04LTS to act as a NAS.

I initially followed the HOW-TO in this thread: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605).

I can see the server from my Windows XP Pro machine, though I cannot access any of the shares.

I have tried to diagnose the problem from the Linux side without success; searching with Google and through this forum.

I suspect the problem is on the Windows XP side: either a security option needs to be changed or a service needs to be enabled.

Are there any guides up to date with Samba 3 configuring a Windows XP machine for sharing?

Thank you in advance.

---

### Post by dmizer on 2009-08-27
> **derek71 said:**
> Hello, I am trying to set-up Samba 3 on a system running Ubuntu 8.04LTS to act as a NAS.

I initially followed the HOW-TO in this thread: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605).

I can see the server from my Windows XP Pro machine, though I cannot access any of the shares.

I have tried to diagnose the problem from the Linux side without success; searching with Google and through this forum.

I suspect the problem is on the Windows XP side: either a security option needs to be changed or a service needs to be enabled.

Are there any guides up to date with Samba 3 configuring a Windows XP machine for sharing?

Thank you in advance.
That howto is pretty old. It's good, but lots of things have changed.

Can you post your current /etc/samba/smb.conf file? I suspect that a few minor edits will get everything working for you.

---

### Post by derek71 on 2009-08-27
Here is my smb.conf file.  The "smbpasswd file" command in the global section appears to be ignored.

[global]
    ; General server settings
    netbios name = wen-chang
    server string = network attached storage
    workgroup = DEEPTHOT
    encrypt passwords = true
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    hosts deny = ALL
    hosts allow = 192.168.1.100 localhost

    interfaces = lo, eth0
    bind interfaces only = true

    ;passdb backend = tdbsam
    passdb backend = smbpasswd

    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    smb passwd file = /etc/samba/smbpasswd

    name resolve order = hosts wins bcast

    domain master = no
    dns proxy = no

    wins support = no

    syslog = 1
    syslog only = no

    log level = 3
    log file = /var/log/samba.log.%m
    max log size = 50
    debug timestamp = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = yes
    read only = no
    ;veto files = /*.{*}/.*/mail/bin/

[dereklewis]
    path = /mnt/raid/dereklewis
    browseable = yes
    read only = no
    guest ok = no
    ;create mask = 0770
    ;directory mask = 0770
    write list = dereklewis
    read list = dereklewis
    valid users = dereklewis
    case sensitive = yes

[test]
    path = /mnt/raid/test
    browseable = yes
    read only = no
    guest only = yes
    guest ok = yes
    create mask = 0777
    directory mask = 0777
    valid users = dereklewis

---

### Post by dmizer on 2009-08-28
Ok, try this:

```
[global]

## Browsing/Identification ###
   workgroup = WORKGROUP

   server string = %h server (Samba, Ubuntu)
   dns proxy = no

#### Networking ####

   interfaces = 127.0.0.0/8 eth0
   bind interfaces only = yes
   hosts allow = 192.168.1.100 localhost
   hosts deny = ALL

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user


############ Misc ############

   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   usershare allow guests = yes

#======================= Share Definitions =======================

[dereklewis]
path = /mnt/raid/dereklewis
browseable = yes
read only = yes
write list = dereklewis
valid users = dereklewis

[test]
path = /mnt/raid/test
browseable = yes
read only = no
guest ok = yes
```

I took your homes section out. You should share individual directories in your home folder by right clicking on the folder and selecting "share options" rather than sharing the whole folder, as that's quite dangerous.

If that still doesn't work, please post the output of:
```
ls -la /mnt/raid/dereklewis
```

Is 192.168.1.100 a Windows machine or a Linux box?

---

### Post by derek71 on 2009-08-29
I implemented the new smb.conf and stopped/started the samba daemons to make sure the configuration file was read.

I did keep the workgroup set to: DEEPTHOT.  Otherwise the file you posted was used intact.

Thank you dmizer very much for your time by the way.

I still get the error: "The specified network name is no longer available".

I can see the workgroup (DEEPTHOT) and the server from the Windows machine Explorer window.  Though I cannot access anything on the server.

To answer your earlier question, the ip address in the hosts allow is the Windows XP machine.

Here is the output from the command: ls -la /mnt/raid/dereklewis

total 8
drwxrwx--- 2 dereklewis dereklewis 4096 2009-08-02 23:55 .
drwxr-xr-x 5 root       root       4096 2009-08-05 00:08 ..

---

### Post by derek71 on 2009-09-20
I have tried one change to fix the Samba connection problems.  I created a share folder for the [test] share described in the posted smb.conf file, though instead located at: ~/test.  I also set permissions for this folder to 777.

I can see the server though unable to browse or connect to any share.

Derek

---

### Post by dmizer on 2009-09-20
Please post the output of:
```
sudo iptables -L
```

---

### Post by derek71 on 2009-09-20
sudo iptables -L:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh 
fail2ban-apache  tcp  --  anywhere             anywhere            multiport dports www,https 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain fail2ban-apache (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere

---

### Post by dmizer on 2009-09-21
Try disabling fail2ban.

---

### Post by derek71 on 2009-09-22
I disabled fail2ban from the command line and confirmed that the process was shut down.  Checked that the iptables were empty with iptables -L and tried to map the network drive.

I get the same error that the server is not accessable.

---

### Post by derek71 on 2009-10-20
Can I create a Samba share directly on the server?  I would like to test whether my connection problem is due to a network problem or samba configuration.

---

### Post by derek71 on 2009-11-08
I installed smbclient to test creating a share on the server itself.  I still get a connection refused error.  I used ps -ef to confirm that smbd and nmbd are running.

---

### Post by dmizer on 2009-11-09
Your problem is most likely with Windows then.

---

### Post by derek71 on 2009-11-28
After hitting a dead end with my current efforts to get Samba working, I went back to the default samba configuration: smb.conf.template and added my share definitions and network parameters.

I was able to get a connection to my shares briefly, and was able to copy files to it from my PC.  Following attempts to connect result in an error: "The local device name is already  in use."

I have increased the log level to 10, and have checked for error messages in smbd.log, and nmbd.log.  I see a message indicating repeated attempts to contact the WINS server.

I tried to re-connect to the Samba share with the PC firewall off, though I get the same result.

I am closer to making Samba work, though I am not sure what to try next.

Here is my current smb.conf file:

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
   workgroup = DEEPTHOT

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = no
#   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z
   wins server = 192.168.1.100

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
   name resolve order = lmhosts host bcast

# Set Samba to be the local master browser, and the PC as the domain master
# browser.
   domain master = no
   local master = no
   preferred master = no
   os level = 0

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

   hosts allow = 192.168.1.100 127.0.0.1 localhost

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 10

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d

   smb ports = 139

####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how nsuccessful authentication attempts are mapped 
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
[dereklewis]
path=/mnt/raid/dereklewis
browseable=yes
read only=no
guest ok=no
create mode = 0660
directory mode = 0770
valid users=dereklewis

[test]
path=/mnt/raid/test
browseable=yes
read only=no
guest ok=yes
create mode = 0660
directory mode = 0770
valid users=dereklewis

---

### Post by dmizer on 2009-11-29
Just disable the wins stuff. This is only useful if you need Samba name resolution to work across subdomains.

Also, add this line just below the "workgroup" option:
```
netbios name = wen-chang
```

Remove the "create mode" and "directory mode" from the share options, as these are no longer valid options.

---

### Post by derek71 on 2009-12-06
I implemented the net bios line, though Samba seemed to ignore it.  I went through my Samba configuration and checked my network settings, and browse settings.

I am able to map the network drive, though I can't access the contents.  Also, I cannot browse the shares; though the workgroup and server are visible.  From the logs, I see some connectivity problems: "timeout",  "connection refused", though no indication of the source of the problem.

I have attached my current smb.conf file, and my logs: log.smbd, log.nmbd, and log.kamen (PC).
 
I had to rename the files to *.txt in order to upload them, and log.kamen had to be zipped.

---

