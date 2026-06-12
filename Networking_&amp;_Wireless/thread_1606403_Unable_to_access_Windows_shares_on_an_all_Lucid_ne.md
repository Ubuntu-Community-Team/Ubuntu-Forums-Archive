---
title: "Unable to access Windows shares on an all Lucid network"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by Mylorharbour on 2010-10-26
[I][COLOR="Navy"]I marked this solved when I discovered, after much reconfiguring, I had a faulty Netgear router - I just thought I'd save you reading all this to find the answer. Cheers
[/COLOR][/I]
I have 3 machines at home all running Lucid. All have Samba and shared folders but I can't access files on any machine from any other. This worked ok when they were running Karmic. I'm also unable to set up printing across the network from the two machines without local printers. The main machine has 2 printers connected via USB, the others are using WiFi. I'm not using firewalls on any machine.

Filesharing
On any machine I go to Places, Network and Nautilus opens at network:/// and shows me 'Windows Network' I open that and see the Workgroup folder which I open and see the folder is empty. (I did see the 3 machines before I completely removed Samba and re-installed a few minutes ago)

Printing
On one of the remote machines I go to Add Printer, Select Device, Network Printer, Windows Printer via Samba, Browse but I can't see the machine with the printers attached in the Workgroup. Another clue is that when I look at the printer properties, policies on the main machine all 3 boxes are ticked, Enabled, Accepting jobs (but it says Not published) and Shared.

Basically guys, the more things I try the worse it gets. Can someone put me right?

---

### Post by Morbius1 on 2010-10-26
Pick one machine ... say the one with the printer ... and make sure the following services are running:
```
sudo service cups status
sudo service nmbd status
sudo service smbd status

```If any of them are not running start them:
```
sudo service cups start
sudo service nmbd start
sudo service smbd start
```Check to see if anything has changed and if not post the output of the following commands:
```
smbtree
``````
net usershare info
``````
testparm -s
```

---

### Post by d3v1150m471c on 2010-10-26
please post the output of the following commands:
```

cat /etc/samba/smb.conf


nmblookup -A 192.168.1.0/24 # assuming your gateway is 192.168.1.1, adjust appropriately

smbclient -L {one of the hostnames from previous command} -I {that machine's ip}

```

---

### Post by Mylorharbour on 2010-10-26
Morbius1,
Some output for you.....

Status of Common Unix Printing System: cupsd is running.
roy@HPdc7700:~$ sudo service nmbd status
nmbd start/running, process 992
roy@HPdc7700:~$ sudo service smbd status
smbd start/running, process 866
roy@HPdc7700:~$ smbtree
Enter roy's password: 
WORKGROUP
	\\HPDC7700       		HPdc7700 server (Samba, Ubuntu)
		\\HPDC7700\shared         	
		\\HPDC7700\IPC$           	IPC Service (HPdc7700 server (Samba, Ubuntu))
		\\HPDC7700\print$         	Printer Drivers
	\\DELL-INSPIRON-L		Dell-Inspiron-Laptop server (Samba, Ubuntu)
cli_start_connection: failed to connect to DELL-INSPIRON-L<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
roy@HPdc7700:~$ 
roy@HPdc7700:~$ net usershare info
roy@HPdc7700:~$ 
roy@HPdc7700:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Global parameter usershare allow guests found in service section!
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

---

### Post by Mylorharbour on 2010-10-26
d3v1150m471c,
Some for you too. How do I go about finding gateways and IPs?

oy@HPdc7700:~$ cat /etc/samba/smb.conf
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
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

[ printers]

comment = All Printers
path = /var/spool/samba
browseable = no
printable = yes

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

[printers]
   comment = All Printers
   browseable = no
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

---

### Post by Morbius1 on 2010-10-26
[1] Well, for one thing you have no shares defined. 

"net usershare info" would have told us how your usershares or nautilus-shares are defined and the output os null. And testparm -s would have told us if you have any classic shares and there aren't any of those either.

[2] If you're going to use Samba as pass-through to cups you need to make a modification of your smb.conf:
> [printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   **[COLOR=Blue]guest ok = yes[/COLOR]**
   read only = yes
   create mask = 0700[3] Your machine name is too long
> [COLOR=Black]\\DELL-INSPIRON-L[/COLOR]        **[COLOR=Blue]Dell-Inspiron-Laptop[/COLOR]** server (Samba, Ubuntu)
cli_start_connection: failed to connect to DELL-INSPIRON-L<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFULBy default samba will use the hostname to anounce itself to the network but it has to be less than or equal to 15 characters in length.

The fastest way to fix this is to add a line to the [global] section of smb.conf:
```
netbios name = Dell-Laptop
```It doesn't have to be that exact name but make it <= 15 characters in length.
[COLOR=Blue]**EDIT:**[/COLOR] Sorry, I should have been clearer about where to make that change. It should be none on [COLOR=Black]**Dell-Inspiron-Laptop**[/COLOR]'s smb.conf not on **HPdc7700.**

Then restart samba:
```
sudo service smbd restart
```

---

### Post by Morbius1 on 2010-10-26
There are two things from your output that I just can't figure out:

[1] "net usershare" and testparm show no shares yet smbtree show this:
>          \\HPDC7700\shared             Is that by any chance the printer? Or did you create a nautilus-share as root. If you do the following command do you get an output:
```
sudo net usershare info
```[2] testparm error:
>  Global parameter usershare allow guests found in service section!For the life of me the only reference to it in your smb.conf is where it should be.

---

### Post by d3v1150m471c on 2010-10-26
```

ifconfig # will tell you your ip

```

your router's ip address is your gateway. don't mistake this for your modem. if you don't know your router's ip you can right-click your network tray icon and go into connection information (while connected) and it will be your "default route". it'll probably be something like 192.168.1.1

please see my responses on this thread as it may tell you what you need to know.
[URL="http://ubuntuforums.org/showthread.php?p=10022515#post10022515"]
http://ubuntuforums.org/showthread.php?p=10022515#post10022515[/URL]

 it contains my additions to smb.conf (that file is otherwise not modified) and I touched on nautilus-share as well. i use my firewall to manage my samba security because it's easier especially with the dhcp on my network and sometimes the windows machines i share with have a myocardial infarction when they've encountered my samba security in the past.

---

### Post by Mylorharbour on 2010-10-26
> **d3v1150m471c said:**
> please post the output of the following commands:
```

cat /etc/samba/smb.conf


nmblookup -A 192.168.1.0/24 # assuming your gateway is 192.168.1.1, adjust appropriately

smbclient -L {one of the hostnames from previous command} -I {that machine's ip}

```

Hmmm.... My router's address is 192.168.0.1. Is that the gateway you refer to? I have a couple of listing but I don't think they're what you're after:

roy@HPdc7700:~$ nmblookup -A 192.168.0.0/24
Looking up status of 0.0.0.0
	HPDC7700        <00> -         B <ACTIVE> 
	HPDC7700        <03> -         B <ACTIVE> 
	HPDC7700        <20> -         B <ACTIVE> 
	..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 
	WORKGROUP       <1d> -         B <ACTIVE> 
	WORKGROUP       <1e> - <GROUP> B <ACTIVE> 
	WORKGROUP       <00> - <GROUP> B <ACTIVE> 

	MAC Address = 00-00-00-00-00-00

roy@HPdc7700:~$ nmblookup -A 192.168.1.0/24
Looking up status of 0.0.0.0
	HPDC7700        <00> -         B <ACTIVE> 
	HPDC7700        <03> -         B <ACTIVE> 
	HPDC7700        <20> -         B <ACTIVE> 
	..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 
	WORKGROUP       <1d> -         B <ACTIVE> 
	WORKGROUP       <1e> - <GROUP> B <ACTIVE> 
	WORKGROUP       <00> - <GROUP> B <ACTIVE> 

	MAC Address = 00-00-00-00-00-00

---

### Post by Mylorharbour on 2010-10-26
Sorry guys I'm about to lose access this machine. The shift worker's arrived home and it's in her bedroom. I'll pick this up again in the morning. Cheers.

---

### Post by d3v1150m471c on 2010-10-26
> **Mylorharbour said:**
> 

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No


you have two instances of browseable, one of which is missing the "e" before the "a".

i don't know from nautilus but your terminal doesn't seem to be picking up the other 2 computers when you issued the nmblookup command. somewhere along the lines they are not communicating. i have to ask, your other two lucid computers were running and connected at the time you issued the command, right? if not you'll have to try it as such.


you said you weren't behind a firewall but posting the output of the following to double check is good:
```

sudo iptables -L

```

if you scroll up i posted a link to a similar thread i posted on. please examine my additions to the samba setup. try using those, if not temporarily, to see if they work out.

---

### Post by Morbius1 on 2010-10-26
> **d3v1150m471c said:**
> you have two instances of browseable, one of which is missing the "e" before the "a". 
That's normal an a quirk of testparm when it interprets the smb.conf. If you notice it's not in his output of cat /etc/samba/smb.conf so there is nothing to fix. If you ran testparm on your own machine you would no doubt find the same  thing.

> somewhere along the lines they are not communicating. One of the missing machines is due to the hostname being greater than 15 characters long.

As for the firewall I would also like to suggest the following procedure:
Install and run nmap:
```
sudo apt-get install nmap
``````
sudo nmap -sS -sU -T4 192.168.0.100
```Run it 3 times changing 192.168.0.100 to the ip address of each of the machines. It will display the open ports on each of those machines. You will need the following ports open for samba / cups to work:
> 139, 445, 631 tcp
137, 138, 631 udp

---

### Post by Mylorharbour on 2010-10-27
[B]Morbius1,
[/B]
I carried out 2) and 3) from post #6 and restarted samba on both machines. No difference I'm afraid.

\\HPDC7700\shared is a shared partition, shared between Windows and Ubuntu (dual boot machine).

[INDENT]roy@HPdc7700:~$ sudo net usershare info
[sudo] password for roy: 
[shared]
path=/media/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=n
[/INDENT]

[B]
d3v1150m471c,[/B]

roy@HPdc7700:~$ ifconfig #
eth0      Link encap:Ethernet  HWaddr 00:0f:fe:63:98:da  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:feff:fe63:98da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:221959 (221.9 KB)  TX bytes:53328 (53.3 KB)
          Memory:e0400000-e0420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14680 (14.6 KB)  TX bytes:14680 (14.6 KB)

Guys,
I'll post again shortly when I've followed up some of your other suggestions.

---

### Post by Mylorharbour on 2010-10-27
[B]d3v1150m471c,
[/B]

roy@HPdc7700:~$ sudo iptables -L
[sudo] password for roy: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


I'll have a look at your link, cheers.

---

### Post by Morbius1 on 2010-10-27
[1] Make sure you restart samba everytime you make changes to smb.conf:
> sudo service smbd restart[2] If you run the following command again:
```
smbtree
```Does it now show all of your shares on HPdc7700 and Dell-Laptop ( or whatever you renamed it to ). Or at least is it running without errors?

[3] You say this share is shared between Windows and Linux in a dual boot:
> [shared]
    path=/media/Shared
    comment=
    usershare_acl=Everyone:F,
    guest_ok=nI'm going to guess that you do not have that partition automounted in fstab but mount it as you need it by going to Nautilus. If that's so then the remote user will never see it because the permissions are incorrect.

My recommendation is to add 2 more lines to your smb.conf in the [COLOR=Blue]**[global]**[/COLOR] section:
```
usershare allow guests = yes
force user = roy
```Save smb.conf and then restart samba again:
```
sudo service smbd restart
```Now go back into Nautilus as gksu and check on the "Guest Access" box in Sharing Options for /media/Shared.

And see if there is any change.

---

### Post by Mylorharbour on 2010-10-27
Morbius1,
I installed Nmap as requested:

192.168.0.5 is the HPdc7700 with local printers (USB)
192.168.0.2 is the Dell Inspiron
192.168.0.4 is the wife's Asus Eee

Ignore the blue stats. I pressed return a couple of times as I thought it may have crashed.

roy@HPdc7700:~$ sudo nmap -sS -sU -T4 192.168.0.5

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-10-27 21:50 BST
Interesting ports on 192.168.0.5:
Not shown: 1994 closed ports
PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
68/udp   open|filtered dhcpc
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.45 seconds
roy@HPdc7700:~$ 
roy@HPdc7700:~$ sudo nmap -sS -sU -T4 192.168.0.2

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-10-27 21:51 BST
Warning: Giving up on port early because retransmission cap hit.
[COLOR="Blue"]Stats: 0:01:03 elapsed; 0 hosts completed (1 up), 1 undergoing UDP Scan
UDP Scan Timing: About 10.89% done; ETC: 22:00 (0:08:28 remaining)
Stats: 0:05:38 elapsed; 0 hosts completed (1 up), 1 undergoing UDP Scan
UDP Scan Timing: About 38.97% done; ETC: 22:05 (0:08:48 remaining)
[/COLOR]Interesting ports on 192.168.0.2:
Not shown: 1983 closed ports
PORT      STATE         SERVICE
22/tcp    open          ssh
139/tcp   open          netbios-ssn
445/tcp   open          microsoft-ds
68/udp    open|filtered dhcpc
137/udp   open|filtered netbios-ns
138/udp   open|filtered netbios-dgm
502/udp   open|filtered asa-appl-proto
593/udp   open|filtered http-rpc-epmap
1026/udp  open|filtered win-rpc
5353/udp  open|filtered zeroconf
17302/udp open|filtered unknown
20313/udp open|filtered unknown
20876/udp open|filtered unknown
21303/udp open|filtered unknown
21524/udp open|filtered unknown
33249/udp open|filtered unknown
60381/udp open|filtered unknown
MAC Address: 00:13:02:26:8A:C5 (Intel Corporate)

Nmap done: 1 IP address (1 host up) scanned in 979.14 seconds
roy@HPdc7700:~$ 
roy@HPdc7700:~$ 
roy@HPdc7700:~$ sudo nmap -sS -sU -T4 192.168.0.4
[sudo] password for roy: 

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-10-27 22:11 BST
Warning: Giving up on port early because retransmission cap hit.
Interesting ports on 192.168.0.4:
Not shown: 1984 closed ports
PORT      STATE         SERVICE
139/tcp   open          netbios-ssn
445/tcp   open          microsoft-ds
68/udp    open|filtered dhcpc
137/udp   open|filtered netbios-ns
138/udp   open|filtered netbios-dgm
500/udp   open|filtered isakmp
688/udp   open|filtered unknown
903/udp   open|filtered unknown
1080/udp  open|filtered socks
5353/udp  open|filtered zeroconf
5555/udp  open|filtered rplay
17332/udp open|filtered unknown
19273/udp open|filtered unknown
21742/udp open|filtered unknown
22045/udp open|filtered unknown
52225/udp open|filtered unknown
MAC Address: 00:15:AF:BD:7C:91 (AzureWave Technologies)

Nmap done: 1 IP address (1 host up) scanned in 996.55 seconds

---

### Post by Morbius1 on 2010-10-27
You have the requisite ports open for samba but you don't have them open for cups and that's your printer. If it's ok with you let's leave that for last because there is already too much going on here.

Let's just make sure that smbtree from HPdc7700 can see everyone without generating errors.

That /media/Shared directory is still confusing me. Can you post the output of the following:
```
ls -dl /media/Shared
```

---

### Post by Mylorharbour on 2010-10-27
Morbius1,

Some errors for you....

roy@HPdc7700:~$ sudo service smbd restart
[sudo] password for roy: 
smbd start/running, process 2275
roy@HPdc7700:~$ 
roy@HPdc7700:~$ smbtree
Enter roy's password: 
WORKGROUP
	\\WENDY-LAPTOP   		wendy-laptop server (Samba, Ubuntu)
cli_start_connection: failed to connect to WENDY-LAPTOP<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\HPDC7700       		HPdc7700 server (Samba, Ubuntu)
		\\HPDC7700\shared         	
		\\HPDC7700\deskjet-5550   	hp deskjet 5550
		\\HPDC7700\Stylus-Photo-R220	EPSON Stylus Photo R220
		\\HPDC7700\IPC$           	IPC Service (HPdc7700 server (Samba, Ubuntu))
		\\HPDC7700\print$         	Printer Drivers
	\\DELL-LAPTOP    		Dell-Inspiron-Laptop server (Samba, Ubuntu)
cli_start_connection: failed to connect to DELL-LAPTOP<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
roy@HPdc7700:~$ 


/media/shared is an NTFS partition only shared between Windows and Ubuntu, whichever OS I boot up, on the HP. It's not shared across the network. It contains home video files mainly which are edited by Windows and Ubuntu apps.

I haven't added the 'usershare' code to smb.conf for that reason. Presumably this would do the same as right-clicking on the folder in Nautilus and ticking the box in Properties, Share?

---

### Post by Mylorharbour on 2010-10-27
As requested but see my previous post as I don't think it's relevant to this networking issue.

roy@HPdc7700:~$ ls -dl /media/Shared
drwxrwxrwx 1 root root 4096 2010-10-23 12:46 /media/Shared

---

### Post by Morbius1 on 2010-10-27
You are sharing /media/Shared across the network:
> \\HPDC7700               HPdc7700 server (Samba, Ubuntu)
        [COLOR=Blue]\\HPDC7700\shared[/COLOR]             > sudo net usershare info
[sudo] password for roy: 
[[COLOR=Blue]shared[/COLOR]]
path=[COLOR=Blue]/media/Shared[/COLOR]
comment=
usershare_acl=Everyone:F,
guest_ok=n> I haven't added the 'usershare' code to smb.conf for that reason.  Presumably this would do the same as right-clicking on the folder in  Nautilus and ticking the box in Properties, Share?     userhare allow guests enables nautilus-share to grant guest access. Without it "Guest Access" would be grayed out.

Let me think a bit about the latest smbtree output.

---

### Post by Morbius1 on 2010-10-27
From HPdc7700 run the following command and tell me what happens:

```
nautilus smb://192.168.0.2
```If it actually opens up Dell-Laptop without errors do it in reverse:

From Dell-Laptop:

```
nautilus smb://192.168.0.5
```And tell me if HPdc7700 opens up without errors.

---

### Post by Mylorharbour on 2010-10-27
Should I add the 'usershare' entry to the smb.conf or hang on a bit. I've no objection to /media/shared being shared across the network, it's just that in Nautilus the box isn't ticked in the Properties, Share window. I couldn't say why it shows that way in the listings but it'd be good to tidy it up a bit.

---

### Post by Morbius1 on 2010-10-27
"userhare allow guests = yes" is in the default smb.conf that comes from the factory. Yes it should be there just in case you want to allow guest access on one of your folders someday.

---

### Post by Mylorharbour on 2010-10-27
> Now go back into Nautilus as gksu and check on the "Guest Access" box in Sharing Options for /media/Shared.

Guest access is greyed out and unticked.

Running the Nautilus command from the HP allow me to access the shared folders on the Dell fine.

When I do the same from the Dell I see just print$ and shared (lower case 's'). I double click on shared and am asked to enter the password but I can't get in, it just returns to the password window.

Note, I can't recall setting any sharing on HP folders. The Dell's my main machine nowadays so I tend to pull files from there to the HP. I just tried to share an NTFS folder though using Properties, Share but get this message:

[COLOR="Blue"]'net usershare' returned error 255: net usershare add: cannot share path /media/Video_XP as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.[/COLOR]

---

### Post by Morbius1 on 2010-10-28
[1]
> [QUOTE]Now go back into Nautilus as gksu and check on the "Guest Access" box in Sharing Options for /media/Shared.Guest access is greyed out and unticked.[/QUOTE]Because you didn't add:
```
usershare allow guests = yes
```To the global section of smb.conf and restart samba

[2]
> When I do the same from the Dell I see just print$ and shared (lower  case 's'). I double click on shared and am asked to enter the password  but I can't get in, it just returns to the password window.It's asking you for a password because that's the way you set up the share:
> [QUOTE][SIZE=1]\\HPDC7700               HPdc7700 server (Samba, Ubuntu)
[/SIZE]         [SIZE=1][COLOR=Blue]\\HPDC7700\shared[/COLOR][/SIZE]             > sudo net usershare info
[sudo] password for roy: 
[[COLOR=Blue]shared[/COLOR]]
path=[COLOR=Blue]/media/Shared[/COLOR]
comment=
usershare_acl=Everyone:F,
guest_ok=n[/QUOTE]See [1] above.

[3] 
> I just tried to share an NTFS folder though using Properties, Share but get this message:
[COLOR=Blue]'net usershare' returned error 255: net usershare  add: cannot share path /media/Video_XP as we are restricted to only  sharing directories we own.
    Ask the administrator to add the line "usershare owner only = false" 
    to the [global] section of the smb.conf to allow this.[/COLOR]That may be the greatest error message in the history of computers and software. It not only tells you the nauture of the problem but it tells you exactly how to fix it:
Open up the smb.conf on the Dell and add the following line to the [global] section of smb.conf:
```
usershare owner only = false
```Then restart samba

---

### Post by Mylorharbour on 2010-10-28
Morbius1,

Thanks for bearing with me.

My smb.conf listing in post #5 shows the usershare line was there originally but I've added the others you mentioned plus the error message command to the HP and Dell smb.conf files, restarted samba and have since rebooted both machines. Here is the current 'global section' for you to check I did it right as I'm not sure about the ';' at the start of each command line.

[COLOR="Blue"]
#======================= Global Settings =======================


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
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

[ printers]

comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
guest ok = yes
read only = yes
create mask = 0700 

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
;   usershare allow guests = yes
;   force user = roy
;   usershare owner only = false
[/COLOR]

Using 'nautilus smb://' I can browse the Dell from the HP fine but not vice-versa. To clarify the 'password' comment, when I attempt to browse the HP from the Dell Nautilus opens and I can see the shared folders on the HP but when I try to browse one of them I get a 'Password required' window as expected showing Username (roy), Domain (WORKGROUP) and a Password box into which I enter my password. On pressing 'Connect' the Password window flashes and returns for me to enter the password again, and again, and again.

---

### Post by Mylorharbour on 2010-10-28
Just after I posted an Unable to mount location window popped up on the Dell over that Password required window. 

It says 'DBus error org.freedesktop.Dbus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by Morbius1 on 2010-10-28
> [COLOR=Blue]# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
;   usershare allow guests = yes
;   force user = roy
;   usershare owner only = false[/COLOR]Get rid of the ";" at the beginning of the last 3 lines so that it looks like this:
> [COLOR=Blue]# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
  usershare allow guests = yes
  force user = roy
  usershare owner only = false[/COLOR]> To clarify the 'password' comment, when I attempt to browse the HP from  the Dell Nautilus opens and I can see the shared folders on the HP but  when I try to browse one of them I get a 'Password required' window as  expected showing Username (roy), Domain (WORKGROUP) and a Password box  into which I enter my password. On pressing 'Connect' the Password  window flashes and returns for me to enter the password again, and  again, and again.     I don't know how to make this any clearer. It's asking you for a pssword because that's the way you set up the share:
sudo net usershare info
> [sudo] password for roy: 
[[COLOR=Black]shared[/COLOR]]
path=[COLOR=Black]/media/Shared[/COLOR]
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]**guest_ok=n                      **[/COLOR]It looks that way because you need to back into nautilus and and check on "Guest Access". At he moment you cannot do that becasue it is grayed out. It's grayed out because you have a ";" in front of the line that would enable it:
> [COLOR=Blue];   usershare allow guests = yes[/COLOR]

---

### Post by Mylorharbour on 2010-10-28
Ok, done that.

[COLOR="Blue"]# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
usershare allow guests = yes
force user = roy
usershare owner only = false
[/COLOR]

I do know why it's asking for a password and I enter a password but it doesn't seem to want to accept it as it returns me to the password required window again. Presumably that's because of the 'guest_ok=n' line in the usershare configs on the HP? I've added a couple more shares on the HP:


roy@HPdc7700:~$ sudo net usershare info
[maxtor_ext]
path=/media/Maxtor_External
comment=
usershare_acl=Everyone:F,
guest_ok=n

[video_xp]
path=/media/Video_XP
comment=
usershare_acl=Everyone:F,
guest_ok=n

[shared]
path=/media/Shared
comment=
usershare_acl=Everyone:F,
guest_ok=n

I've restarted samba (sudo service smbd restart), opened Nautilus (gksudo nautilus), opened the above folders, Properties, Share but still get a greyed-out Guest access. I'll now reboot and check smb.conf again.

I don't know how this works but as the changes don't seem to have made a difference could there be another smb.conf somewhere? Is there another file pointing samba to smb.conf?

I've searched the filesystem and come up with smb.conf in these folders
/usr/share/doc/nautilus-share/examples (188bytes)
/usr/share/samba (12.1Kb)
/etc/samba (12.3Kb) This is the one I've been editing.

---

### Post by Mylorharbour on 2010-10-28
Rebooted, checked /etc/samba/smb.conf which is as we modified it.
gksudo nautilus, opened a share, Properties, Share, still greyed-ou Guest access.

Would it be possible to edit the text files directly in var/lib/samba/usershares to prove a point? Just guessing as I'm out of my depth really.

Thanks very much for sticking with me. It's now 1.30am here so I'm off to bed. I won't be around for a couple of days as I'm off to a conference in Manchester. I should be back late Sunday.

Thanks again.

---

### Post by Morbius1 on 2010-10-29
Post your entire smb.conf file please:

```
cat /etc/samba/smb.conf
```

---

### Post by Mylorharbour on 2010-10-31
smb.conf as requested:

roy@HPdc7700:~$ cat /etc/samba/smb.conf
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
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

[ printers]

comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
guest ok = yes
read only = yes
create mask = 0700 

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
force user = roy
usershare owner only = false


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

[printers]
   comment = All Printers
   browseable = no
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

roy@HPdc7700:~$ 


It's been a very long day Morbius. Take your time, I'll be back online tomorrow. Thanks

---

### Post by Morbius1 on 2010-11-01
I ran a testparm on your smb.conf posting and once again i get these errors which just made no sense:
> Global parameter usershare allow guests found in service section!
Global parameter usershare owner only found in service section!But I think I finally figured it out. Samba has a quirk in how it constructs and reads a share definition in smb.conf . It starts every share definition with a [*sharename*] but doesn't consider the share definition completed until it reads another [*sharename*].

You have a [printers] share in the wrong place in smb.conf and samba is reading all the usershare parameters as being part of that share instead of reading it as part of the [global] settings.

Go into smb.conf, find the following section, and put a # sign in front of the the [printers] share so that it looks like this:
> ########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
# load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
; printing = bsd
; printcap name = /etc/printcap

# CUPS printing. See also the cupsaddsmb( manpage in the
# cupsys-client package.
; printing = cups
; printcap name = cups

[COLOR=Blue]#[ printers]

#comment = All Printers
#browseable = no
#path = /var/spool/samba
#printable = yes
#guest ok = yes
#read only = yes
#create mask = 0700[/COLOR]While you're in smb.conf go down further until you reach the real [printers] share and change guest ok to yes:
> # Un-comment the following and create the profiles directory to store
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
**[COLOR=Blue]    guest ok = yes[/COLOR]**
   read only = yes
   create mask = 0700Save smb.conf and restart samba:
```
sudo service smbd restart
```

---

### Post by Mylorharbour on 2010-11-05
Apologies Morbius but my wife's new netbook arrived and she wanted it setup to triple boot Win7, Lucid and Maverick. Done now so I'm back.

Ok I did that before the netbook arrived but only now got to test it. Much the same I'm afraid. On the HP I can see the other machines when I go to Places, Network but when I click on them I get a window saying 'Opening "Dell-Laptop"' then after about 20 seconds an error message, 'Unable to Mount Location', 'Failed to retrieve share list from server'.

On the Dell or on the new netbook booted into Maverick, when I go to Places, Network i see 'Windows Network', double-click that and I see 'Workgroup. Double-clicking that I see an 'Opening "Workgroup"' window then after about 20 seconds an error message, 'Unable to Mount Location', 'Failed to retrieve share list from server'.

When trying to set up a printer from the Dell or the Samsung netbook I go to System, Admin, Printing, Select Device, Network Printer, Windows Printer via Samba, the SMB browser shows the Workgroup share but double-clicking on to doesn't do anything.

---

### Post by Mylorharbour on 2011-01-11
Well, yesterday I lost my sanity.

Nearly eight hours following very useful networking threads and at each turn the situation got a little better. Then, when I was almost there........nothing! Nothing at all. Suddenly, when I was reconfiguring smb.conf on one machine not a single PC could see could see any other. How could that be? I went to bed depressed.

Then today, Victory! Something that I didn't find on any networking thread popped into my head. Sometimes we get so engrossed with setting up Ubuntu we fail to check what else could be happening. Only 4 days ago I asked if it could be hardware related then promptly forgot about it but today I proved conclusively it was the router. I just swapped it for a different make and all the networking just burst into life.

Suffice to say if anyone's having issues seeing other computers or printers on the network, especially if their router's a Netgear, they should have a good look at that as part of the diagnosis.

Thanks all for your help. At least I now KNOW my network's set up correctly.

---

### Post by Morbius1 on 2011-01-12
You know it would be very helpful if you could post the make and model of the netgear that didn't work and the make and model of the router that did work.

I'm getting more convinced that a lot of problems people attribute to Samba are really networking problems and I have seen this "swapped out the routers and everything worked" phenomenon before.

---

### Post by Mylorharbour on 2011-01-12
No probs Morbius.

The failed router was a Netgear DG834PN about 3 years old but permanently left on of course. I came across a thread on the internet which mentioned these routers not showing all 'attached devices'. Devices, usually wireless, seem to go missing although they can still access the internet, other machines can't see them. Sure enough, when I looked at the attached devices some were missing from the list.

The replacement was sent by my ISP when I signed up to a 12 month contract some months ago. It's a BT HomeHub 2.0. I'm not sure whether it's marketed outside the UK as  but it must now be the most common router here as BT seem to give 'em away to anybody signing up whether they already have one or not. Wikipedia says 'This model is electronically identical to the Thomson Speedtouch TG797n.' BT are still the biggest phone line provider here.

Thanks again.

---

