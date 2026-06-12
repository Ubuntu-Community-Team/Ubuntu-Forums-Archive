---
title: "cannot access ubuntu 12.04 SAMBA share from windows 7 using hostname"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by Cfhs_1 on 2012-10-18
I've been trying for days to get this working, and everywhere I look online it seems no one has a definitive answer, so here is the run down:

I have an external drive attached to my ubuntu 12.04 machine, "nicholas-desktop." I have the entire drive shared over the network via SAMBA. If I try to access the drive from windows 7 by using "\nicholas-desktop" it fails saying it cannot locate "nicholas-desktop." However, if I use the current IP address assigned to my machine by my router's DHCP server by typing "\192.168.2.XXX" I have no problems accessing the share. if I try to ping my ubuntu machine's hostname from windows it fails. The same happens if I try to ping my windows machine, "nicholas-laptop" from my ubuntu machine. Again, if I use either machine's assigned IP address it works fine. Can someone please help me get this working? I don't want any workarounds like setting a static IP, or DHCP reservation, I want to be able to resolve hostnames from both sides. I have tried enabling SAMBA'a WINS server so I could resolve the hostnames using netBIOS, however that didn't work either, I may have made a mistake setting it up though.

I have also made this exact same post over at askubuntu.com, but got no help what-so-ever. 
[_HERE_]("http://bit.ly/PdxXet") is the link to that.


Thanks for your time,

NCB

---

### Post by bab1 on 2012-10-19
> **Cfhs_1 said:**
> I have an external drive attached to my ubuntu 12.04 machine, "nicholas-desktop."
The is a problem.  Samba only resolves COMPUTER NAMES of 15 characters or less.> 
 I have the entire drive shared over the network via SAMBA. If I try to access the drive from windows 7 by using "\nicholas-desktop" it fails saying it cannot locate "nicholas-desktop."  However, if I use the current IP address assigned to my machine by my router's DHCP server by typing "\192.168.2.XXX" I have no problems accessing the share. 
Samba attempts to resovle the COMPUTER NAME to IP address.  If you provide the IP address then there is no need for name resolution. > 
if I try to ping my ubuntu machine's hostname from windows it fails. The same happens if I try to ping my windows machine, "nicholas-laptop" from my ubuntu machine.
Ping is a part of TCP/IP and uses hostnames for reoslution.  This is NOT a COMPUTER NAME.  Samba is able convert a hostname to a COMPUTER NAME (NetBIOS), but only if the hostname is resolvable via DNS or by the /etc/hosts file.>  Again, if I use either machine's assigned IP address it works fine. Can someone please help me get this working? I don't want any workarounds like setting a static IP, or DHCP reservation, I want to be able to resolve hostnames from both sides. 
DNS and NetBIOS resolution are two different things, requiring two solutions.  The Samba/NetBIOS name is the easiest to solve with a simple configuration parameters change in the /etc/samba/smb.conf file. > 
I have tried enabling SAMBA'a WINS server so I could resolve the hostnames using netBIOS, however that didn't work either, I may have made a mistake setting it up though.
This should have worked as the WINS server is used to resolve NetBIOS names to IP addresses.  My guess us that you have not provided a NetBIOS name for the host (or at the least a proper NetBIOS name (see above)).

If you wish to have dynamic IP to hostname DNS resolution you either need to configure an internal DNS server or find a router that will do this,  Since it has nothing to do with Samba I won't comment further on a setting up DNS.

Let's start with you posting the output of the */etc/samba/smb.conf* file (enclose the text in the **[code] [ /code]** brackets).

---

### Post by Cfhs_1 on 2012-10-19
> **bab1 said:**
> The is a problem.  Samba only resolves COMPUTER NAMES of 15 characters or less.Samba attempts to resovle the COMPUTER NAME to IP address.  If you provide the IP address then there is no need for name resolution. Ping is a part of TCP/IP and uses hostnames for reoslution.  This is NOT a COMPUTER NAME.  Samba is able convert a hostname to a COMPUTER NAME (NetBIOS), but only if the hostname is resolvable via DNS or by the /etc/hosts file.DNS and NetBIOS resolution are two different things, requiring two solutions.  The Samba/NetBIOS name is the easiest to solve with a simple configuration parameters change in the /etc/samba/smb.conf file. This should have worked as the WINS server is used to resolve NetBIOS names to IP addresses.  My guess us that you have not provided a NetBIOS name for the host (or at the least a proper NetBIOS name (see above)).

If you wish to have dynamic IP to hostname DNS resolution you either need to configure an internal DNS server or find a router that will do this,  Since it has nothing to do with Samba I won't comment further on a setting up DNS.

Let's start with you posting the output of the */etc/samba/smb.conf* file (enclose the text in the **```
 [ /code]** brackets).

[CODE]#
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
	username map = /etc/samba/smbusers
	security = user
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

[networkshare]
	path = /media/networkshare
	writeable = yes
;	browseable = yes
#	valid users = nicholas
	force user = nicholas
```

What would be the best solution then? I would like to be able to map the network drive in windows without having to lock my machine down to a static IP.

Thanks,
NCB

---

### Post by bab1 on 2012-10-19
> **Cfhs_1 said:**
> 
What would be the best solution then? I would like to be able to map the network drive in windows without having to lock my machine down to a static IP.

Thanks,
NCB
The first thing we can do is make this host visible to Windows sharing hosts (CIFS).  You should use a name of your choosing that is less than 15 characters ([COLOR="Red"]**see red below**[/COLOR]) and edit the existing code ([COLOR="Green"]**see green below**[/COLOR]) ```
# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
```

We want it to look like this```

[COLOR="Red"]**netbios name = COMPUTER_NAME**[/COLOR]
# What naming service and in what order should we use to resolve host names
# to IP addresses
[COLOR="Green"]name resolve order = bcast[/COLOR]
```

This should broadcast the COMPUTER_NAME (NetBIOS) and Samba will resolve that to the IP address.  Note: You should start with any firewall between hosts off while testing.

---

### Post by Cfhs_1 on 2012-10-19
> **bab1 said:**
> The first thing we can do is make this host visible to Windows sharing hosts (CIFS).  You should use a name of your choosing that is less than 15 characters ([COLOR="Red"]**see red below**[/COLOR]) and edit the existing code ([COLOR="Green"]**see green below**[/COLOR]) ```
# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
```

We want it to look like this```

[COLOR="Red"]**netbios name = COMPUTER_NAME**[/COLOR]
# What naming service and in what order should we use to resolve host names
# to IP addresses
[COLOR="Green"]name resolve order = bcast[/COLOR]
```

This should broadcast the COMPUTER_NAME (NetBIOS) and Samba will resolve that to the IP address.  Note: You should start with any firewall between hosts off while testing.

Alright, I made the changes you suggested to smb.conf, and also enabled WINS support again. Windows still cannot see my machine. I changed my machine's name to nicholas-dsktop which is exactly 15 characters.

---

### Post by JKyleOKC on 2012-10-19
Does Win 7 still have a "hosts" file in its WINDOWS folder? I suspect that it does, since many folk use this file as a way to lock out certain unwanted web addresses.

If it does, you can add this one line (properly edited to fit your situation) to that file and you should then be able to access the other machine by either name or IP address: ```
192.168.2.XXX   nicholas-dsktop
```Then change this line in your smb.conf file  ```
name resolve order = bcast
```back so that it reads 
```
name resolve order = host bcast lmhost wins
```and reload the smbd daemon.

Adding the IP address to the hosts file makes the system translate the name into the IP address, which you say works properly. Do you have a reason for not wanting to assign the same address to your other machine each time it connects? Most routers make it easy to do, and it solves many problems quite simply.

---

### Post by bab1 on 2012-10-19
> **JKyleOKC said:**
> Does Win 7 still have a "hosts" file in its WINDOWS folder? I suspect that it does, since many folk use this file as a way to lock out certain unwanted web addresses...

The OP specifically insisted on DHCP IP addressing ...>  I would like to be able to map the network drive in windows without having to lock my machine down to a static IP.

In this case using a hosts file mapping won't work.  Only NetBIOS broadcasts or WINS will work.  We need to map NetBIOS name to IP address, not IP address to hostname.  Note the order of resolution.  The only thing static is the NetBIOS name.

---

### Post by bab1 on 2012-10-19
> **Cfhs_1 said:**
> Alright, I made the changes you suggested to smb.conf, and also enabled WINS support again. Windows still cannot see my machine. I changed my machine's name to nicholas-dsktop which is exactly 15 characters.

Why the WINS support?  What do you mean by WINS support specifically?  With bcast you do not need a WINS server on a single segment LAN, 

Did you reload the SMBD daemon or reboot the machine?

From the terminal, what do you get from this command```
smbtree -d3
```

---

### Post by JKyleOKC on 2012-10-19
> **bab1 said:**
> The OP specifically insisted on DHCP IP addressing ...

In this case using a hosts file mapping won't work.  Only NetBIOS broadcasts or WINS will work.  We need to map NetBIOS name to IP address, not IP address to hostname.  Note the order of resolution.  The only thing static is the NetBIOS name.Agreed, which is why I asked if he had a reason to stay strictly with DHCP.

As it happens, my Motorola 3347 router has the ability to pin a DHCP address to a specific MAC, making it effectively a static IP although it's given out via DHCP. If the OP's systems have a similar capability, he can achieve his goal much more simply than by dealing with NetBIOS. However I don't recall seeing such an ability on my old WRT54G, so it may not be common.

If sticking with NetBIOS, he may be running into the problem of case sensitivity; Windows usually does its network searches using all-upper-case; if he sets his NetBIOS name to lower case, it may not be found -- although I would hope that the Samba daemons would correct for this automagically.

---

### Post by bab1 on 2012-10-19
> **JKyleOKC said:**
> Agreed, which is why I asked if he had a reason to stay strictly with DHCP.
He specifically stated that he wanted to stay with DHCP on more than one occasion.> 

As it happens, my Motorola 3347 router has the ability to pin a DHCP address to a specific MAC, making it effectively a static IP although it's given out via DHCP. If the OP's systems have a similar capability, he can achieve his goal much more simply than by dealing with NetBIOS. However I don't recall seeing such an ability on my old WRT54G, so it may not be common.
I understand, but the OP has stated his goal and it is a doable thing so why the not help him achieve just what he wants?> 

If sticking with NetBIOS, he may be running into the problem of case sensitivity; Windows usually does its network searches using all-upper-case; if he sets his NetBIOS name to lower case, it may not be found -- although I would hope that the Samba daemons would correct for this automagically.
Samba converts everything to UPPER CASE.  MS has always been case insensitive anyway. At the worst it has only case preference.

---

### Post by Cfhs_1 on 2012-10-20
> **bab1 said:**
> He specifically stated that he wanted to stay with DHCP on more than one occasion.I understand, but the OP has stated his goal and it is a doable thing so why the not help him achieve just what he wants?
Samba converts everything to UPPER CASE.  MS has always been case insensitive anyway. At the worst it has only case preference.

```
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::213:72ff:fe2b:8326%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.2.5 bcast=192.168.2.255 netmask=255.255.255.0
Enter nicholas's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.2.112 ( 192.168.2.112 )
Connecting to host=192.168.2.112
Connecting to 192.168.2.112 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.2.112 ( 192.168.2.112 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.2.112 ( 192.168.2.112 )
Connecting to host=192.168.2.112
Connecting to 192.168.2.112 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.2.112 ( 192.168.2.112 )
Connecting to host=192.168.2.112
Connecting to 192.168.2.112 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\NICHOLAS-DSKTOP		nicholas-dsktop server (Samba, Ubuntu)
Connecting to host=NICHOLAS-DSKTOP
resolve_lmhosts: Attempting lmhosts lookup for name NICHOLAS-DSKTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name NICHOLAS-DSKTOP<0x20>
resolve_wins: Attempting wins lookup for name NICHOLAS-DSKTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name NICHOLAS-DSKTOP<0x20>
resolve_hosts: getaddrinfo failed for name NICHOLAS-DSKTOP [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name NICHOLAS-DSKTOP<0x20>
Got a positive name query response from 192.168.2.5 ( 192.168.2.5 )
Connecting to 192.168.2.5 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\NICHOLAS-DSKTOP\IPC$           	IPC Service (nicholas-dsktop server (Samba, Ubuntu))
		\\NICHOLAS-DSKTOP\networkshare   	
	\\MINECRAFT-SERVER		Minecraft-Server server (Samba, Ubuntu)
Connecting to host=MINECRAFT-SERVER
resolve_lmhosts: Attempting lmhosts lookup for name MINECRAFT-SERVER<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name MINECRAFT-SERVER<0x20>
resolve_wins: Attempting wins lookup for name MINECRAFT-SERVER<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name MINECRAFT-SERVER<0x20>
resolve_hosts: getaddrinfo failed for name MINECRAFT-SERVER [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name MINECRAFT-SERVER<0x20>
Got a positive name query response from 192.168.2.112 ( 192.168.2.112 )
Connecting to 192.168.2.112 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\MINECRAFT-SERVER\IPC$           	IPC Service (Minecraft-Server server (Samba, Ubuntu))
		\\MINECRAFT-SERVER\minecraft
```  

What I mean by WINS support is in smb.conf I changed the line that reads "wins support = no" to "wins support = yes"

My router does not support DHCP reservations, nor would I like to use anything like that. I specifically want every PC to remain dynamic. I could easily set "nicholas-dsktop" to a static IP like "192.168.2.111" and be done with this, but that is not what I want.

Thanks for all your help so far, I feel like we are getting close,
-NCB

---

### Post by bab1 on 2012-10-20
> **Cfhs_1 said:**
> ```
resolve_lmhosts: Attempting lmhosts lookup for name NICHOLAS-DSKTOP<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name NICHOLAS-DSKTOP<0x20>
resolve_wins: Attempting wins lookup for name NICHOLAS-DSKTOP<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name NICHOLAS-DSKTOP<0x20>
resolve_hosts: getaddrinfo failed for name NICHOLAS-DSKTOP [No address associated with hostname]
[B]name_resolve_bcast: Attempting broadcast lookup for name NICHOLAS-DSKTOP<0x20>
Got a positive name query response from 192.168.2.5 ( 192.168.2.5 )
Connecting to 192.168.2.5 at port 445
```[/B]

Did you really change the name resolve order to this ```
name resolve order = bcast
```
Looking at the above section of debug you can see that the system is resolving the name via bcast, but only after trying all the other methods. I can see that it finds the master browser and all names are resolved.>  

What I mean by WINS support is in smb.conf I changed the line that reads "wins support = no" to "wins support = yes"
This only says use the WINS server.  Did you define a WINS server?  The debug specifically says it can't find one.

Did you reboot this machine or reload the smbd daemon?

---

### Post by JKyleOKC on 2012-10-20
Yep, he's getting very close. Once the "name resolve order" line is correct and the WINS line is back to "no" it should work properly. I'm bowing out since bab1 has fully addressed the OP's desire...

---

### Post by Cfhs_1 on 2012-10-21
> **bab1 said:**
> Did you really change the name resolve order to this ```
name resolve order = bcast
```
Looking at the above section of debug you can see that the system is resolving the name via bcast, but only after trying all the other methods. I can see that it finds the master browser and all names are resolved.This only says use the WINS server.  Did you define a WINS server?  The debug specifically says it can't find one.

Did you reboot this machine or reload the smbd daemon?

Okay, I changed WINS support back to no, triple checked that my name resolve line only reads "name resolve order = bcast" which it does. rebooted my machine to ensure smbd was reloaded, but every time I regenerate the debug it still says it's using all of the other methods before bcast. Also, now every time I use the "sudo" command my machine says "sudo: unable to resolve host nicholas-dsktop"

Any clue what is going on? I'm 100% positive I have it set to just bcast.

Thanks,
NCB

---

### Post by bab1 on 2012-10-21
> **Cfhs_1 said:**
> Okay, I changed WINS support back to no, triple checked that my name resolve line only reads "name resolve order = bcast" which it does. rebooted my machine to ensure smbd was reloaded, but every time I regenerate the debug it still says it's using all of the other methods before bcast. 
Post the output of these please```
cat /etc/samba/smb.conf

pgrep -l mbd
```> 

Also, now every time I use the "sudo" command my machine says "sudo: unable to resolve host nicholas-dsktop"
This is strange.  The sudo command requires the hostname to match an entry in the /etc/hosts file.  Post the output of these to commands```
cat /etc/hosts

hostname
```> 

Any clue what is going on? I'm 100% positive I have it set to just bcast.

Thanks,
NCB

The problem is related to name services for sure.  You should be able to use any NETBIOS name and Samba without interfering with hosts naming (DNS names) for other services.  What do you get with this command```
ping nicholas-dsktop
```

---

### Post by Cfhs_1 on 2012-10-21
> **bab1 said:**
> Post the output of these please```
cat /etc/samba/smb.conf

pgrep -l mbd
```This is strange.  The sudo command requires the hostname to match an entry in the /etc/hosts file.  Post the output of these to commands```
cat /etc/hosts

hostname
```

The problem is related to name services for sure.  You should be able to use any NETBIOS name and Samba without interfering with hosts naming (DNS names) for other services.  What do you get with this command```
ping nicholas-dsktop
```

cat /etc/samba/smb.conf:
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
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

netbios name = nicholas-dsktop
# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = bcast

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
	username map = /etc/samba/smbusers
	security = user
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

[networkshare]
	path = /media/networkshare
	writeable = yes
;	browseable = yes
#	valid users = nicholas
	force user = nicholas
```

pgrep -l mbd:
```
Gives no output
```

cat /etc/hosts:
```
127.0.0.1	localhost
127.0.1.1	nicholas-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

hostname:
```
nicholas-dsktop
```

ping nicholas-dsktop:
```
ping: unknown host nicholas-dsktop
```

---

### Post by bab1 on 2012-10-21
> **Cfhs_1 said:**
> cat /etc/samba/smb.conf:
```

netbios name = nicholas-dsktop
# What naming service and in what order should we use to resolve host names
# to IP addresses
**[COLOR="Red"];[/COLOR]**   name resolve order = bcast

```
You left the comment marker (**[COLOR="Red"][SIZE="2"];[/SIZE][/COLOR]**) in front of the line above.  Remove it so the line acutally is used. > 

pgrep -l mbd:
```
Gives no output
```
Let's try this in a different way.  Post the output of this```
ps -ef|grep mbd
```> 

cat /etc/hosts:
```
127.0.0.1	localhost
127.0.1.1	nicholas-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```
This is good.> 
hostname:
```
nicholas-dsktop
```
This is very wrong.  Return this back to what it was originally (nicholas-desktop).  Changing the hostname is what killed your sudo.  The hostname is NOT the NETBIOS (COMPUTER) name.>  

ping nicholas-dsktop:
```
ping: unknown host nicholas-dsktop
```
At this point this is probably ok.

To summarize: Uncomment the name resolve line and return the hostname to its original name.

---

### Post by Cfhs_1 on 2012-10-21
> **bab1 said:**
> You left the comment marker (**[COLOR="Red"][SIZE="2"];[/SIZE][/COLOR]**) in front of the line above.  Remove it so the line acutally is used. Let's try this in a different way.  Post the output of this```
ps -ef|grep mbd
```This is good.This is very wrong.  Return this back to what it was originally (nicholas-desktop).  Changing the hostname is what killed your sudo.  The hostname is NOT the NETBIOS (COMPUTER) name.
At this point this is probably ok.

To summarize: Uncomment the name resolve line and return the hostname to its original name.

ps -ef|grep mbd:
```
root       778     1  0 16:10 ?        00:00:00 smbd -F
root       784   778  0 16:10 ?        00:00:00 smbd -F
root      1568     1  0 16:10 ?        00:00:00 nmbd -D
nicholas  2313  2202  0 16:20 pts/0    00:00:00 grep --color=auto mbd

```

I've made the other suggested changes, and rebooted. Still cannot access it from Windows.
NCB

---

### Post by bab1 on 2012-10-21
> **Cfhs_1 said:**
> ps -ef|grep mbd:
```
root       778     1  0 16:10 ?        00:00:00 smbd -F
root       784   778  0 16:10 ?        00:00:00 smbd -F
root      1568     1  0 16:10 ?        00:00:00 nmbd -D
nicholas  2313  2202  0 16:20 pts/0    00:00:00 grep --color=auto mbd

```

I've made the other suggested changes, and rebooted. Still cannot access it from Windows.
NCBWhat do we get from ```
smbtree -d3
```

[COLOR="Blue"]EDIT: Can you sudo now?[/COLOR]

---

### Post by Cfhs_1 on 2012-10-21
> **bab1 said:**
> What do we get from ```
smbtree -d3
```

```
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.2.6 ( 192.168.2.6 )
Connecting to host=192.168.2.6
Connecting to 192.168.2.6 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.2.6 ( 192.168.2.6 )
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.2.6 ( 192.168.2.6 )
Connecting to host=192.168.2.6
Connecting to 192.168.2.6 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.2.6 ( 192.168.2.6 )
Connecting to host=192.168.2.6
Connecting to 192.168.2.6 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\NICHOLAS-LAPTOP		
Connecting to host=NICHOLAS-LAPTOP
name_resolve_bcast: Attempting broadcast lookup for name NICHOLAS-LAPTOP<0x20>
cli_start_connection: failed to connect to NICHOLAS-LAPTOP<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\NICHOLAS-DSKTOP		nicholas-desktop server (Samba, Ubuntu)
Connecting to host=NICHOLAS-DSKTOP
name_resolve_bcast: Attempting broadcast lookup for name NICHOLAS-DSKTOP<0x20>
Got a positive name query response from 192.168.2.6 ( 192.168.2.6 )
Connecting to 192.168.2.6 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\NICHOLAS-DSKTOP\File Server    	File Server on Nicholas-Desktop
		\\NICHOLAS-DSKTOP\IPC$           	IPC Service (nicholas-desktop server (Samba, Ubuntu))

```

---

### Post by bab1 on 2012-10-21
> **Cfhs_1 said:**
> ```
..
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\NICHOLAS-LAPTOP		
Connecting to host=NICHOLAS-LAPTOP
name_resolve_bcast: Attempting broadcast lookup for name NICHOLAS-LAPTOP<0x20>
cli_start_connection: failed to connect to NICHOLAS-LAPTOP<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\NICHOLAS-DSKTOP		nicholas-desktop server (Samba, Ubuntu)
Connecting to host=NICHOLAS-DSKTOP
name_resolve_bcast: Attempting broadcast lookup for name NICHOLAS-DSKTOP<0x20>
Got a positive name query response from 192.168.2.6 ( 192.168.2.6 )
Connecting to 192.168.2.6 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\NICHOLAS-DSKTOP\File Server    	File Server on Nicholas-Desktop
		\\NICHOLAS-DSKTOP\IPC$           	IPC Service (nicholas-desktop server (Samba, Ubuntu))

```

Please post the output of ```
smbclient -L NICHOLAS-DSKTOP
```

Are you browsing "network neighborhood" or trying to mount a specific known share?

---

### Post by Cfhs_1 on 2012-10-21
> **bab1 said:**
> Please post the output of ```
smbclient -L NICHOLAS-DSKTOP
```

Are you browsing "network neighborhood" or trying to mount a specific known share?

smbclient -L NICHOLAS-DSKTOP:
```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (nicholas-desktop server (Samba, Ubuntu))
	networkshare    Disk      Network Storage on Nicholas-Desktop
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	MATT-LAPTOP          
	NICHOLAS-DSKTOP      nicholas-desktop server (Samba, Ubuntu)
	NICHOLAS-LAPTOP      

	Workgroup            Master
	---------            -------
	WORKGROUP            NICHOLAS-DSKTOP
```

I've tried both methods everytime, neither work.

---

### Post by bab1 on 2012-10-21
> **Cfhs_1 said:**
> smbclient -L NICHOLAS-DSKTOP:
```
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (nicholas-desktop server (Samba, Ubuntu))
	networkshare    Disk      Network Storage on Nicholas-Desktop
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

	Server               Comment
	---------            -------
	MATT-LAPTOP          
	NICHOLAS-DSKTOP      nicholas-desktop server (Samba, Ubuntu)
	NICHOLAS-LAPTOP      

	Workgroup            Master
	---------            -------
	WORKGROUP            NICHOLAS-DSKTOP
```

I've tried both methods everytime, neither work.

From the above it appears that the Ubuntu host (NICHOLAS-DSKTOP) is working.  As a matter of fact it is serving as the Master Browser database for the network.  I think your problem is with the WIndows machine.  It may have a FW that is blocking Samba (CIFS).  What is MATT_LAPTOP?  Is that a visitor to the network?  It appears to have shares or at least it is broadcasting its NETBIOS name.  From NICHOLAS-DSKTOP can you browse shares on MATT-LAPTOP?  Can you browse shares on  NICHOLAS-DSKTOP from MATT-LAPTOP?

---

### Post by Cfhs_1 on 2012-10-21
> **bab1 said:**
> From the above it appears that the Ubuntu host (NICHOLAS-DSKTOP) is working.  As a matter of fact it is serving as the Master Browser database for the network.  I think your problem is with the WIndows machine.  It may have a FW that is blocking Samba (CIFS).  What is MATT_LAPTOP?  Is that a visitor to the network?  It appears to have shares or at least it is broadcasting its NETBIOS name.  From NICHOLAS-DSKTOP can you browse shares on MATT-LAPTOP?  Can you browse shares on  NICHOLAS-DSKTOP from MATT-LAPTOP?

I turned NICHOLAS-LAPTOP's FW off, still no access. I cannot access anything on "MATT-LAPTOP" from "NICHOLAS-DSKTOP" I CAN however access "NICHOLAS-DSKTOP" from "MATT-LAPTOP" through both directly entering it's name in explorer, and browsing the network. "MATT-LAPTOP" is a windows client. This seems to mean that the problem is actually my windows client, "NICHOLAS-LAPTOP" What could it be?
NCB

---

### Post by bab1 on 2012-10-21
> **Cfhs_1 said:**
> I turned NICHOLAS-LAPTOP's FW off, still no access. I cannot access anything on "MATT-LAPTOP" from "NICHOLAS-DSKTOP" I CAN however access "NICHOLAS-DSKTOP" from "MATT-LAPTOP" through both directly entering it's name in explorer, and browsing the network. "MATT-LAPTOP" is a windows client. This seems to mean that the problem is actually my windows client, "NICHOLAS-LAPTOP" What could it be?
NCB

I don't admin Windows machines so I wouldn't have a clue.  The Windows laptop I have is Vista and I just made sure was capable of browsing the network when I acquired it.  Vista worked right out of the box.

Just to be sure here; you are saying that you *can* browse "network neighborhood" and see NICHOLAS-DSKTOP from MATT-LAPTOP.  If this is correct then you have achived what you started out to do with this thread (e.g. Make NICHOLAS-DSKTOP broadcast its presence by name on the network with a dynamic IP address).  

I would try one of the Win7 forums or start a new thread at this forum to answer your just revealed problem with your Windows laptop.  Out of curiosity, can the laptops see the other?

---

### Post by Cfhs_1 on 2012-10-21
> **bab1 said:**
> I don't admin Windows machines so I wouldn't have a clue.  The Windows laptop I have is Vista and I just made sure was capable of browsing the network when I acquired it.  Vista worked right out of the box.

Just to be sure here; you are saying that you *can* browse "network neighborhood" and see NICHOLAS-DSKTOP from MATT-LAPTOP.  If this is correct then you have achived what you started out to do with this thread (e.g. Make NICHOLAS-DSKTOP broadcast its presence by name on the network with a dynamic IP address).  

I would try one of the Win7 forums or start a new thread at this forum to answer your just revealed problem with your Windows laptop.  Out of curiosity, can the laptops see the other?

Thanks for all your help! "MATT-LAPTOP" can see "NICHOLAS-LAPTOP" but "NICHOLAS-LAPTOP" can only see it's self.
NCB

---

### Post by bab1 on 2012-10-21
> **Cfhs_1 said:**
> Thanks for all your help! "MATT-LAPTOP" can see "NICHOLAS-LAPTOP" but "NICHOLAS-LAPTOP" can only see it's self.
NCB
Well that confirms it.  You need to fix NICHOLAS-LAPTOP before it can see any shares.

BTW - You are the first person I have found on this forum that wanted to use DHCP and broadcasting NETBIOS names for name resolution.  I knew it would work but I had never set it up with Ubuntu before.  It certainly is easier than setting up dynamic name resolution with DNS. :D

---

### Post by Cfhs_1 on 2012-10-21
> **bab1 said:**
> Well that confirms it.  You need to fix NICHOLAS-LAPTOP before it can see any shares.

BTW - You are the first person I have found on this forum that wanted to use DHCP and broadcasting NETBIOS names for name resolution.  I knew it would work but I had never set it up with Ubuntu before.  It certainly is easier than setting up dynamic name resolution with DNS. :D

Thanks for all your help, I couldn't have gotten this done without you. I think I'm just going to reinstall windows on my Laptop as it is clearly the problem here. I can access "NICHOLAS-DSKTOP" from both "MATT-LAPTOP" as well as my other ubuntu box. "NICHOLAS-LAPTOP" is the only one that cannot access anything.
NCB

---

### Post by bab1 on 2012-10-21
> **Cfhs_1 said:**
> Thanks for all your help, I couldn't have gotten this done without you. I think I'm just going to reinstall windows on my Laptop as it is clearly the problem here. I can access "NICHOLAS-DSKTOP" from both "MATT-LAPTOP" as well as my other ubuntu box. "NICHOLAS-LAPTOP" is the only one that cannot access anything.
NCB

Reinstalling might be the fastest as we know that the other Windows machines work.  Good luck.  

Write down what we did so you can refer to it if you want to configure the other Ubuntu host you have.  Remember this only works for Samba.  I don't know of any other apps that use NETBIOS for name rez.

---

