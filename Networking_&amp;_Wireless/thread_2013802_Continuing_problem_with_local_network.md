---
title: "Continuing problem with local network"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by jemvyc on 2012-07-01
I have been facing a networking problem since I installed Ubuntu 12.04.  
I have 2 laptops, wired network between them works with XP and with Ubuntu 10.44  but not with Ubuntu 12.04.  The computers are a Compaq Presario 2100 and an Acer Aspire 5315.

The networking specifies DHCP which is a handover from XP and Ubuntu 10.44  I have spent many hours going thru Samba help and manual.  I have run testparm on both and I see very little difference between the results, but 12.04 will not network from either system.  The testparm results are here:

Testparm from Acer Aspire running Ubuntu 12.04:

jim@acer-u12:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[File System]"
WARNING: The security=share option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = MYHOME
	server string = %h server (Samba, Ubuntu)
	security = SHARE
	encrypt passwords = No
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = jim
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
	read only = No

[File System]
	path = /
	read only = No
jim@acer-u12:~$ 


testparm from Compaq Presario 2100 running Ubuntu 10.44:

jim@laptop-u-10:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[File System]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = MYHOME
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
	usershare allow guests = Yes
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

[File System]
	path = /
	read only = No
	guest ok = Yes
jim@laptop-u-10:~$ 

Can anyone see anything to help me get these computer to talk to each other?


Thanks

---

### Post by Morbius1 on 2012-07-01
On the Acer go into /etc/samba/smb.conf and change this:
> security = SHARE
    encrypt passwords = NoTo this:
> security = USER
     encrypt passwords = YesThen restart samba:
```
sudo service smbd restart
```When you restart samba the network has a minor tantrum so wait a few minutes before trying things again.

*BTW, creating a guest share of your entire linux filesystem is insane but that is entirely up to you.*

---

### Post by jemvyc on 2012-07-01
Thanks for the help.  

I tried what you said and I am perplexed.  I edited /etc/samba/smb.conf using gedit, I saved the file and ran restart.  After a few minutes I ran testparm and the entries for security and encrypt passwords had BOTH disappeared.  I tried again and it still gives the same result.  I have gone back and looked at /etc/samba/smb.conf and my (your) changes are there.  Further, when I try to access network it just runs for a while and then presents an error message.

How can that be?

Jim

---

### Post by Morbius1 on 2012-07-01
> After a few minutes I ran testparm and the entries for security and encrypt passwords had BOTH disappearedActually, that's normal and as it should be,

Smb.conf is a list of additions and overrides to the default settings of samba. When you run testparm you are looking at the affect smb.conf has on the defaults. As it turns out "security = USER" and "encrypt passwords = Yes" are the defaults so testparm should return nothing for those parameters.

Anyway, what error message does it display?

You might want to post the output of the following command from whatever machine you happen to be on at the moment:
```
smbtree
```

---

### Post by jemvyc on 2012-07-01
I am currently on the laptop (Compaq) and it is quick and easy to past the result from smbtree.

The output from smbtree raises new issues so instead of confusing you, phonecomputer is an old HP desktop running xp with printer and a magicjack phone installed.

Newgames is another old HP desktop running xp with my wife's games on it.  It is on a wireless connection thru the same DSL modem where all the others are on ethernet.  Ill get you the output from the Acer shortly.  I have to use a zip drive.


Enter jim's password: 
MYHOME
	\\PHONECOMPUTER  		New HP
		\\PHONECOMPUTER\Microsof       	Microsoft XPS Document Writer
		\\PHONECOMPUTER\C$             	Default share
		\\PHONECOMPUTER\ADMIN$         	Remote Admin
		\\PHONECOMPUTER\Desktop        	
		\\PHONECOMPUTER\User           	
		\\PHONECOMPUTER\Downloads      	
		\\PHONECOMPUTER\HPPhotos       	HP Photosmart C4200 series
		\\PHONECOMPUTER\HPDeskJe       	HP DeskJet 340 (Monochrome)
		\\PHONECOMPUTER\C              	
		\\PHONECOMPUTER\All Users      	
		\\PHONECOMPUTER\print$         	Printer Drivers
		\\PHONECOMPUTER\SharedDocs     	
		\\PHONECOMPUTER\IPC$           	Remote IPC
		\\PHONECOMPUTER\APRS           	
		\\PHONECOMPUTER\HPDeskJe.2     	HP DeskJet 340
		\\PHONECOMPUTER\Administrator  	
		\\PHONECOMPUTER\Documents and Settings	
	\\NEWGAMES       		New Games
		\\NEWGAMES\C$             	Default share
		\\NEWGAMES\ADMIN$         	Remote Admin
		\\NEWGAMES\Favorites      	
		\\NEWGAMES\Desktop        	
		\\NEWGAMES\OS (C)         	
		\\NEWGAMES\Mom            	
		\\NEWGAMES\Program Files  	
		\\NEWGAMES\SharedDocs     	
		\\NEWGAMES\IPC$           	Remote IPC
		\\NEWGAMES\My Documents   	
		\\NEWGAMES\Documents and Settings	
	\\LAPTOP-U-10    		laptop-u-10 server (Samba, Ubuntu)
		\\LAPTOP-U-10\IPC$           	IPC Service (laptop-u-10 server (Samba, Ubuntu))
		\\LAPTOP-U-10\File System    	
		\\LAPTOP-U-10\print$         	Printer Drivers
	\\ACER-X         		ACER-X
cli_start_connection: failed to connect to ACER-X<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME
	\\ACER-U12       		acer-u12 server (Samba, Ubuntu)
		\\ACER-U12\print$         	Printer Drivers
		\\ACER-U12\File System    	
		\\ACER-U12\IPC$           	IPC Service (acer-u12 server (Samba, Ubuntu))
jim@laptop-u-10:~$

---

### Post by Morbius1 on 2012-07-01
The only problem I see is ACER-X. What OS is that one running?

---

### Post by jemvyc on 2012-07-01
smbtree from the acer:

Enter jim's password: 
MYHOME
	\\PHONECOMPUTER  		New HP
	\\NEWGAMES       		New Games
	\\LAPTOP-U-10    		laptop-u-10 server (Samba, Ubuntu)
	\\ACER-U12       		acer-u12 server (Samba, Ubuntu)
		\\ACER-U12\print$         	Printer Drivers
		\\ACER-U12\File System    	
		\\ACER-U12\IPC$           	IPC Service (acer-u12 server (Samba, Ubuntu))
jim@acer-u12:~$ 


******************************************************************
The error message from trying to browse the network:

There is a box about 6 inches by 2 inches 

Bold print says "Could not display "network:///".
                 Error :DBus error org.freedesktop.DBus.Error.NoReply:Did not receive a reply

Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Please select another viewer and try again.

That's all I can find out for now.  Thanks for the continuing support.

---

### Post by jemvyc on 2012-07-01
Acer-X is the Acer when it is running XP.  In the case we are looking at it is running Ubuntu 12 therefore Acer-X is not here.  I have not run XP on it for a couple of hours.

---

### Post by Morbius1 on 2012-07-01
> "Could not display "network:///".On whatever machine you got that error message install the following packages:
```
sudo apt-get install gvfs-backends
``````
sudo apt-get install gvfs-fuse
```And just for good measure make sure you are a member of the fuse group:
```
sudo gpasswd -a your-user-name fuse
```Logout ( not reboot ) and login again for the group membership to take affect and try it again.

---

### Post by jemvyc on 2012-07-01
I got the same error message as before.  It took a lot longer to show the error.  I have copied the exchange where I tried to do what you said.  If I made a mistake, let me know.

This network situation with Ubuntu 12.04 is really tough.  I appreiate your help.

jim@acer-u12:~$ sudo apt-get install gvfs-backends
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gvfs-backends is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 265 not upgraded.
jim@acer-u12:~$ sudo apt-get install gvfs-fuse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gvfs-fuse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 265 not upgraded.
jim@acer-u12:~$ sudo gpasswd -a jim fuse
Adding user jim to group fuse
jim@acer-u12:~$

---

### Post by Morbius1 on 2012-07-01
Open a terminal from acer-u12 and run the following command:
```
nautilus smb://laptop-u-10
```
Does it open nautilus and list the shares of the laptop?

---

### Post by jemvyc on 2012-07-02
I'm back.  Sorry for the delay.  Needed sleep and a trip to the store.

The simple answer is no.

On the terminal it pops up the command prompt.  Then after a long wait it puts up a message panel about 2 inches by 4 inches.  It says Could not display smb://laptop-u-10/

I moved over to the laptop and it ran nautilus and listed 2 items:  File system and Print$

I began wondering what would happen from Acer using Ubuntu 10.  I tried rebooting Acer and tried it.  It works just fine.  I tried to open the File system from laptop-u-10 and got an error file does not exist.  After a minute I realized that is fine, Acer-u12 was not there. Acer was running u-10 

I rebooted acer to u-12 and tried opening the file system from that first nautius on laptop-u-10 and there it was.  I went on and opened /etc/samba/smb.conf with gedit.  It looks just like I left it yesterday when you were helping.

I hope this make sense to you.  Some of it does to me, but why can't I see laptop from acer u 12

---

### Post by jemvyc on 2012-07-04
While continuing to beat my head against the rock, I was searching to see what software was installed on Acer-u12.  I was checking network manager and I found 2 add-ons not installed.  After installing the add-ons, I can see farther into the network from Acer-u12.  Not all the way, but browse network in home folder pops up the windows network icon.  Clicking the windows network icon pops up the myhome icon.  Clicking myhome hangs for a long time and responds that it was unable to mount location Failed to retrieve share list from server.

Not completely solved, but further on.  

Anybody with help would really be appreciated.

Jim

---

### Post by Morbius1 on 2012-07-04
A "Failed to retrieve share list from server" has a limited number of causes:

(1) Hostname length in excess of 15 characters which doesn't seem to be the issue here.

(2) Firewall is in the way - I think you posted somewhere here that you turned them all off so I don't think that's the issue.

(3) Name resolve order is -- um --- out of order.
Add a line to everyone's smb.conf file - right under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```
Then restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```

---

### Post by jemvyc on 2012-07-04
After rebooting, the improvement is gone.

---

### Post by Morbius1 on 2012-07-04
I don't know what that means. You restarted samba, everything worked, then you rebooted and now it's all gone?

Restart smbd and nmbd again.

If you meant something else, install the following package:
```
sudo apt-get install nmap
```Then run the following command:
```
sudo nmap -sP 192.168.0.100/24
```Change 192.168.0.100 to the ip address of whatever machine you are on.

Does it list every network device on your lan?

---

### Post by jemvyc on 2012-07-04
WOW!  I think you fixed it!!!

After restarting smbd, the icons showed back up.  This time clicking myhome showed the network computers.  When I clicked on the laptop, it showed the directories and so I went to /etc/samba.   When I double clicked on smb.conf I got an error message saying the computer (I don't know which one) didn't know how to open that kind of file.  At the bottom of that message was a button to pick it myself and I did pick gedit.  That worked.  Gedit opened the file.

Is there anything else I should check to make sure you did it?

Thanks 

Jim

---

### Post by jemvyc on 2012-07-04
We are talking at the same time.  I am sending this to tell you I will read your last post and then respond.

---

### Post by jemvyc on 2012-07-04
While you were sending message the message to add name resolve order, I was rebooting.  After that reboot browse got me the messages we have seen for days all over again.

I came back after that to see your message to add name resolve order and when I implemented that it seems to work the same way ubuntu 10 has been working before.  I tested it to see if I could see the smb.conf and then went back to tell you the good news.

When I got back to the forum, I saw that I had confused you about the fact that access to the myhome had stopped.

Right now the Acer is seeing all that I expect it to see.  I have not checked printing yet.  When I have checked printing, I will post again.

Thanks again for success.

---

### Post by jemvyc on 2012-07-04
Print driver installation went very easily, even browsed to the printer located on phone computer, and I just printed a file from Acer-u12 to the printer installed on the phone computer.  



Thanks so much.

At the beginning of this discussion you said it was stupid to give world access to all my files. 

When you have time, would you tell me where it did that so I can fix it without breaking all your hard work.


Jim

---

### Post by Morbius1 on 2012-07-04
After all this I'm not sure I'd want to change anything but:

On laptop-u-10 you have this file share:
> [File System]
path = /
read only = No
guest ok = YesYou are allowing everyone write access to your entire file system. Granted, the way Linux is set up even you don't have write access to your entire filesystem unless you become root but the fact that you are allowing guest access at all just looks spooky.

Your share on acer-u12 is also a for the whole filesystem but at least on that one you require credentials to gain access. Your laptop will eventually leave the relative security of being behind a home router and will become exposed to having it's OS viewable by anyone.

And I don't think I used the word "stupid" - "insane" maybe.

---

### Post by jemvyc on 2012-07-06
Well, I tried to remove the "insanity" without damaging anything.  Then I went on and pasted the file into laptop-u-12 and even to Linux Mint 13.  It worked without issues both times.  In case anybody has the same problems I think it would be good to have a look at the smb.conf as I now have it.  So here it is:


smb.conf which is working for jemvyc:

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
	workgroup = myhome

name resolve order = bcast host lmhosts wins

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
	security = user

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
	guest ok = yes
	guest account = jim
	username map = /etc/samba/smbusers

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

;	wins support = no
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


[File System]
	path = /
;	available = yes
;	browseable = yes
	guest ok = yes
	writeable = yes

---

